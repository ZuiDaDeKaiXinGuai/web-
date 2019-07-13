### 单进程单线程

Node保持了JavaScript在浏览器中单[进程](https://baike.baidu.com/item/%E8%BF%9B%E7%A8%8B)单[线程](https://baike.baidu.com/item/%E7%BA%BF%E7%A8%8B)的特点。
而且在Node中,JavaSript与其余线程是无法共享任何状态的。

> process

在node应用执行期间一直存在的一个对象，该对象包含了当前进程执行的相关信息，并且可以通过process对其进行控制。

#### process对象是EventEmmitter的实例

##### 相关事件

1. 'beforeExit'  该事件在事件循环清空的时候调用。
2. 'exit' node进程因为以下情况退出的时候，会触发该事件。该事件的回调函数中只能指向同步代码。
    - 显示的调用 process.exit()方法
    - 事件循环被清空，且不再执行任何工作。

3. 'warning' node进程发出的警告总会触发该事件

##### 相关方法

1. `process.exit()`  退出进程

2. `process.abort()` 立即结束进程，并生成一个core文件

3. `process.arch`  返回一个表示cpu架构的字符串

4. `process.argv` 返回一个数组，该数组的第一个元素是node.exe的绝对路径，第二个元素是运行的脚本文件绝对路径，后边的元素是传入的参数。在传入参数的时候，可以传入多个，用空格隔开。

5. `process.argv0` 返回的是node.exe的绝对路径

6. `process.cwd()` 获取当前node进程的工作目录，一般默认是命令行所在的目录。

7. `process.chdir()` 接收一个路径，改变当前进程的工作目录。(一般模块引用相对目录的参照目录是当前模块所在的目录，而操作静态文件的相对目录是工作目录，__diranme永远指的是当前模块所在的目录)

8. `process.env` 返回一个当前系统环境变量的对象

9. `process.execPath` 返回node.exe的绝对路径

10. `process.exitCode` 如果通过exit方法退出进程的时候未指定退出码的话，那么该属性的值将作为退出码

11. `process.memoryUsage()` 该方法返回内存使用情况
    
----
单进程单线程的最大好处是不用像多线程编程那样处处在意状态的同步问题，这里没有死锁的存在，也没有线程上下文交换所带来的性能上的开销。

单线程同样也有自身的弱点

- 无法利用多核 [cpu](https://baike.baidu.com/item/%E4%B8%AD%E5%A4%AE%E5%A4%84%E7%90%86%E5%99%A8/284033?fromtitle=CPU&fromid=120556&fr=aladdin)
- 错误会引起整个应用退出，应用的健壮性值得考验
- 大量计算占用CPU导致无法继续调用异步I/O

![异步I/O图示](https://note.youdao.com/yws/public/resource/3c39708a20e4a060a913ea3fa4c27750/xmlnote/1B1CFD19802D4FC8BCA00D9AAC4906FF/4675)

#### 解决大计算量问题

像浏览器中JavaScript与UI共用一个线程一样，JavaSript长时间执行会导致UI的渲染和响应被中断。在Node中，长时间的CPU占用也会导致后续的异步I/O发不出调用,已完成的异步I/O的回调函数也会得不到及时执行。

HTML5定制了[Web Workers](https://developer.mozilla.org/zh-CN/docs/Web/API/Web_Workers_API/Using_web_workers)的标准，Web Workers能够创建工作线程来进行计算，以解决JavaScript大计算阻塞UI渲染的问题。工作线程为了不阻塞主线程，通过消息传递的方式来传递运行结果，这也使得工作线程不能访问到主线程中的UI。

Node采用了与Web Workers相同的思路来解决单线程中大计算量的问题: ==child process==

> child process

子进程的出现，意味着Node可以从容地应对单线程在健壮性和无法利用多核CPU方面的问题。通过将计算分发到各个子进程，可以将大量计算分解掉，然后再通过进程之间的事件消息来传递结果，这可以很好地保持应用模型的简单和低依赖。通过Master- Worker的管理方式，也可以很好地管理各个工作进程，以达到更高的健壮性。

#### 创建子进程

`child_process`模块给予noede可以随意子进程得能力，以下4个方法：

方法 | 说明
---|---
spawn() | 创建一个子进程来执行特定命令，用法与execFile方法类似，但是没有回调函数，只能通过监听事件，来获取运行结果。它属于异步执行，适用于子进程长时间运行的情况。
exec() | 启动一个子进程来执行命令,于spawn()不同得是其接口不同，它有一个回调函数获知子进程得状况
execFile() | 启动一个子进程来执行可执行文件
fork() | 于spawn()类似，但是它创建得node子进程只需要指定要执行得JavaScript文件模块即可

- `spawn()`与`exec()`、`execFile()`不同得是，后两者创建时可以指定timeout属性设置超时时间，一旦创建得进程运行超过设定时间将会被杀死。
- `exec()`与`execFile()`不同的是，`exec()`适合执行已有得命令，`execFile()`适合执行文件


以上四个方法在创建子进程之后均会返回子进程对象。


#### 进程通信

- 子进程向父进程传递消息

```
//子进程文件
process.send(消息内容)
```

```
//父进程文件
child_porcess.on('data',data=>{
    //data 子进程传递过来的消息
})
```
- 父进程向子进程传递消息

```
//父进程文件
child_porcess.send(消息内容)
```

```
//子进程文件
porcess.on('data',data=>{
    //data 父进程传递过来的消息
})
```


#### 进程通信原理

通过fork()或其他api创建子进程后，为了实现父子进程通信，父子进程之间会创建IPC通道，通过通道，父子进程之间才能通过message和send()传递信息。
IPC即进程间的通信，由libuv提供。

![如图](https://upload-images.jianshu.io/upload_images/15893243-8338d460ab8cccbd.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000/format/webp)

父进程在实际创建子进程之前，会创建IPC通道并监听它，然后才真正创建子进程，并通过环境变量告诉子进程这个IPC通道的文件描述符，子进程在启动时根据文件描述符连接这个已经存在的IPC通道。

#### 进程的稳定

除了message事件外，还有如下事件:

事件 | 作用
---|---
error | 当子进程无法被创建、无法被杀死、无法发送消息时触发
exit | 子进程退出时触发。如果是子进程是正常退出事件的第一个参数为退出码，如果非正常退出则为null. 如果通过kill杀死，则会有第二个参数，为杀死进程时的信号
close | 在子进程的标准输入输出流终止时触发
disconnect | 在父进程或子进程中调用disconect()方法触发，disconnect()方法关闭监听IPC通道

