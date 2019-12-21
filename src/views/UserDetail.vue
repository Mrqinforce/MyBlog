<template>
	<div class="container">
		<div class="main-top  col-12 ">
			<div class="row flex flex-left">
			<div class="col-8 ">
			<img :src="userVo.user.avatar" class="avatar-xs" @click="handleClick()" v-if="userVo.user.id === this.user.id"/>
			<img :src="avatar" class="zh-avatars" v-else />
		    <input type="file" @change="changeAvatar($event)" style="display: none;" id="fileBox" />
			<p>{{ userVo.user.nickname }}</p>
		</div>
		
			</div>
		<ul class="btn link">
			<button class="nav-item  btn-lg btn-circle " v-on:click="change()">
				<i class="iconfont">&#xe605;</i>写文章
				</button>
					
	  </ul>	
	  <div class="   ">
	  	<p>电子邮箱：{{userVo.user.email}}</p>
	  	<p>性别：{{userVo.user.gender}}</p>
	  	<p>简介：{{userVo.user.introduction}}</p>
	  	<p>家庭住址：{{ userVo.user.address }}</p>
	  	<p>出生日期：{{ userVo.user.birthday.year }}年{{ userVo.user.birthday.month }}月{{ userVo.user.birthday.day }}日</p>
		<p>
		注册时间:{{ userVo.user.createTime.date.year }}年{{ userVo.user.createTime.date.month }}月{{ userVo.user.createTime.date.day }}日
											</p>
	  	</div>
	  </div>
	  
	  <div class="writearticle border" v-if="show">
	  		<div class="con">
	  			<div class="con-head">
	  				<input type="text" placeholder="标题:" v-model="writeArticle.title">
	  				<input type="text" placeholder="简介:" v-model="writeArticle.summary">
	  				<input type="text" placeholder="专题ID:" v-model="writeArticle.topicId">
	  				<input type="text" placeholder="图片地址:" v-model="writeArticle.thumbnail">
	  			</div>
	  			<div class="con-body">				
	  				<textarea rows="10" cols="30" placeholder="内容:" v-model="writeArticle.content"></textarea>
	  				<button @click="change()" v-on:click="release">发布</button>
	  			</div>
	  		</div>       						
	  	</div>
	  	
		<ul class="list user-dynamic col-4">
			<li class="badge-icon">
				<a target="_blank" href="https://www.jianshu.com/mobile/campaign/stories2018">
					<img width="20" heigth="20" src="//upload.jianshu.io/user_badge/75b4d254-b610-4455-8192-07adc0f82dee" alt="75b4d254 b610 4455 8192 07adc0f82dee" />
					简书2018年的10个好故事作者
				</a>
			</li>
			<li class="badge-icon">
				<a target="_blank" href="http://www.jianshu.com/p/ed7ca899d796">
					<img width="20" heigth="20" src="//upload.jianshu.io/user_badge/b8f6544c-367e-4c1a-81f6-4a4875c556d8" alt="B8f6544c 367e 4c1a 81f6 4a4875c556d8" />
					简书版权
				</a>
			</li>
			<li class="badge-icon">
				<a target="_blank" href="http://www.jianshu.com/p/d1d89ed69098">
					<img width="20" heigth="20" src="//upload.jianshu.io/user_badge/20679c3c-3334-417c-8b46-901bbd891345" alt="20679c3c 3334 417c 8b46 901bbd891345" />
					旅行达人
				</a>
			</li>
		</ul>
		<div class="row">
			<div class="col-8">
				<div class="col-12" v-for="(item, index) in userVo.articleList" :key="index">
					<div class="media-wraaper bg shadow">
						<div class="media-left"><img :src="getImages(item.article.thumbnail)" class="avatar-lg link" />
						</div>
						<div class="media-middle flex flex-left flex-around">
							<p class="title link" @click="toDetail(item.article.id)">{{ item.article.title }}</p>
							<p class="sub-title ">{{ item.article.summary }}</p>
						</div>
						<i class="iconfont" style="color:grey; font-size: 25px;float: right;" @click="dels(item.article.id, item.article.useId)">&#xe61c;</i>
					</div>
				</div>
			</div>
			<div class="col-4 border">
				<div class="col-12">
					<!---->
					<ul class="list user-dynamic">
						<li class="badge-icon">
							<a target="_blank" href="http://www.jianshu.com/p/d1d89ed69098">
								<img width="20" heigth="20" src="//upload.jianshu.io/user_badge/5b7a3117-2773-45ac-9d61-03af8463898e" alt="5b7a3117 2773 45ac 9d61 03af8463898e" />
								观察优秀作者
							</a>
							<audio controls="controls">
								<source src="../../music.mp3" type="audio/ogg" autoplay="autoplay" />
							</audio>
							<hr />
						</li>
					</ul>
					<div class="title">个人介绍</div>
					<hr />
					<div class="description">
						<div class="js-intro">
							欢迎关注我的个人公众号：lulu_blog
							<br />
							坦然生活，默然体验，欣然恋念，偶然发言
						</div>
						<hr />
						<a
							class="social-icon-sprite social-icon-weixin"
							data-toggle="popover"
							data-placement="bottom"
							data-html="true"
							data-trigger="hover"
							href="javascript:void(0);"
							data-content="
				  <div class=&quot;qrcode&quot;>
				    <div class=&quot;arrow-top&quot;></div>
				    <img src=&quot;//upload.jianshu.io/users/qrcodes/301940/qrcode_for_gh_0d53a1e1bd0e_344.jpg?imageMogr2/auto-orient/strip|imageView2/1/w/320/h/320&quot; alt=&quot;320&quot; />
				  </div>
				"
							data-original-title=""
							title=""
						></a>
					</div>
					<div id="user-publications"><!----></div>
					<div id="user-courses"><!----></div>
					<ul class="list user-dynamic">
						<li>
							<a href="/users/ef4f2422125f/subscriptions">
								<i class="iconfont ic-collection"></i>
								<span>他关注的专题/文集/连载</span>
							</a>
						</li>
						<li>
							<a href="/users/ef4f2422125f/liked_notes">
								<i class="iconfont ic-like"></i>
								<span>他喜欢的文章</span>
							</a>
						</li>
					</ul>
					<!-- 专题和文集 -->
					<div>
						<div>
							<div class="title">他创建的专题</div>
							<hr />
							<!---->
							<ul class="list">
								<li><a href="/c/4b1a5445dde5" target="_blank" class="name">父母的备忘录</a></li>
								<li>
									<!---->
									<!---->
								</li>
							</ul>
							<!---->
						</div>
						<!---->
						<div>
							<div class="title">他的文集</div>
							<hr />
							<ul class="list">
								<li>
									<a href="/nb/621165" target="_blank"><i class="iconfont ic-search-notebook"></i></a>
									<a href="/nb/621165" target="_blank" class="name">
										日记本
										<!---->
									</a>
								</li>
								<li>
									<a href="/nb/621166" target="_blank"><i class="iconfont ic-search-notebook"></i></a>
									<a href="/nb/621166" target="_blank" class="name">
										卢璐的随笔
										<!---->
									</a>
								</li>
								<li>
									<a href="/nb/30608924" target="_blank"><i class="iconfont ic-search-notebook"></i></a>
									<a href="/nb/30608924" target="_blank" class="name">
										新媒体管家发布
										<!---->
									</a>
								</li>
								<li>
									<a href="/nb/1172116" target="_blank"><i class="iconfont ic-search-notebook"></i></a>
									<a href="/nb/1172116" target="_blank" class="name">
										原味法餐
										<span class="tag">连载</span>
									</a>
								</li>
								<li>
									<!---->
									<!---->
								</li>
							</ul>
						</div>
					</div>
					<div class="user-action">
						<a class="js-block-button" data-user-id="301940" href="javascript:void(null);">加入黑名单</a>
						·
						<a class="js-report-button" data-reportable-id="301940" data-reportable-type="user">举报用户</a>
					</div>
					<!---->
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
						show:false,
			alteruser:{
						 nickname: '',
			    		 gender : '',
						 address : '',
						 introduction: '',
						 homepage: '',
						 id: ''
							}
		};
	},
	created() {
		var query = window.location.href;
		//锁定到最后一个"/"的位置
		var begin = query.lastIndexOf('/') + 1;
	    //取出地址中最后的id值
		var usersId = query.substring(begin);
		var id = this.$route.params.id;
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
						dels(id, id1) {
									if (id1 !== this.user.id) {
										alert('不能删');
										return;
									}
									alert(id);
									this.axios.delete(this.GLOBAL.baseUrl + '/article/delete?id=' + id + '&userId=' + this.user.id).then(res => {
										this.user.articles--;
										// this.$router.go(0);
									});
									alert('删除文章成功');
								},
								
		changeshow(id){			
					this.flag=id;
				},
				change() {
					this.show =! this.show;
				},
				getImages(_url) {
							if (_url) {
								let _u = _url.substring(8);
								return 'https://images.weserv.nl/?url=' + _u;
							}
						},
						toDetail(id) {
									this.$router.push('/article/' + id);
								},
								//点击头像，即模拟点击文件选择组件
										handleClick: function() {
											document.getElementById('fileBox').click();
										},
										changeAvatar: function() {
											var _this = this;
											let formData = new FormData();
											alert(event.target.files[0].name);
											formData.append('file', event.target.files[0]);
											this.$http({
												method: 'post',
												url: this.GLOBAL.baseUrl + '/upload',
												headers: {
													'Content-Type': 'multipart/form-data'
												},
												data: formData,	
												processData: false,
												contentType: false
											}).then(uploadFileRes=> {
												console.log(uploadFileRes.data.data)
												_this.avatar = uploadFileRes.data.data;
												this.updateAvatar(_this.avatar);
											});
											//调用修改头像的方法
											
										},
										updateAvatar: function(avatar) {
											var _this = this
											console.log(avatar)
											this.$http({
												method: 'post',
												url: this.GLOBAL.baseUrl + '/user/update',
												headers: {
													'Content-Type': 'application/x-www-form-urlencoded'
												},
												params: {
													mobile: this.user.mobile,
													avatar: avatar
												}
											}).then(res => {
												  console.log(res.data.code);
											});
										}
	}
};

</script>

<style scoped="scoped">
@font-face {
  font-family: 'iconfont';  /* project id 1434148 */
  src: url('//at.alicdn.com/t/font_1434148_ad9vjrnxzc7.eot');
  src: url('//at.alicdn.com/t/font_1434148_ad9vjrnxzc7.eot?#iefix') format('embedded-opentype'),
  url('//at.alicdn.com/t/font_1434148_ad9vjrnxzc7.woff2') format('woff2'),
  url('//at.alicdn.com/t/font_1434148_ad9vjrnxzc7.woff') format('woff'),
  url('//at.alicdn.com/t/font_1434148_ad9vjrnxzc7.ttf') format('truetype'),
  url('//at.alicdn.com/t/font_1434148_ad9vjrnxzc7.svg#iconfont') format('svg');
}
.iconfont {
	font-family: 'iconfont' !important;
	font-size: 18px;
	font-style: normal;
	-webkit-font-smoothing: antialiased;
	-webkit-text-stroke-width: 0.4px;
	-moz-osx-font-smoothing: grayscale;
}
	.writearticle{
			padding: 20px;
			height: 800px;
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
	.con-body textarea{
		width: 800px;
		height: 100px;
		margin-top: 30px;
		margin-bottom: 30px;
	}
	.con-body button{			
		width: 100px;
		height: 40px;
		background-color: rgb(242, 242, 242);
	}
.avatar-lg {
	width: 170px;
	height: 210px;
	border-radius: 5%;
}
.banner {
	width: 100%;
	height: 200px;
	margin-top: 50px;
	padding-bottom: 40px;
}
.cover {
	width: 90%;
	height: 100%;
	margin-left: 38px;
}
.love {
	display: flex;
	flex-flow: column;
	margin-top: 20px;
}
.ku {
	margin-top: 50px;
	margin-right: 10px;
}
.lab {
	height: 50px;
	width: 100%;
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: center;
	margin-top: 5px;
	background-color: wheat;
}
.btn-circle {
	width: 85px;
	height: 80px;
	border-radius: 45%;
}
.lab p {
	font-size: 30px;
	font-weight: 600;
	color: white;
}
.first {
	display: flex;
	flex-direction: column;
	align-items: center;
}
.first img {
	border: 2px solid #fff;
}
.ku p {
	margin-bottom: 10px;
}
.row {
	display: flex;
	margin-top: -50px;
	flex-wrap: wrap;
}
.zh-navs {
	height: 70px;
	position: fixed;
	top: 0;
	left: 0;
	right: 0;
	z-index: 999;
	background-color: rgba(172, 91, 155);
	cursor: pointer;
}
.changeBox {
	display: flex;
} 
.tui {
	cursor: pointer;
	margin-left: 30px;
	padding-top: 7px;
}
.zh-containers {
	width: 80%;
	margin: auto;
	margin-top: 100px;
}
.nav-item {
	height: 70px;
	line-height: 70px;
	background-color: rgb(242, 242, 242);
} 
/* 下边框 */
	.border-bottom {
	border-bottom: 1px solid #ddd;
	padding-bottom: 20px;
}
.zh-avatars {
	width: 100px;
	height: 100px;
	border-radius: 50%;
	cursor: pointer;
}
.thumnail-xs {
	width: 150px;
	height: 150px;
	border-radius: 10px;
}
	.preview-box {
		width: 100px;
		height: 100px;
		border: 1px dashed #aaa;
		position: relative;
		top: -10px;
		left: 0px;
	
	}
	
	.preview-box img {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
	
	}
	
	.select-file {
		position: absolute;
		top: 0;
		left: 0;
		height: 100%;
		width: 100%;
		opacity: 0;
		z-index: 9999;
		cursor: pointer;
	}
	
	.carousel-wrap {
		position: relative;
		width: 72%;
		height: 380px;
		overflow: hidden;
		left: 200px;
	
	}
	
	.slide-ul {
		width: 100%;
		height: 100%;
	}
	
	.slide-ul li {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
	}
	
	.slide-ul li img {
		width: 100%;
		height: 100%;
	}
	
	.carousel-items {
		z-index: 100;
		position: relative;
		top: -80px;
		text-align: center;
		font-size: 0;
	}
	
	.carousel-items span {
		display: inline-block;
		width: 50px;
		height: 6px;
		margin: 0 5px;
		background-color: #eee;
		cursor: pointer;
	}
	
	.carousel-items .active {
		background-color: #FFA500;
	}
	
	动画
	.slide-enter-to {
		transition: all 1s ease;
		transform: translateX(0);
	}
	
	.slide-leave-active {
		transition: all 1s ease;
		transform: translateX(-100%)
	}
	
	.slide-enter {
		transform: translateX(100%)
	}
	
	.slide-leave {
		transform: translateX(0)
	}
	
	.card-wrap {
		display: flex;
		width: 28%;
		flex-wrap: wrap;
	}
	
	.card {
		flex: 0 0 28%;
	}
.main-top .info {
	margin-top: 5px;
	padding-left: 100px;
	font-size: 14px;
}
.main-top .user-follow-button {
	padding: 8px 0;
	width: 100px;
}
.main-top .btn-hollow {
	padding: 8px 0;
	width: 90px;
}
.main-top {
	margin-bottom: 20px;
	margin-top: -30px;
}
*,
:after,
:before {
	box-sizing: border-box;
}
audio {
	background-color: rgb(245, 245, 240);
}

.main-top .btn,
.main-top .user-follow-button {
	float: right;
	margin: 23px 0 23px 16px;
	font-size: 15px;
}
.cover {
	width: 100%;
	height: 100%;
	border-radius: 10px;
}
.infoo {
	position: relative;
	top: 10px;
	left: -500px;
	color: #fff;
	margin-bottom: -50px;
	padding: 10px;
	width: 130px;
	height: 130px;
	margin: 0 auto;
	text-align: center;
	border-radius: 20px;
}
.main-top .info {
	margin-top: 5px;
	padding-left: 100px;
	font-size: 14px;
}
.main-top {
	margin-bottom: 20px;
}
.main-top .title {
	padding: 5px 0 0 100px;
}
.main-top .title .name {
	display: inline;
	font-size: 21px;
	font-weight: 700;
	vertical-align: middle;
}
.main-top .ic-man,
.main-top .ic-woman {
	font-size: 17px;
	vertical-align: middle;
}
.main-top .info ul {
	font-size: 0;
}
ul {
	padding-left: 0;
}
.main-top .info ul .meta-block {
	font-size: 12px;
	margin: 0 7px 6px 0;
	padding: 0 7px 0 0;
	border-right: 1px solid #f0f0f0;
}
.main-top .info ul a,
.main-top .info ul div {
	color: #969696;
}

.row {
	margin-top: 100px;
}
.box {
	width: 90%;
	margin: 0 auto;
	padding: 10px;
	min-height: 100px;
}
.box > p {
	line-height: 20px;
}
.aside {
	padding: 0;
}
.col-xs-offset-1 {
	margin-left: 4.16667%;
}
.col-xs-7 {
	width: 29.16667%;
}
*,
:after,
:before {
	box-sizing: border-box;
}
.reader-black-font,
.reader-black-font .history-mode .view-area,
.reader-black-font .history-mode .view-area pre,
.reader-black-font .main .kalamu-area,
.reader-black-font .main .markdown .text,
.reader-black-font input,
.reader-black-font select,
.reader-black-font textarea {
	font-family: -apple-system, SF UI Text, Arial, PingFang SC, Hiragino Sans GB, Microsoft YaHei, WenQuanYi Micro Hei, sans-serif;
}
a,
body {
	color: #333;
}
body {
	padding-top: 56px !important;
	min-width: 768px;
	font-family: -apple-system, SF UI Text, Arial, PingFang SC, Hiragino Sans GB, Microsoft YaHei, WenQuanYi Micro Hei, sans-serif;
	font-size: 17px;
}
body {
	font-family: Helvetica Neue, Helvetica, Arial, sans-serif;
	font-size: 14px;
	line-height: 1.42857;
	background-color: #fff;
}
.user-dynamic {
	padding-bottom: 6px;
}
.list {
	margin-bottom: 16px;
	padding-bottom: 16px;
	list-style: none;
	border-bottom: 1px solid #f0f0f0;
	clear: both;
}
ul {
	padding-left: 0;
}
ol,
ul {
	margin-top: 0;
	margin-bottom: 10px;
}
*,
:after,
:before {
	box-sizing: border-box;
}
ul {
	display: block;
	list-style-type: disc;
	margin-block-start: 1em;
	margin-block-end: 1em;
	margin-inline-start: 0px;
	margin-inline-end: 0px;
	padding-inline-start: 40px;
}
.person .aside .list li {
	margin-bottom: 10px;
}
li {
	line-height: 20px;
}
*,
:after,
:before {
	box-sizing: border-box;
}
li {
	display: list-item;
	text-align: -webkit-match-parent;
}
.list li a {
	display: inline-block;
}
.user-dynamic a {
	font-size: 14px;
	color: #333;
	line-height: 30px;
}

a,
a:hover {
	color: #3194d0;
}
a {
	cursor: pointer;
}
a,
body {
	color: #333;
}
a {
	color: #337ab7;
	text-decoration: none;
}
a {
	background-color: transparent;
}
*,
:after,
:before {
	box-sizing: border-box;
}
a:-webkit-any-link {
	color: -webkit-link;
	cursor: pointer;
	text-decoration: underline;
}
li {
	line-height: 20px;
}
li {
	text-align: -webkit-match-parent;
}
.aside .title {
	float: left;
	margin-bottom: 10px;
	font-size: 14px;
	color: #969696;
}
ul {
	list-style-type: disc;
}
.description,
.new-collection-block {
	position: relative;
	margin-bottom: 16px;
	padding: 0 0 16px;
	text-align: left;
	font-size: 0;
	border-bottom: 1px solid #f0f0f0;
	clear: both;
	word-break: break-word !important;
	word-break: break-all;
}
.description .js-intro,
.new-collection-block .js-intro {
	margin-bottom: 10px;
	line-height: 20px;
	font-size: 14px;
}
.description a,
.new-collection-block a {
	margin-right: 5px;
}
a,
a:hover {
	color: #3194d0;
}
#user-publications {
	box-sizing: border-box;
}
#user-courses {
	box-sizing: border-box;
}
.user-dynamic {
	padding-bottom: 6px;
}
.list li {
	margin-bottom: 10px;
}
.list li a {
	display: inline-block;
}
.user-dynamic i {
	margin-right: 10px;
	font-size: 20px;
	vertical-align: middle;
}
.iconfont {
	font-family: iconfont !important;
	font-size: inherit;
	font-style: normal;
	font-weight: 400 !important;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
}
.user-dynamic span {
	vertical-align: middle;
}
.user-dynamic a {
	font-size: 14px;
	color: #333;
	line-height: 30px;
}
a,
a:hover {
	color: #3194d0;
}
.list li {
	margin-bottom: 10px;
}
.user-dynamic span {
	vertical-align: middle;
}
.title {
	float: left;
	margin-bottom: 10px;
	font-size: 14px;
	color: #969696;
}
.list li a {
	display: inline-block;
}
.avatar,
.avatar-collection {
	margin-right: 5px;
	width: 32px;
	height: 32px;
}
body {
	padding-top: 56px !important;
	min-width: 768px;
	font-family: -apple-system, SF UI Text, Arial, PingFang SC, Hiragino Sans GB, Microsoft YaHei, WenQuanYi Micro Hei, sans-serif;
	font-size: 17px;
}
body {
	font-family: Helvetica Neue, Helvetica, Arial, sans-serif;
	font-size: 14px;
	line-height: 1.42857;
	background-color: #fff;
}
html {
	font-size: 10px;
	-webkit-tap-highlight-color: transparent;
}
html {
	font-family: sans-serif;
	-ms-text-size-adjust: 100%;
	-webkit-text-size-adjust: 100%;
}

html {
	color: -internal-root-color;
}
.description,
.new-collection-block {
	position: relative;
	margin-bottom: 16px;
	padding: 0 0 16px;
	text-align: left;
	font-size: 0;
	border-bottom: 1px solid #f0f0f0;
	clear: both;
	word-break: break-word !important;
	word-break: break-all;
}
.description .js-intro,
.new-collection-block .js-intro {
	margin-bottom: 10px;
	line-height: 20px;
	font-size: 14px;
}
*,
:after,
:before {
	box-sizing: border-box;
}
.description a,
.new-collection-block a {
	margin-right: 5px;
}
.description,
.new-collection-block {
	position: relative;
	margin-bottom: 16px;
	padding: 0 0 16px;
	text-align: left;
	font-size: 0;
	border-bottom: 1px solid #f0f0f0;
	clear: both;
	word-break: break-word !important;
	word-break: break-all;
}
.user-dynamic i {
	margin-right: 10px;
	font-size: 20px;
	vertical-align: middle;
}
.user-dynamic span {
	vertical-align: middle;
}
.list li a .ic-search-notebook {
	color: #969696;
	vertical-align: middle;
	margin-right: 5px;
}
.list li a {
	display: inline-block;
}
@media (max-width: 1080px) .person .aside .name {
	max-width: 176px;
}
.name {
	position: relative;
	max-width: 236px;
	vertical-align: middle;
	top: 1px;
	font-size: 14px;
	color: #333;
}

.aplayer.aplayer-fixed {
	position: fixed;
	bottom: 0;
	left: 0;
	right: 0;
	margin: 0;
	z-index: 99;
	overflow: visible;
	max-width: 400px;
	box-shadow: none;
}
.aplayer {
	background: #fff;
	font-family: Arial, Helvetica, sans-serif;
	margin: 5px;
	box-shadow: 0 2px 2px 0 rgba(0, 0, 0, 0.07), 0 1px 5px 0 rgba(0, 0, 0, 0.1);
	border-radius: 2px;
	overflow: hidden;
	-webkit-user-select: none;
	-moz-user-select: none;
	-ms-user-select: none;
	user-select: none;
	line-height: normal;
	position: relative;
}
.aplayer-fixed {
	position: fixed;
	bottom: 0;
	left: 0;
	right: 0;
	margin: 0;
	z-index: 99;
	overflow: visible;
	max-width: 400px;
	box-shadow: none;
}
.aplayer {
	background: #fff;
	font-family: Arial, Helvetica, sans-serif;
	margin: 5px;
	box-shadow: 0 2px 2px 0 rgba(0, 0, 0, 0.07), 0 1px 5px 0 rgba(0, 0, 0, 0.1);
	border-radius: 2px;
	overflow: hidden;
	-webkit-user-select: none;
	-moz-user-select: none;
	-ms-user-select: none;
	user-select: none;
	line-height: normal;
	position: relative;
}
.aplayer-list-hide {
	max-height: 0 !important;
}
.aplayer-fixed .aplayer-list {
	margin-bottom: 65px;
	border: 1px solid #eee;
	border-bottom: none;
}
.aplayer-withlist .aplayer-list {
	display: block;
}
.aplayer-list {
	overflow: auto;
	transition: all 0.5s ease;
	will-change: height;
	display: none;
	overflow: hidden;
}
.aplayer * {
	box-sizing: content-box;
}
.aplayer-list ol {
	list-style-type: none;
	margin: 0;
	padding: 0;
	overflow-y: auto;
}
.aplayer-list ol {
	background-color: #fff;
}
.aplayer * {
	box-sizing: content-box;
}
ol {
	display: block;
	list-style-type: decimal;
	margin-block-start: 1em;
	margin-block-end: 1em;
	margin-inline-start: 0px;
	margin-inline-end: 0px;
	padding-inline-start: 40px;
}

.aplayer-list-light {
	background: #e9e9e9;
}
.aplayer-list ol li:first-child {
	border-top: none;
}
.aplayer-list ol li {
	position: relative;
	height: 32px;
	line-height: 32px;
	padding: 0 15px;
	font-size: 12px;
	border-top: 1px solid #e9e9e9;
	cursor: pointer;
	transition: all 0.2s ease;
	overflow: hidden;
	margin: 0;
}
.aplayer-list-light .aplayer-list-cur {
	display: inline-block;
}
.aplayer-list-cur {
	display: none;
	width: 3px;
	height: 22px;
	position: absolute;
	left: 0;
	top: 5px;
	cursor: pointer;
}

li {
	display: list-item;
	text-align: -webkit-match-parent;
}
.aplayer-list-index {
	color: #666;
	margin-right: 12px;
	cursor: pointer;
}
.aplayer * {
	box-sizing: content-box;
}
.aplayer-list ol li {
	position: relative;
	height: 32px;
	line-height: 32px;
	padding: 0 15px;
	font-size: 12px;
	border-top: 1px solid #e9e9e9;
	cursor: pointer;
	transition: all 0.2s ease;
	overflow: hidden;
	margin: 0;
}
.aplayer .aplayer-list ol li .aplayer-list-author {
	color: #666;
	float: right;
	cursor: pointer;
}
.aplayer-list-index {
	color: #666;
	margin-right: 12px;
	cursor: pointer;
}
.aplayer-list ol li {
	position: relative;
	height: 32px;
	line-height: 32px;
	padding: 0 15px;
	font-size: 12px;
	border-top: 1px solid #e9e9e9;
	cursor: pointer;
	transition: all 0.2s ease;
	overflow: hidden;
	margin: 0;
}
.aplayer-list-author {
	color: #666;
	float: right;
	cursor: pointer;
}
.aplayer-fixed .aplayer-body {
	position: fixed;
	bottom: 0;
	left: 0;
	right: 0;
	margin: 0;
	z-index: 99;
	background: #fff;
	padding-right: 18px;
	transition: all 0.3s ease;
	max-width: 400px;
}
.aplayer-body {
	position: relative;
}
.aplayer-pic {
	position: relative;
	float: left;
	height: 66px;
	width: 66px;
	background-size: cover;
	background-position: 50%;
	transition: all 0.3s ease;
	cursor: pointer;
}
.aplayer-pic .aplayer-play {
	width: 26px;
	height: 26px;
	border: 2px solid #fff;
	bottom: 50%;
	right: 50%;
	margin: 0 -15px -15px 0;
}
.aplayer-pic .aplayer-button {
	position: absolute;
	border-radius: 50%;
	opacity: 0.8;
	text-shadow: 0 1px 1px rgba(0, 0, 0, 0.2);
	box-shadow: 0 1px 1px rgba(0, 0, 0, 0.2);
	background: rgba(0, 0, 0, 0.2);
	transition: all 0.1s ease;
}
.aplayer-pic .aplayer-play svg {
	position: absolute;
	top: 3px;
	left: 4px;
	height: 20px;
	width: 20px;
}
.aplayer svg {
	width: 100%;
	height: 100%;
}
svg:not(:root) {
	overflow: hidden;
}
.aplayer.aplayer-fixed .aplayer-info {
	-webkit-transform: scaleX(1);
	transform: scaleX(1);
	-webkit-transform-origin: 0 0;
	transform-origin: 0 0;
	transition: all 0.3s ease;
	border-bottom: none;
	border-top: 1px solid #e9e9e9;
}
.aplayer-withlist .aplayer-info {
	border-bottom: 1px solid #e9e9e9;
}
.aplayer-info {
	margin-left: 66px;
	padding: 14px 7px 0 10px;
	height: 66px;
	box-sizing: border-box;
}
.aplayer-fixed .aplayer-info .aplayer-music {
	width: calc(100% - 105px);
}
.aplayer-info .aplayer-music {
	overflow: hidden;
	white-space: nowrap;
	text-overflow: ellipsis;
	margin: 0 0 13px 5px;
	-webkit-user-select: text;
	-moz-user-select: text;
	-ms-user-select: text;
	user-select: text;
	cursor: default;
	padding-bottom: 2px;
	height: 20px;
}
.aplayer-info .aplayer-music .aplayer-title {
	font-size: 14px;
}
.aplayer-info .aplayer-music .aplayer-author {
	font-size: 12px;
	color: #666;
}
.aplayer-info .aplayer-controller {
	position: relative;
	display: flex;
}
.aplayer-info .aplayer-controller .aplayer-bar-wrap {
	margin: 0 0 0 5px;
	padding: 4px 0;
	cursor: pointer !important;
	flex: 1;
}
.aplayer-info .aplayer-controller .aplayer-bar-wrap .aplayer-bar {
	position: relative;
	height: 2px;
	width: 100%;
	background: #cdcdcd;
}
.aplayer-loaded {
	position: absolute;
	left: 0;
	top: 0;
	bottom: 0;
	background: #aaa;
	height: 2px;
	transition: all 0.5s ease;
}
.aplayer-played {
	position: absolute;
	left: 0;
	top: 0;
	bottom: 0;
	height: 2px;
}
.aplayer .aplayer-info .aplayer-controller .aplayer-bar-wrap .aplayer-bar .aplayer-played .aplayer-thumb {
	position: absolute;
	top: 0;
	right: 5px;
	margin-top: -4px;
	margin-right: -10px;
	height: 10px;
	width: 10px;
	border-radius: 50%;
	cursor: pointer;
	transition: all 0.3s ease-in-out;
	-webkit-transform: scale(0);
	transform: scale(0);
}
.aplayer .aplayer-info .aplayer-controller .aplayer-loading-icon {
	display: none;
}
svg {
	position: absolute;
	-webkit-animation: rotate 1s linear infinite;
	animation: rotate 1s linear infinite;
}
.aplayer svg {
	width: 100%;
	height: 100%;
}
svg:not(:root) {
	overflow: hidden;
}
.aplayer-time {
	position: relative;
	right: 0;
	bottom: 4px;
	height: 17px;
	color: #999;
	font-size: 11px;
	padding-left: 7px;
}
.aplayer-time-inner {
	vertical-align: middle;
}
.aplayer-time {
	position: relative;
	right: 0;
	bottom: 4px;
	height: 17px;
	color: #999;
	font-size: 11px;
	padding-left: 7px;
}
.aplayer-time {
	position: relative;
	right: 0;
	bottom: 4px;
	height: 17px;
	color: #999;
	font-size: 11px;
	padding-left: 7px;
}
.aplayer-icon {
	cursor: pointer;
	transition: all 0.2s ease;
}
.aplayer-icon-back {
	right: 75px;
}
.aplayer svg {
	width: 100%;
	height: 100%;
}
.aplayer-icon {
	cursor: pointer;
	transition: all 0.2s ease;
}
.aplayer-icon-play {
	right: 50px;
}
.aplayer-icon {
	cursor: pointer;
	transition: all 0.2s ease;
}

.aplayer-icon-forward {
	right: 25px;
}
.aplayer-volume-wrap {
	position: relative;
	display: inline-block;
	margin-left: 3px;
	cursor: pointer !important;
}
.aplayer-volume-bar-wrap {
	position: absolute;
	bottom: 15px;
	right: -3px;
	width: 25px;
	height: 0;
	z-index: 99;
	overflow: hidden;
	transition: all 0.2s ease-in-out;
}
.aplayer-volume-bar {
	position: absolute;
	bottom: 0;
	right: 10px;
	width: 5px;
	height: 35px;
	background: #aaa;
	border-radius: 2.5px;
	overflow: hidden;
}
.aplayer-icon-loop {
	margin-right: 2px;
}
.aplayer-icon-menu {
	display: inline;
}
.aplayer-icon-order {
	display: inline;
}
.aplayer-icon-lrc {
	display: none;
}
.aplayer-notice {
	opacity: 0;
	position: absolute;
	top: 50%;
	left: 50%;
	-webkit-transform: translate(-50%, -50%);
	transform: translate(-50%, -50%);
	font-size: 12px;
	border-radius: 4px;
	padding: 5px 10px;
	transition: all 0.3s ease-in-out;
	overflow: hidden;
	color: #fff;
	pointer-events: none;
	background-color: #f4f4f5;
	color: #909399;
}
.aplayer-miniswitcher {
	display: block;
}
.aplayer-miniswitcher {
	display: none;
	position: absolute;
	top: 0;
	right: 0;
	bottom: 0;
	height: 100%;
	background: #e6e6e6;
	width: 18px;
	border-radius: 0 2px 2px 0;
}
.aplayer-icon {
	height: 100%;
	width: 100%;
	-webkit-transform: rotateY(180deg);
	transform: rotateY(180deg);
	transition: all 0.3s ease;
}
.aplayer-icon {
	width: 15px;
	height: 15px;
	border: none;
	background-color: transparent;
	outline: none;
	cursor: pointer;
	opacity: 0.8;
	vertical-align: middle;
	padding: 0;
	font-size: 12px;
	margin: 0;
	display: inline-block;
}
.aplayer-lrc {
	display: block;
	position: fixed;
	bottom: 10px;
	left: 0;
	right: 0;
	margin: 0;
	z-index: 98;
	pointer-events: none;
	text-shadow: -1px -1px 0 #fff;
}
.aplayer-lrc {
	display: none;
	position: relative;
	height: 30px;
	text-align: center;
	overflow: hidden;
	margin: -10px 0 7px;
}
.aplayer-lrc-contents {
	width: 100%;
	transition: all 0.5s ease-out;
	-webkit-user-select: text;
	-moz-user-select: text;
	-ms-user-select: text;
	user-select: text;
	cursor: default;
}
</style>
