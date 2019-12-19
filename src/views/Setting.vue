<template>
<div class="row">
		<div class=" col-12 flex">
				<ul class="box link">
				<li class="box border-bottom" v-on:click="change()">修改个人资料</li>	
				</ul>	
				<div class="alter border" v-if="show">
					  	<div class="con-head">
					    <input type="text" placeholder="用户ID:" v-model="user.id">
				  		<input type="text" placeholder="昵称:" v-model="alteruser.nickname">
				  		<input type="text" placeholder="性别:" v-model="alteruser.gender">
				  		<input type="text" placeholder="地址:" v-model="alteruser.address">
				  		<input type="text" placeholder="简介:" v-model="alteruser.introduction">
						<input type="date" placeholder="生日:" v-model="alteruser.birthday">
						<input type="text" placeholder="邮箱:" v-model="alteruser.email">
						<div class="con-body">	
				  		<button v-on:click="alter()">确定</button>
						</div>
						  	</div>
				  	</div>
				</div>
				</div>
</template>

<script>
	export default {
		data() {
			return {
				flag:0,
				user: JSON.parse(localStorage.getItem('user')),
				userVo: {
					user: {},
					articleList: {}
				},
				alteruser:{
							 nickname: '',
				    		 gender : '',
							 address : '',
							 introduction: '',
							 birthday: '',
							 id: ''
								},
								show:false,
			};
		},
		mounted(){
	
		},
		created() {
			this.axios.get(this.GLOBAL.baseUrl + '/user/' + id).then(res => {
				console.log(res.data.data);
				this.userVo = res.data.data;
			});
	
		},
		methods: {
			alter(){
						this.alteruser.id = this.user.id;
						alert(this.user.id)
						this.axios.post(this.GLOBAL.baseUrl + '/user/alter', this.alteruser)
							.then(res => {
								this.$router.go(0);
							});
							alert("成功")
					},
					change() {
						this.show =! this.show;
					},
		}
	};
</script>

<style>
	.alter{
			padding: 180px;
			height: 700px;
		}
	.con-head{
		display: flex;
		flex-direction: column;
		margin-bottom: 20px;
	}
	 .con-head input{
		width: 500px;
		height: 40px;
		margin-top: 20px;
	}
	.con-body{
		width: 500px;
		height: 40px;
		margin-top: 20px;
	}
	/* .nav-item {
		height: 70px;
		/* line-height: 70px;
	} */
	.box {
		width: 100px;
		height: 800px;
	}
</style>