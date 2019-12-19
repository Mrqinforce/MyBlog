<template>
	<div>
		<div class="nav primary-fill shadow">
			<div class="nav-bar">
				<ul class="nav-list flex-around">
					<li class="nav-item link">
						<router-link to="/setting">
						<i class="iconfont">&#xe611;</i>
						</router-link>
						</li>
					<li class="nav-item"><router-link to="/index">主页</router-link></li>
					<li class="nav-item"><input type="text" class="input-box" placeholder="搜索:请输入你想要的内容" v-model="keywords" /></li>
					<li class="nav-item"><i class="iconfont" @click="search">&#xe601;</i></li>
					<li class="nav-item"><router-link to="/topics">专题</router-link></li>
					<li class="nav-item"><router-link to="/articles">文章</router-link></li>
					<li class="nav-item"><router-link to="/users">作者</router-link></li>
					<li class="nav-item" v-if="!this.user"><router-link to="/sign-in">登录</router-link></li>
					<router-link :to="{ path: '/user/' + user.id }" v-if="this.user">
						<img :src="user.avatar" @mouseenter="this.show = true" class="avatar-xs abs-center-right" />
					</router-link>
					<li class="nav-item" v-if="this.user"><a class="link" @click="logout">退出</a></li>
				</ul>
			</div>
		</div>
		
		<router-view class="container" />
	</div>
</template>
<script>
export default {
	data() {
		return {
			user: JSON.parse(localStorage.getItem('user')),
			keywords: ''
		};
	},
	created() {},
	methods: {
		logout() {
			this.user = null;
			localStorage.clear();
		},
		search() {
			let currentPath = this.$route.path;
			alert(currentPath);
			if (currentPath != '/search' || currentPath != '/search/article' || currentPath != '/search/topic' || currentPath != '/search/usere') {
				this.$router.push({ path: '/search', query: { keywords: this.keywords } });
			} else {
				this.$router.push({ path: '/empty', query: { keywords: this.keywords } });
			}
		}
	}
};
</script>
<style scoped>
/* 路由激活高亮样式 */
.router-link-active {
	background-color: rgba(0, 0, 0, 0.35);
	font-weight: 700;
}
.container {
	margin-top: 80px;
}
@font-face {
  font-family: 'iconfont';  /* project id 1434148 */
  src: url('//at.alicdn.com/t/font_1434148_qkwlcfrgblp.eot');
  src: url('//at.alicdn.com/t/font_1434148_qkwlcfrgblp.eot?#iefix') format('embedded-opentype'),
  url('//at.alicdn.com/t/font_1434148_qkwlcfrgblp.woff2') format('woff2'),
  url('//at.alicdn.com/t/font_1434148_qkwlcfrgblp.woff') format('woff'),
  url('//at.alicdn.com/t/font_1434148_qkwlcfrgblp.ttf') format('truetype'),
  url('//at.alicdn.com/t/font_1434148_qkwlcfrgblp.svg#iconfont') format('svg');
}
.iconfont {
	font-family: 'iconfont' !important;
	font-size: 25px;
	font-style: normal;
	-webkit-font-smoothing: antialiased;
	-webkit-text-stroke-width: 0.4px;
	-moz-osx-font-smoothing: grayscale;
}

</style>
