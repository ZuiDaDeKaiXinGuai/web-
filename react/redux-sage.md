sages 采用 `Generator` 函数来 yield Effects（包含指令的文本对象）。Generator 函数的作用是可以暂停执行，再次执行的时候从上次暂停的地方继续执行。Effect 是一个简单的对象，该对象包含了一些给 middleware 解释执行的信息。你可以通过使用 effects API 如 fork，call，take，put，cancel 等来创建 Effect。




