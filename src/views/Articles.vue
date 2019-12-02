<template>
	<div class="row">
		<div v-for="(item, index) in articles" :key="index" class="col-12">
			<div class="media-wraaper bg shadow">
				<div class="media-left">
					<img :src="item.author.avatar" class="avatar-lg link" />
					<p>{{ item.author.nickname }}</p>
					<strong>来自</strong>
					<p>{{ item.topic.topicName }}</p>
				</div>
				<div class="media-middle flex flex-left flex-around">
					<router-link :to="{ path: '/article/' + item.article.id }">
						<p>
							<span>{{ item.article.id }}</span>
							{{ item.article.title }}
						</p>
					</router-link>
					<p class="sub-title link">{{ item.article.summary }}</p>
					<p>
						<span class="meta">{{ item.article.comments }}评论</span>
						<i class="iconfont">&#xe635;</i>
						<span class="meta">  {{ item.article.likes }}喜欢</span>
						<i class="iconfont" style="color: rgb(255, 50, 0);">&#xe602;</i>
					</p>
					<span class="time">发表时间：{{ item.article.createTime.date.year }}年{{ item.article.createTime.date.month }}月{{ item.article.createTime.date.day }}日</span>
				</div>
				<div class="media-right"><img :src="item.article.thumbnail" /></div>
			</div>
		</div>

		<div class="col-12"><button class="btn btn-lg warning-fill" @click="loadMore">点击加载更多</button></div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			articles: [],
			currentPage: 1,
			count: 20
		};
	},
	created() {
		this.axios
			.get(this.GLOBAL.baseUrl + '/article', {
				params: {
					page: this.currentPage,
					count: this.count
				}
			})
			.then(res => {
				console.log(res.data.data.length);
				this.articles = res.data.data;
			});
	},
	methods: {
		loadMore() {
			this.currentPage = this.currentPage + 1;
			this.axios
				.get(this.GLOBAL.baseUrl + '/article', {
					params: {
						page: this.currentPage,
						count: this.count
					}
				})
				.then(res => {
					console.log(res.data.data.length);
					let temp = [];
					temp = res.data.data;
					for (var i = 0; i < temp.length; i++) {
						this.articles.splice(this.currentPage * this.count, 0, temp[i]);
					}
					console.log(this.articles.length);
				});
		}
	}
};
</script>

<style scoped="scoped">
.bg {
	background-size: contain;
	background-position-y: 100px;
}
@font-face {
	font-family: 'iconfont'; /* project id 1434148 */
	src: url('//at.alicdn.com/t/font_1434148_os48i7mdre.eot');
	src: url('//at.alicdn.com/t/font_1434148_os48i7mdre.eot?#iefix') format('embedded-opentype'), url('//at.alicdn.com/t/font_1434148_os48i7mdre.woff2') format('woff2'),
		url('//at.alicdn.com/t/font_1434148_os48i7mdre.woff') format('woff'), url('//at.alicdn.com/t/font_1434148_os48i7mdre.ttf') format('truetype'),
		url('//at.alicdn.com/t/font_1434148_os48i7mdre.svg#iconfont') format('svg');
}
.iconfont {
	font-family: 'iconfont' !important;
	font-size: 18px;
	font-style: normal;
	-webkit-font-smoothing: antialiased;
	-webkit-text-stroke-width: 0.4px;
	-moz-osx-font-smoothing: grayscale;
}
.time {
	margin-left: 50px;
}
</style>
