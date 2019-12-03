<template>
	<div class="container">
		<div class="main-top  col-12 flex ">
			<img :src="userVo.user.avatar" class="avatar" />
			<p>{{ userVo.user.nickname }}</p>
			<button data-v-6292e408="" class="off  user-follow-button">
				<i data-v-6292e408="" class="iconfont"></i>
				<span data-v-6292e408="">关注</span>
			</button>
			<a class="btn btn-hollow" href="/notifications#/chats/new?mail_to=7133325">发简信</a>

			<div class="title"><i class="iconfont ic-man"></i></div>
			<div class="info">
				<ul>
					<li>
						<div class="meta-block">
							<a href="/users/bf26d103fb8d/following">
								<p>80</p>
								关注
								<i class="iconfont ic-arrow"></i>
							</a>
						</div>
					</li>
					<li>
						<div class="meta-block">
							<a href="/users/bf26d103fb8d/followers">
								<p>34591</p>
								粉丝
								<i class="iconfont ic-arrow"></i>
							</a>
						</div>
					</li>
					<li>
						<div class="meta-block">
							<a href="/u/bf26d103fb8d">
								<p>96</p>
								文章
								<i class="iconfont ic-arrow"></i>
							</a>
						</div>
					</li>
					<li>
						<div class="meta-block">
							<p>225309</p>
							<div>字数</div>
						</div>
					</li>
					<li>
						<div class="meta-block">
							<p>1079</p>
							<div>收获喜欢</div>
						</div>
					</li>
					<li>
						<div class="meta-block">
							<p>1016</p>
							<div>总资产</div>
						</div>
					</li>
				</ul>
			</div>
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
			<div i="aplayer col-12" class="aplayer aplayer-withlist aplayer-mobile aplayer-fixed">
				<div class="col-12">
					<div class="aplayer-list aplayer-list-hide" style="max-height: 250px">
						<ol style="max-height: 250px">
							<li class="aplayer-list-light">
								<span class="aplayer-list-cur" style="background-color: #b7daff;"></span>
								<span class="aplayer-list-index">1</span>
								<span class="aplayer-list-title">canon in d</span>
								<span class="aplayer-list-author">Brian&nbsp;Crain</span>
							</li>

							<li>
								<span class="aplayer-list-cur" style="background-color: #b7daff;"></span>
								<span class="aplayer-list-index">2</span>
								<span class="aplayer-list-title">Apologize</span>
								<span class="aplayer-list-author">Martin Ermen</span>
							</li>

							<li>
								<span class="aplayer-list-cur" style="background-color: #b7daff;"></span>
								<span class="aplayer-list-index">3</span>
								<span class="aplayer-list-title">River Flows in You</span>
								<span class="aplayer-list-author">Yiruma</span>
							</li>

							<li>
								<span class="aplayer-list-cur" style="background-color: #b7daff;"></span>
								<span class="aplayer-list-index">4</span>
								<span class="aplayer-list-title">惊蛰</span>
								<span class="aplayer-list-author">音阙诗听/王梓钰</span>
							</li>
						</ol>
					</div>
					<div class="aplayer-body" style="width: 400px;">
						<div
							class="aplayer-pic"
							style="background-image: url(&quot;http://p1.music.126.net/QGb9Vtyw7qHS00uEvPfM6g==/843325418547559.jpg?param=130y130&quot;);background-color: #b7daff;"
						>
							<div class="aplayer-button aplayer-play">
								<svg xmlns="http://www.w3.org/2000/svg" version="1.1" viewBox="0 0 16 31">
									<path
										d="M15.552 15.168q0.448 0.32 0.448 0.832 0 0.448-0.448 0.768l-13.696 8.512q-0.768 0.512-1.312 0.192t-0.544-1.28v-16.448q0-0.96 0.544-1.28t1.312 0.192z"
									></path>
								</svg>
							</div>
						</div>
						<div class="aplayer-info" style="display: block;">
							<div class="aplayer-music">
								<span class="aplayer-title">canon in d</span>
								<span class="aplayer-author">- Brian&nbsp;Crain</span>
							</div>
							<div class="aplayer-controller">
								<div class="aplayer-bar-wrap">
									<div class="aplayer-bar">
										<div class="aplayer-loaded" style="width: 52.1266%;"></div>
										<div class="aplayer-played" style="width: 0.141902%; background: rgb(183, 218, 255);">
											<span class="aplayer-thumb" style="background: #b7daff;">
												<span class="aplayer-loading-icon">
													<svg xmlns="http://www.w3.org/2000/svg" version="1.1" viewBox="0 0 32 32">
														<path
															d="M4 16c0-6.6 5.4-12 12-12s12 5.4 12 12c0 1.2-0.8 2-2 2s-2-0.8-2-2c0-4.4-3.6-8-8-8s-8 3.6-8 8 3.6 8 8 8c1.2 0 2 0.8 2 2s-0.8 2-2 2c-6.6 0-12-5.4-12-12z"
														></path>
													</svg>
												</span>
											</span>
										</div>
									</div>
								</div>
								<div class="aplayer-time aplayer-time-narrow">
									<span class="aplayer-time-inner">
										<span class="aplayer-ptime">00:00</span>
										/
										<span class="aplayer-dtime">05:11</span>
									</span>
									<span class="aplayer-icon aplayer-icon-back">
										<svg xmlns="http://www.w3.org/2000/svg" version="1.1" viewBox="0 0 32 32">
											<path
												d="M25.468 6.947c-0.326-0.172-0.724-0.151-1.030 0.057l-6.438 4.38v-3.553c0-0.371-0.205-0.71-0.532-0.884-0.326-0.172-0.724-0.151-1.030 0.057l-12 8.164c-0.274 0.186-0.438 0.496-0.438 0.827s0.164 0.641 0.438 0.827l12 8.168c0.169 0.115 0.365 0.174 0.562 0.174 0.16 0 0.321-0.038 0.468-0.116 0.327-0.173 0.532-0.514 0.532-0.884v-3.556l6.438 4.382c0.169 0.115 0.365 0.174 0.562 0.174 0.16 0 0.321-0.038 0.468-0.116 0.327-0.173 0.532-0.514 0.532-0.884v-16.333c0-0.371-0.205-0.71-0.532-0.884z"
											></path>
										</svg>
									</span>
									<span class="aplayer-icon aplayer-icon-play">
										<svg xmlns="http://www.w3.org/2000/svg" version="1.1" viewBox="0 0 16 31">
											<path
												d="M15.552 15.168q0.448 0.32 0.448 0.832 0 0.448-0.448 0.768l-13.696 8.512q-0.768 0.512-1.312 0.192t-0.544-1.28v-16.448q0-0.96 0.544-1.28t1.312 0.192z"
											></path>
										</svg>
									</span>
									<span class="aplayer-icon aplayer-icon-forward">
										<svg xmlns="http://www.w3.org/2000/svg" version="1.1" viewBox="0 0 32 32">
											<path
												d="M25.468 6.947c-0.326-0.172-0.724-0.151-1.030 0.057l-6.438 4.38v-3.553c0-0.371-0.205-0.71-0.532-0.884-0.326-0.172-0.724-0.151-1.030 0.057l-12 8.164c-0.274 0.186-0.438 0.496-0.438 0.827s0.164 0.641 0.438 0.827l12 8.168c0.169 0.115 0.365 0.174 0.562 0.174 0.16 0 0.321-0.038 0.468-0.116 0.327-0.173 0.532-0.514 0.532-0.884v-3.556l6.438 4.382c0.169 0.115 0.365 0.174 0.562 0.174 0.16 0 0.321-0.038 0.468-0.116 0.327-0.173 0.532-0.514 0.532-0.884v-16.333c0-0.371-0.205-0.71-0.532-0.884z"
											></path>
										</svg>
									</span>
									<div class="aplayer-volume-wrap">
										<button type="button" class="aplayer-icon aplayer-icon-volume-down">
											<svg xmlns="http://www.w3.org/2000/svg" version="1.1" viewBox="0 0 28 32">
												<path
													d="M13.728 6.272v19.456q0 0.448-0.352 0.8t-0.8 0.32-0.8-0.32l-5.952-5.952h-4.672q-0.48 0-0.8-0.352t-0.352-0.8v-6.848q0-0.48 0.352-0.8t0.8-0.352h4.672l5.952-5.952q0.32-0.32 0.8-0.32t0.8 0.32 0.352 0.8zM20.576 16q0 1.344-0.768 2.528t-2.016 1.664q-0.16 0.096-0.448 0.096-0.448 0-0.8-0.32t-0.32-0.832q0-0.384 0.192-0.64t0.544-0.448 0.608-0.384 0.512-0.64 0.192-1.024-0.192-1.024-0.512-0.64-0.608-0.384-0.544-0.448-0.192-0.64q0-0.48 0.32-0.832t0.8-0.32q0.288 0 0.448 0.096 1.248 0.48 2.016 1.664t0.768 2.528z"
												></path>
											</svg>
										</button>
										<div class="aplayer-volume-bar-wrap">
											<div class="aplayer-volume-bar"><div class="aplayer-volume" style="height: 70%; background: rgb(183, 218, 255);"></div></div>
										</div>
									</div>
									<button type="button" class="aplayer-icon aplayer-icon-order">
										<svg xmlns="http://www.w3.org/2000/svg" version="1.1" viewBox="0 0 32 32">
											<path d="M0.622 18.334h19.54v7.55l11.052-9.412-11.052-9.413v7.549h-19.54v3.725z"></path>
										</svg>
									</button>
									<button type="button" class="aplayer-icon aplayer-icon-loop">
										<svg xmlns="http://www.w3.org/2000/svg" version="1.1" viewBox="0 0 29 32">
											<path
												d="M2.667 7.027l1.707-1.693 22.293 22.293-1.693 1.707-4-4h-11.64v4l-5.333-5.333 5.333-5.333v4h8.973l-8.973-8.973v0.973h-2.667v-3.64l-4-4zM22.667 17.333h2.667v5.573l-2.667-2.667v-2.907zM22.667 6.667v-4l5.333 5.333-5.333 5.333v-4h-10.907l-2.667-2.667h13.573z"
											></path>
										</svg>
									</button>
									<button type="button" class="aplayer-icon aplayer-icon-menu">
										<svg xmlns="http://www.w3.org/2000/svg" version="1.1" viewBox="0 0 22 32">
											<path
												d="M20.8 14.4q0.704 0 1.152 0.48t0.448 1.12-0.48 1.12-1.12 0.48h-19.2q-0.64 0-1.12-0.48t-0.48-1.12 0.448-1.12 1.152-0.48h19.2zM1.6 11.2q-0.64 0-1.12-0.48t-0.48-1.12 0.448-1.12 1.152-0.48h19.2q0.704 0 1.152 0.48t0.448 1.12-0.48 1.12-1.12 0.48h-19.2zM20.8 20.8q0.704 0 1.152 0.48t0.448 1.12-0.48 1.12-1.12 0.48h-19.2q-0.64 0-1.12-0.48t-0.48-1.12 0.448-1.12 1.152-0.48h19.2z"
											></path>
										</svg>
									</button>
									<button type="button" class="aplayer-icon aplayer-icon-lrc aplayer-icon-lrc-inactivity">
										<svg xmlns="http://www.w3.org/2000/svg" version="1.1" viewBox="0 0 32 32">
											<path
												d="M26.667 5.333h-21.333c-0 0-0.001 0-0.001 0-1.472 0-2.666 1.194-2.666 2.666 0 0 0 0.001 0 0.001v-0 16c0 0 0 0.001 0 0.001 0 1.472 1.194 2.666 2.666 2.666 0 0 0.001 0 0.001 0h21.333c0 0 0.001 0 0.001 0 1.472 0 2.666-1.194 2.666-2.666 0-0 0-0.001 0-0.001v0-16c0-0 0-0.001 0-0.001 0-1.472-1.194-2.666-2.666-2.666-0 0-0.001 0-0.001 0h0zM5.333 16h5.333v2.667h-5.333v-2.667zM18.667 24h-13.333v-2.667h13.333v2.667zM26.667 24h-5.333v-2.667h5.333v2.667zM26.667 18.667h-13.333v-2.667h13.333v2.667z"
											></path>
										</svg>
									</button>
								</div>
							</div>
						</div>
						<div class="aplayer-notice"></div>
						<div class="aplayer-miniswitcher">
							<button class="aplayer-icon">
								<svg xmlns="http://www.w3.org/2000/svg" version="1.1" viewBox="0 0 32 32">
									<path d="M22 16l-10.105-10.6-1.895 1.987 8.211 8.613-8.211 8.612 1.895 1.988 8.211-8.613z"></path>
								</svg>
							</button>
						</div>
					</div>
					<div class="aplayer-lrc"><div class="aplayer-lrc-contents" style="transform: translateY(0); -webkit-transform: translateY(0);"></div></div>
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
}
*,
:after,
:before {
	box-sizing: border-box;
}
.iconfont {
	font-family: iconfont !important;
	font-size: inherit;
	font-style: normal;
	font-weight: 400 !important;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
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
/* .infoo {
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
} */
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
body.reader-black-font,
body.reader-black-font .history-mode .view-area,
body.reader-black-font .history-mode .view-area pre,
body.reader-black-font .main .kalamu-area,
body.reader-black-font .main .markdown .text,
body.reader-black-font input,
body.reader-black-font select,
body.reader-black-font textarea {
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
