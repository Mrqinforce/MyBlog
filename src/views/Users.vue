<template>
	<div>
		<div class="row">
			<div v-for="(item, index) in users" :key="index" class="col-4">
				<div class="card shadow flex flex-top-y">
					<div class="card-head flex flex-center">
						<router-link :to="{ path: '/user/' + item.id }"><img :src="item.avatar" /></router-link>
					</div>

					<div class="card-body flex flex-left">
						<div>
							<p class="title">{{ item.nickname }}</p>							
							<a :href="item.homepage" class="link" @click="go(item.homepage)">个人主页</a>							
							<p class="sub-title">{{ item.introduction }}</p>
						</div>
						<p class="meta">
							<strong>来自：{{ item.address }}</strong>
						</p>
						<p class="meta">{{ item.articles }}篇文章，{{ item.fans }}个粉丝</p>
						<button class="btn btn-lg btn-rd dark-fill link" @click="follow(item.id)" v-show="show">关注</button>
					</div>
				</div>
			</div>
		</div>
		<div class="row"><button class="btn btn-lg btn-rd dark-fill" @click="loadMore">点击加载更多</button></div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			user: JSON.parse(localStorage.getItem('user')),
			users: [],
			currentPage: 1,
			count: 6,
			userFollow: {
				fromId: 0,
				toId:0
						},
				show: true,
				color: []	
		};
	},
	created() {
		this.axios
			.get(this.GLOBAL.baseUrl + '/user', {
				params: {
					page: this.currentPage,
					count: this.count
				}
			})
			.then(res => {
				console.log(res.data.data.length);
				this.users = res.data.data;
			});
	},
	methods: {
		loadMore() {
			this.currentPage = this.currentPage + 1;
			this.axios
				.get(this.GLOBAL.baseUrl + '/user', {
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
						this.users.splice(this.currentPage * this.count, 0, temp[i]);
					}
					console.log(this.users.length);
				});
		},
		go(page) {
			window.location.href = page;
		},
		follow(id) {
					this.userFollow.fromId = this.user.id;
					this.userFollow.toId = id;
					this.axios.get(this.GLOBAL.baseUrl + '/follow', {
						params: {
							fromId: this.userFollow.fromId,
							toId: this.userFollow.toId
						}
					}).then(res => {
						if(res.data.msg==='关注成功') {
							alert("不能重复关注");
							this.unFollow(id);
							
						} else {
							
							this.axios.post(this.GLOBAL.baseUrl + '/follow', this.userFollow).then(res => {
								alert(res.data.msg);
							})
						}
					})
				},
				changeColor(index) {
					if(this.color[index]) {
						this.color.splice(index, 1, false);
						
					} else {
						this.color.splice(index, 1, true);
					}
				},
				unFollow(id) {
					this.userFollow.fromId = this.user.id;
					this.userFollow.toId = id;
					this.axios.delete(this.GLOBAL.baseUrl + '/follow', {
						params: {
							fromId: this.userFollow.fromId,
							toId: this.userFollow.toId
						}
					}).then(res => {
						alert(res.data.msg);
					})
				}
		
	}
};
</script>
<style scoped>
.card {
	width: 90%;
	height: 470px;
	background-color: #2C3E50;
	border-radius: 5%;
	font-weight: 700;
}
.card img {
	border-radius: 60%;
	width: 100%;
	height: 72%;
	/* border-top-left-radius: 5px;
	border-bottom-right-radius: 5px; */
}
</style>
