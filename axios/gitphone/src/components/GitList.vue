<template>
  <div id="GitList">
        <span class="card" v-for="user of info.users" :key="user.login">
            <a :href="user.html_url" target="_blank">
                <img :src="user.avatar_url" style='width: 100px'/>
            </a>
            <p>{{user.login}}</p>
        </span>
        <!-- 展示欢迎词 -->
        <h1 v-show="info.isFirst">您好，欢迎！</h1>
        <!-- 显示正在加载 -->
        <h1 v-show="info.isLoading">loading...</h1>
        <!-- 显示请求失败信息 -->
        <h1>{{info.errorMsg}}</h1>
  </div>
</template>

<script>
export default {
    name:'GitList',
    props:['info']
}
</script>

<style scoped>
    .album {
		min-height: 50rem; /* Can be removed; just added for demo purposes */
		padding-top: 3rem;
		padding-bottom: 3rem;
		background-color: #f7f7f7;
	}

	.card {
		float: left;
		width: 33.333%;
		padding: .75rem;
		margin-bottom: 2rem;
		border: 1px solid #efefef;
		text-align: center;
	}

	.card > img {
		margin-bottom: .75rem;
		border-radius: 100px;
	}

	.card-text {
		font-size: 85%;
	}
</style>