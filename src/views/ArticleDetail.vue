<template>
	<div class="container border">
		<h2 class="title">{{ articleVo.article.title }}</h2>
		<div class="box1">
			<img :src="articleVo.author.avatar" class="avatar-xs" />
			<span class="meta gutter">{{ articleVo.author.nickname }}</span>
			<span class="meta gutter">
				{{ articleVo.article.createTime.date.year }}年{{ articleVo.article.createTime.date.month }}月{{ articleVo.article.createTime.date.day }}日
				{{ articleVo.article.createTime.time.hour }}:{{ articleVo.article.createTime.time.minute }}:{{ articleVo.article.createTime.time.second }}
			</span>
		</div>
		<p v-html="articleVo.article.content"></p>
		<fieldset>
			<legend>评论</legend>
			<div class="card" v-for="(item, index) in comment" :key="index">
				<div class="avatar-xs"><img :src="item.author.avatar" alt="头像" class="avatar" /></div>
				<p class="sub-title">{{ item.author.nickname }}</p>
				<p class="meta">
					{{ item.comment.createTime.date.year }}年{{ item.comment.createTime.date.month }}月{{ item.comment.createTime.date.day }}日
					{{ item.comment.createTime.time.hour }}:{{ item.comment.createTime.time.minute }}:{{ item.comment.createTime.time.second }}
				</p>
				<p>{{ item.comment.content }}</p>
				<button class="del" @click="del(item.comment.id)">删除</button>
			</div>
			<div class="aaa">
				<input type="text" style="height: 80px; width: 400px;" v-model="writeComment.content" />
				<button class=" btn-round link" @click="release()">发布</button>
			</div>
		</fieldset>
	</div>
</template>

<script>
export default {
	data() {
		return {
			user: JSON.parse(localStorage.getItem('user')),
			articleVo: {},
			comment: {},
			writeComment: {
				articleId: 0,
				userId: 0,
				content: ''
			}
		};
	},
	created() {
		var id = this.$route.params.id;
		this.axios.get(this.GLOBAL.baseUrl + '/article/' + id).then(res => {
			// console.log(res.data.data);
			this.articleVo = res.data.data;
		});
		this.axios.get(this.GLOBAL.baseUrl + '/comment?articleId=' + id).then(res => {
			// console.log(res.data.data);
			this.comment = res.data.data;
		});
	},
	methods: {
		release() {
			this.writeComment.articleId = this.$route.params.id;
			this.writeComment.userId = this.user.id;
			// alert(this.comment.content);
			this.axios.post(this.GLOBAL.baseUrl + '/comment', this.writeComment).then(res => {
				// alert(res.data.msg);
				this.$router.go(0);
			});
		},
		del(id) {
			alert(id);
			this.axios.delete(this.GLOBAL.baseUrl + '/comments/delete/' + id).then(res => {
				this.$router.go(0);
			});
			alert('删除成功');
		}
	},
	computed: {}
};
</script>

<style scoped="scoped">
.aaa {
	flex: 1 1 20%;
	width: 100%;
	margin-top: 280px;
}
.container {
	margin-top: 80px;
}
.avatar {
	width: 40px;
	height: 40px;
}
.title {
	text-align: center;
}
.btn-round {
	background-color: #2c3e50;
	color: #ffffff;
	border-radius: 20%;
	height: 80px;
	width: 60px;
	margin-left: 5px;
}
.box1 {
	margin-bottom: -190px;
	line-height: 10px;
}
.card {
	width: 1000px;
	height: 150px;
	border: 1px solid #e6e6e6;
	/* 圆角边框 */
	border-radius: 5px;
	/* margin是指从自身边框到另一个容器边框之间的距离，就是容器外距离 */
	margin: 30px;
	/* padding是指自身边框到自身内部另一个容器边框之间的距离，就是容器内距离 */
	padding: 20px;
}
.ccc {
	margin-bottom: 200px;
}
.del {
	width: 50px;
	height: 25px;
	font-size: 14px;
	font-family: '微软雅黑';
	color: black;
	float: right;
	margin-top: 10px;
	margin-right: 10px;
}
</style>
