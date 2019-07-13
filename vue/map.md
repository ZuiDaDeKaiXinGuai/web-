#### map

import {mapState,mapGetters,mapMutations,mapActions} from 'vuex';


概念 | 不用map | 用map
---|---|---
State | 在组件的计算属性中的使用。computed{getCount() {return this.$store.state.count;}} | ...mapState(['count','arr']),
Getters | getPeople(){return this.$store.state.arr.filter(item => item.people > 30);} | ...mapGetters(['getPeople','getnews'])
mutations | addList(){this.$store.commit('addList',{grade:'1611A',people:39});} | ...mapMutations(['addList'])
Actions | add(){this.$store.dispatch('add');} | ...mapActions(['add'])

