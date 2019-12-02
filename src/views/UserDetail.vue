<template>
	<div class="container">
		<div class="banner flex flex-center"><img :src="userVo.user.banner" class="cover shadow" /></div>
		<div class="info">
			<img :src="userVo.user.avatar" class="avatar" />
			<p>{{ userVo.user.nickname }}</p>
			<!-- <p>{{ userVo.user.introduction.slice(0, 20) }}...</p> -->
		</div>
		<div class="row">
			<div class="col-8">
				<div class="col-12" v-for="(item, index) in userVo.articleList" :key="index">
					<div class="media-wraaper shadow">
						<div class="media-left"><img :src="item.article.thumbnail" class="thumnail-xs" /></div>
						<div class="media-middle">
							<p class="title">{{ item.article.title }}</p>
							<p class="sub-title">{{ item.article.summary }}</p>
						</div>
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
							<hr>
						</li>
					</ul>
					<div class="title">个人介绍</div>
					<hr>
					<div class="description">
						<div class="js-intro">
							欢迎关注我的个人公众号：lulu_blog
							<br />
							坦然生活，默然体验，欣然恋念，偶然发言
						</div>
                         <hr>
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
							<hr>
							<!---->
							<ul class="list">
								<li>

									<a href="/c/4b1a5445dde5" target="_blank" class="name">父母的备忘录</a>
								</li>
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
							<hr>
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
</template>

<script>
export default {
	data() {
		return {
			userVo: {
				user: {},
				articleList: {}
			}
		};
	},
	created() {
		var id = this.$route.params.id;
		this.axios.get(this.GLOBAL.baseUrl + '/user/' + id).then(res => {
			console.log(res.data.data);
			this.userVo = res.data.data;
		});
	},
	methods: {}
};
</script>

<style scoped="scoped">
.banner {
	width: 100%;
	height: 300px;
}
.cover {
	width: 100%;
	height: 100%;
	border-radius: 10px;
}
.info {
	position: relative;
	top: -60px;
	left: -400px;
	color: #fff;
	margin-bottom: -50px;
	padding: 10px;
	background-color: rgb(0, 0, 0, 0.3);
	width: 130px;
	height: 130px;
	margin: 0 auto;
	text-align: center;
	border-radius: 20px;
}
.info img {
	width: 80px;
	height: 80px;
	border-radius: 50%;
	border: 2px solid #fff;
	margin-bottom: 10px;
}
.row {
	margin-top: -50px;
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
.person .aside {
    padding: 0;
}
.col-xs-offset-1 {
    margin-left: 4.16667%;
}
.col-xs-7 {
    width: 29.16667%;
}
*, :after, :before {
    box-sizing: border-box;
}
body.reader-black-font, body.reader-black-font .history-mode .view-area, body.reader-black-font .history-mode .view-area pre, body.reader-black-font .main .kalamu-area, body.reader-black-font .main .markdown .text, body.reader-black-font input, body.reader-black-font select, body.reader-black-font textarea {
    font-family: -apple-system,SF UI Text,Arial,PingFang SC,Hiragino Sans GB,Microsoft YaHei,WenQuanYi Micro Hei,sans-serif;
}
a, body {
    color: #333;
}
body {
    padding-top: 56px!important;
    min-width: 768px;
    font-family: -apple-system,SF UI Text,Arial,PingFang SC,Hiragino Sans GB,Microsoft YaHei,WenQuanYi Micro Hei,sans-serif;
    font-size: 17px;
}
body {
    font-family: Helvetica Neue,Helvetica,Arial,sans-serif;
    font-size: 14px;
    line-height: 1.42857;
    background-color: #fff;
}
.person .aside .user-dynamic {
    padding-bottom: 6px;
}
.person .aside .list {
    margin-bottom: 16px;
    padding-bottom: 16px;
    list-style: none;
    border-bottom: 1px solid #f0f0f0;
    clear: both;
}
ul {
    padding-left: 0;
}
ol, ul {
    margin-top: 0;
    margin-bottom: 10px;
}
*, :after, :before {
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
*, :after, :before {
    box-sizing: border-box;
}li {
    display: list-item;
    text-align: -webkit-match-parent;
}
.person .aside .list li a {
    display: inline-block;
}
.person .aside .user-dynamic a {
    font-size: 14px;
    color: #333;
    line-height: 30px;
}
body.reader-black-font, body.reader-black-font .history-mode .view-area, body.reader-black-font .history-mode .view-area pre, body.reader-black-font .main .kalamu-area, body.reader-black-font .main .markdown .text, body.reader-black-font input, body.reader-black-font select, body.reader-black-font textarea {
    font-family: -apple-system,SF UI Text,Arial,PingFang SC,Hiragino Sans GB,Microsoft YaHei,WenQuanYi Micro Hei,sans-serif;
}
.person .aside a, .person .aside a:hover {
    color: #3194d0;
}
a {
    cursor: pointer;
}
a, body {
    color: #333;
}
a {
    color: #337ab7;
    text-decoration: none;
}
a {
    background-color: transparent;
}
*, :after, :before {
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
.person .aside .title {
    float: left;
    margin-bottom: 10px;
    font-size: 14px;
    color: #969696;
}
ul {
    list-style-type: disc;
}
.person .aside .description, .person .aside .new-collection-block {
    position: relative;
    margin-bottom: 16px;
    padding: 0 0 16px;
    text-align: left;
    font-size: 0;
    border-bottom: 1px solid #f0f0f0;
    clear: both;
    word-break: break-word!important;
    word-break: break-all;
}
.person .aside .description .js-intro, .person .aside .new-collection-block .js-intro {
    margin-bottom: 10px;
    line-height: 20px;
    font-size: 14px;
}
.person .aside .description a, .person .aside .new-collection-block a {
    margin-right: 5px;
}
.person .aside a, .person .aside a:hover {
    color: #3194d0;
}
#user-publications {
    box-sizing: border-box;
}
#user-courses {
    box-sizing: border-box;
}
.person .aside .user-dynamic {
    padding-bottom: 6px;
}
.person .aside .list li {
    margin-bottom: 10px;
}
.person .aside .list li a {
    display: inline-block;
}
.person .aside .user-dynamic i {
    margin-right: 10px;
    font-size: 20px;
    vertical-align: middle;
}
.iconfont {
    font-family: iconfont!important;
    font-size: inherit;
    font-style: normal;
    font-weight: 400!important;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}
.person .aside .user-dynamic span {
    vertical-align: middle;
}
.person .aside .user-dynamic a {
    font-size: 14px;
    color: #333;
    line-height: 30px;
}
.person .aside a, .person .aside a:hover {
    color: #3194d0;
}
.person .aside .list li {
    margin-bottom: 10px;
}
.person .aside .user-dynamic span {
    vertical-align: middle;
}
.person .aside .title {
    float: left;
    margin-bottom: 10px;
    font-size: 14px;
    color: #969696;
}
.person .aside .list li a {
    display: inline-block;
}
.person .aside .avatar, .person .aside .avatar-collection {
    margin-right: 5px;
    width: 32px;
    height: 32px;
}
body {
    padding-top: 56px!important;
    min-width: 768px;
    font-family: -apple-system,SF UI Text,Arial,PingFang SC,Hiragino Sans GB,Microsoft YaHei,WenQuanYi Micro Hei,sans-serif;
    font-size: 17px;
}
body {
    font-family: Helvetica Neue,Helvetica,Arial,sans-serif;
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
.person .aside .description, .person .aside .new-collection-block {
    position: relative;
    margin-bottom: 16px;
    padding: 0 0 16px;
    text-align: left;
    font-size: 0;
    border-bottom: 1px solid #f0f0f0;
    clear: both;
    word-break: break-word!important;
    word-break: break-all;
}
.person .aside .description .js-intro, .person .aside .new-collection-block .js-intro {
    margin-bottom: 10px;
    line-height: 20px;
    font-size: 14px;
}
*, :after, :before {
    box-sizing: border-box;
}
.person .aside .description a, .person .aside .new-collection-block a {
    margin-right: 5px;
}
.person .aside .description, .person .aside .new-collection-block {
    position: relative;
    margin-bottom: 16px;
    padding: 0 0 16px;
    text-align: left;
    font-size: 0;
    border-bottom: 1px solid #f0f0f0;
    clear: both;
    word-break: break-word!important;
    word-break: break-all;
}
.person .aside .user-dynamic i {
    margin-right: 10px;
    font-size: 20px;
    vertical-align: middle;
}
.person .aside .user-dynamic span {	
    vertical-align: middle;
}
.person .aside .list li a .ic-search-notebook {
    color: #969696;
    vertical-align: middle;
    margin-right: 5px;
}
.person .aside .list li a {
    display: inline-block;
}
.person .aside a, .person .aside a:hover {
    color: #3194d0;
}
@media (max-width: 1080px)
.person .aside .name {
    max-width: 176px;
}
.person .aside .name {
    position: relative;
    max-width: 236px;
    vertical-align: middle;
    top: 1px;
    font-size: 14px;
    color: #333;
}
</style>
