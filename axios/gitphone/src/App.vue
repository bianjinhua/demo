<template>
  <div id="app">
    <git-text :addTitle="addTitle" :gitUsers="gitUsers"/>
    <git-list :info="info"/>
  </div>
</template>

<script>
import GitText from './components/GitText.vue'
//引入axios
import axios from 'axios'
import GitList from './components/GitList.vue'


export default {
  components: { GitText, GitList },
  name: 'App',
  data() {
    return {
      title:'',
      info:{
        users:[],
        errorMsg:'',
        isFirst:true,
        isLoading:false,
      }
    }
  },
  methods: {
    //从子组件获取搜索关键词
    addTitle(val){
      this.title=val
    },
    //请求数据
    gitUsers(){
      //请求前更新info数据，显示加载页面
      this.info={users:[],errorMsg:'',isFirst:false,isLoading:true}
      axios.get(`https://api.github.com/search/users?q=${this.title}`).then(
        response=>{
          console.log('请求成功');
          this.info={users:response.data.items,errorMsg:'',isFirst:false,isLoading:false}
          this.users=response.data.items
        },
        error=>{
          console.log('请求失败');
          this.info={users:[],errorMsg:error.message,isFirst:false,isLoading:false}
        }
      )
    }
  },
}
</script>

<style>
#app {
  padding: 0;
  margin: 0;
}
</style>
