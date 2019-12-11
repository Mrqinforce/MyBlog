<template>
	<div class="container border">
		<h2 class="title">{{ articleVo.article.title }}</h2>
		<div class="box">
			<img :src="articleVo.author.avatar" class="avatar-xs" />
			<span class="meta gutter">{{ articleVo.author.nickname }}</span>
			<span class="meta gutter">
				{{ articleVo.article.createTime.date.year }}年{{ articleVo.article.createTime.date.month }}月{{ articleVo.article.createTime.date.day }}日
				{{ articleVo.article.createTime.time.hour }}:{{ articleVo.article.createTime.time.minute }}:{{ articleVo.article.createTime.time.second }}
			</span>
		</div>
		<div v-html="articleVo.article.content"></div>
		<fieldset>
			<legend>评论</legend>
			<div class="card" v-for="(item, index) in comment" :key="index">
				<div class="avatar-xs"><img :src="item.author.avatar" alt="头像" class="avatar" />
				</div>
				<p class="sub-title">{{ item.author.nickname }}</p>
				<p class="meta">
					{{ item.comment.createTime.date.year }}年{{ item.comment.createTime.date.month }}月{{ item.comment.createTime.date.day }}日
					{{ item.comment.createTime.time.hour }}:{{ item.comment.createTime.time.minute }}:{{ item.comment.createTime.time.second }}
				</p>
				<p>{{ item.comment.content }}</p>
			</div>
			<div class="aaa">
				<input type="text" style="height: 80px; width: 400px;" v-model="writeComment.content" />
				<button class=" btn-round" @click="release">发布</button>
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
		}
	},
	computed: {}
};
</script>

<style scoped="scoped">
.aaa {
	width: 100px;
	height: 140px;
}
.container {
	margin-top: 80px;
}
.avatar {
	width: 40px;
	height: 40px;
}
.btn-round {
	background-color: #2c3e50;
	color: #ffffff;
	border-radius: 50%;
	height: 50px;
	width: 40px;
}
.box {
	height: 50px;
	line-height: 10px;
}
</style>
