<template>
	<div id="bg">
		<router-link to="/">返回主页</router-link>
		<div class="login-box">
			<form class="login-form">
				<input type="text" v-model="userDto.mobile" id="mobile" />
				<input type="password" v-model="userDto.password" />
				<div class="code-box">
					<input type="text" v-model="userDto.code" class="code" />
					<img class="verify" @click.prevent="refresh" ref="codeImg" />
				</div>
				<input type="button" class="btn btn-lg dark-fill" value="登录" @click="signIn(userDto)" />
				<div class="asas">
				<i class="iconfont" style="color: #F0F2F7">&#xe603; 下次自动登录</i>               
				<router-link  to ="/sign-up">没有账号？去注册</router-link>
				</div>				
				<div class="line-box">
					<span class="line"></span>
					<span class="login-3rd">第三方登录</span>
					<span class="line"></span>
				</div>
			</form>
			<div class="icon-box" >
				<i class="iconfont" style="color: #00BBDD;">&#xe6ca;</i>
				<i class="iconfont" style="color: rgb(51, 204, 51);">&#xe6ea;</i>
				<i class="iconfont" style="color:#00BBDD;">&#xe68a;</i>
			</div>
		</div>
	</div>
</template>
<script>
export default {
	data() {
		return {
			userDto: {
				mobile: '',
				password: '',
				code: ''
			},
			token: ''
		};
	},
	created() {
		this.axios.get(this.GLOBAL.baseUrl + '/code', { responseType: 'blob' }).then(res => {
			// console.log(res);
			var img = this.$refs.codeImg;
			let url = window.URL.createObjectURL(res.data);
			img.src = url;
			console.log(res.headers);
			//取得后台通过响应头返回的sessionId的值
			this.token = res.headers['access-token'];
			console.log(this.token);
		});
	},
	methods: {
		signIn(userDto) {
			this.axios({
				method: 'post',
				url: this.GLOBAL.baseUrl + '/user/sign-in',
				data: JSON.stringify(this.userDto),
				headers: {
					'Access-Token': this.token //将token放在请求头带到后端
				}
			}).then(res => {
				if (res.data.msg === '成功') {
					alert('登录成功');
					localStorage.setItem('user', JSON.stringify(res.data.data));
					this.$router.push('/');
				} else {
					alert(res.data.msg);
					this.userDto.code = '';
				}
			});
		},
		refresh() {
			this.axios.get(this.GLOBAL.baseUrl + '/code', { responseType: 'blob' }).then(res => {
				console.log(res);
				var img = this.$refs.codeImg;
				let url = window.URL.createObjectURL(res.data);
				img.src = url;
			});
		}
	}
};
</script>
<style scoped>
@font-face {
  font-family: 'iconfont';  /* project id 1434148 */
  src: url('//at.alicdn.com/t/font_1434148_rgva4z2uy1i.eot');
  src: url('//at.alicdn.com/t/font_1434148_rgva4z2uy1i.eot?#iefix') format('embedded-opentype'),
  url('//at.alicdn.com/t/font_1434148_rgva4z2uy1i.woff2') format('woff2'),
  url('//at.alicdn.com/t/font_1434148_rgva4z2uy1i.woff') format('woff'),
  url('//at.alicdn.com/t/font_1434148_rgva4z2uy1i.ttf') format('truetype'),
  url('//at.alicdn.com/t/font_1434148_rgva4z2uy1i.svg#iconfont') format('svg');
}
.iconfont {
	font-family: 'iconfont' !important;
	font-size: 18px;
	font-style: normal;
	
	-webkit-font-smoothing: antialiased;
	-webkit-text-stroke-width: 0.3px;
	-moz-osx-font-smoothing: grayscale;
}

.icon-box {
	cursor: pointer;
	width: 30%;
	margin: 0 auto;
	display: flex;
	justify-content: space-around;
	align-items: center;
}
.line-box {
	width: 100%;
	margin-top: -50px;
	display: inline-flex;
	align-items: center;
}
/*线条样式*/
.line {
	border-bottom: 1px solid #9b9b9b;
	flex: 0 0 33%;
}
/*第三方登录文字样式*/
.login-3rd {
	flex: 0 0 30%;
	font-size: 14px;
	text-align: center;
}
#bg {
	position: absolute;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
	font-size: 20px;
	background-image: url(../assets/img/2.jpg);
}
.asas {
  display: flex;
  justify-content: space-between;
}
.login-box {
	width: 450px;
	height: 340px;
	border: 2px solid rgb(179, 217, 255);
	border-radius: 10px;
	filter: alpha(opacity: 50);
	opacity: 0.5;
	-moz-opacity: 0.5;
	-khtml-opacity: 0.5;
	position: absolute;
	font-size: 15px;
	top: 350px;
	left: 60%;
}
.login-form {
	padding-top: 20px;
	width: 70%;
	margin: 0 auto;
	text-align: left;
}
.login-form input {
	width: 100%;
	height: 40px;
	outline: none;
	border: none;
	margin-bottom: 10px;
	border-radius: 5px;
}
.code-box {
	display: flex;
	margin-top: 10px;
	margin-bottom: 10px;
	justify-content: space-between;
}
.verify {
	flex: 0 0 50%;
	height: 40px;
}
.verify:hover {
	cursor: pointer;
}
.code {
	flex: 0 0 40%;
	height: 40px;
}
a {
	color: rgb(194, 209, 240);
	font-weight: 700;
}
</style>
