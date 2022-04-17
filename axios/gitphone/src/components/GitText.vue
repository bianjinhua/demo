<template>
  <section class="jumbotron">
      <h3 class="jumbotron-heading">search git users</h3>
        <div id="GitText">
            <input type="text" v-model="newTitle">
            <button @click="sendTitle">确认</button>
        </div>
  </section>
</template>

<script>
export default {
    name:'GitText',
    props:['addTitle','gitUsers'],
    data() {
        return {
            newTitle:'',
        }
    },
    methods: {
        //给父组件传递搜索关键词且向服务器提出请求
        sendTitle(){
            this.addTitle(this.newTitle)
            this.gitUsers()
            this.newTitle=''
        }
    },
}
</script>

<style>

</style>