<template>
<div class="row">
		<div class=" col-12 flex">
				<ul class="box link">
				<li class="box border-bottom" v-on:click="changeshow(0)">修改个人资料</li>	
				<li class="box border-bottom " v-on:click="changeshow(1)">写文章</li>		
				</ul>	
				<div class="alter border" v-if="flag===0">
					  	<div class="con-head">
					    <input type="text" placeholder="用户ID:" v-model="user.id">
				  		<input type="text" placeholder="昵称:" v-model="alteruser.nickname">
				  		<div class="xb">	
				  		<p>性别:</p>					
				  		<div><input  type="radio"  value="男" checked="checked"  v-model="alteruser.gender"/><p>男</p></div>					
				  		<div><input  type="radio" value="女" v-model="alteruser.gender"/><p>女</p></div>							
				  		</div> 
				  		<input type="text" placeholder="地址:" v-model="alteruser.address">
				  		<input type="text" placeholder="简介:" v-model="alteruser.introduction">
						<input type="date" placeholder="生日:" v-model="alteruser.birthday">
						<input type="text" placeholder="邮箱:" v-model="alteruser.email">
						<div class="con-body">	
				  		<button v-on:click="alter()">确定</button>
						</div>
						  	</div>
				  	</div>
					<div class="writearticle border" v-if="flag===1">
							<div class="con">
								<div class="con-head">
									<input type="text" placeholder="标题:" v-model="writeArticle.title">
									<input type="text" placeholder="简介:" v-model="writeArticle.summary">
									<input type="text" placeholder="专题ID:" v-model="writeArticle.topicId">
									<input type="text" placeholder="图片地址:" v-model="writeArticle.thumbnail">
								</div>
								<div class="con-body">				
									<textarea rows="10" cols="30" placeholder="内容:" v-model="writeArticle.content"></textarea>
									<button @click="changeshow(1)" v-on:click="release">发布</button>
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
								writeArticle: {
												topicId:'',
												userId: '',
												title:'',
												summary: '',
												thumbnail:'',
												comments:0,
												content:'',
												likes:0
												
											},
								// show:false,
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
					changeshow(id){
								this.flag=id;
							},
					release() {
								if(this.writeArticle.text==''||this.writeArticle.text==''||this.writeArticle.content==''||this.writeArticle.topicId==''){
									alert("内容不能为空")
									return;
								}			
								this.writeArticle.userId= this.user.id;
								this.axios.post(this.GLOBAL.baseUrl + '/article', this.writeArticle)
								.then(res => {
									this.$router.go(0);
								});
								alert("发布成功")
							},
		}
	};
</script>

<style>
	.alter{
			padding: 180px;
			height: 900px;
		}
		.writearticle {
			padding: 180px;
				height: 900px;
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
		width: 150px;
		height: 50px;
		margin-top: -160px;
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
			width: 200px;
			height: 40px;
			margin-top: 20px;
		}
		.con-body textarea{
			width: 500px;
			height: 100px;
			margin-top: 30px;
			margin-bottom: 30px;
		}
		.con-body button{			
			width: 100px;
			height: 40px;
			background-color: rgb(242, 242, 242);
		}
	.banner {
		width: 100%;
		height: 200px;
		margin-top: 50px;
		padding-bottom: 40px;
	}
</style>