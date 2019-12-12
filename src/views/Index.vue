<template>
	<div>
		<div class="back"><img src=../assets/img/background1.jpg /></div>
		<div class="row">
			<div class="col-3" v-for="(item, index) in topics" :key="index">
				<div class="card link shadow">
					<router-link :to="{ path: '/topic/' + item.id }"><img :src="item.logo" class="logo" /></router-link>
					<p class="title">{{ item.topicName }}</p>
					<p class="sub-title">{{ item.description.slice(0, 20) }}...</p>
					<p class="meta">
						<span class="gutter">{{ item.articles }}篇文章,</span>
						<span>{{ item.follows }}人关注</span>
					</p>
				</div>
			</div>
		</div>

		<div class="row">
			<div class="col-8">
				<h3>热门文章</h3>
				<div v-for="(item, index) in articles" :key="index" class="col-12">
					<div class="media-wraaper border">
						<div class="media-left">
							<router-link :to="{ path: '/user/' + item.article.userId }"><img :src="item.author.avatar" class="avatar-lg link" /></router-link>
							<p>{{ item.author.nickname }}</p>
							<strong>来自</strong>
							<p>{{ item.topic.topicName }}</p>
						</div>
						<div class="media-middle flex flex-around flex-left">
							<router-link :to="{ path: '/article/' + item.article.id }" class="subtitle">{{ item.article.title }}</router-link>
							<p class="sub-title link">{{ item.article.summary }}</p>
							<p>
								<span class="meta">{{ item.article.comments }}评论</span>
								<router-link :to="{ path: '/article/' + item.article.id }">
								<i class="iconfont gutter" style="color: #000000;">&#xe635;</i>
								</router-link>
								<span class="meta ">转发</span>
								<i class="iconfont meta gutter ">&#xe920;</i>
								<span class="meta">{{ item.article.likes }}喜欢</span>
								<i class="iconfont" style="color: rgb(255, 50, 0);">&#xe602;</i>
							</p>
							<span class="time">
								发表时间：{{ item.article.createTime.date.year }}年{{ item.article.createTime.date.month }}月{{ item.article.createTime.date.day }}日
							</span>
						</div>
					</div>
				</div>
			</div>
			<div class="col-4">
				<h3>热门作者</h3>
				<div class="row">
					<div v-for="(item, index) in users" :key="index" class="col-12">
						<div class="col-12 border box">
							<div class="flex-center-y">
								<router-link :to="{ path: '/user/' + item.id }"><img :src="item.avatar" class="avatar-xs link" /></router-link>
							</div>
							<div class="flex-center-y">
								<p class="sub-title">{{ item.nickname }}</p>
								<p class="meta">写了{{ item.articles }}篇文章</p>
								<p class="meta">{{ item.fans }}个粉丝</p>
							</div>
							<div class="flex-center-y"><i class="iconfont" style="color: rgb(0, 153, 0);">&#xe600;关注</i></div>
						</div>
					</div>
					<div class="GlobalSideBar col-12" data-za-detail-view-path-module="RightSideBar" data-za-extra-module="{&quot;card&quot;:{&quot;content&quot;:null}} ">
						<div class="col-12">
							<div class="Sticky" style="">
								<div class="Card GlobalWrite-card">
									<div class="GlobalWrite">
										<div class="GlobalWrite-nav">
											<a class="GlobalWrite-navItem" href="/question" target="_blank" rel="noopener noreferrer" title="回答">
												<svg class="Zi Zi--Paper GlobalWrite-navIcon" fill="currentColor" viewBox="0 0 24 24" width="24" height="24">
													<path
														d="M9.273 6.13c-1.103 0-1.439.064-1.782.243a1.348 1.348 0 0 0-.576.564c-.183.336-.248.664-.248 1.743v6.64c0 1.079.065 1.407.248 1.743.135.247.323.431.576.564.343.18.68.243 1.782.243h5.454c1.103 0 1.439-.064 1.782-.243.253-.133.44-.317.576-.564.183-.336.248-.664.248-1.743V8.68c0-1.079-.065-1.407-.248-1.743a1.348 1.348 0 0 0-.576-.564c-.343-.18-.68-.243-1.782-.243H9.273zm0-1.63h5.454c1.486 0 2.025.151 2.568.436.543.284.97.7 1.26 1.232.29.532.445 1.059.445 2.512v6.64c0 1.453-.155 1.98-.445 2.512-.29.531-.717.948-1.26 1.232-.543.285-1.082.436-2.568.436H9.273c-1.486 0-2.025-.151-2.568-.436a2.997 2.997 0 0 1-1.26-1.232C5.155 17.3 5 16.773 5 15.32V8.68c0-1.453.155-1.98.445-2.512.29-.531.717-.948 1.26-1.232.543-.285 1.082-.436 2.568-.436zM8.5 8.576v1.467h7V8.576h-7zm0 2.609v1.467h7v-1.467h-7zm0 2.608v1.468h4.667v-1.468H8.5z"
													></path>
												</svg>
												<div class="GlobalWrite-navTitle">写回答</div>
											</a>
											<a class="GlobalWrite-navItem" href="//zhuanlan.zhihu.com/write" target="_blank" rel="noopener noreferrer" title="写文章">
												<svg class="Zi Zi--WriteArticle GlobalWrite-navIcon" fill="currentColor" viewBox="0 0 24 24" width="24" height="24">
													<path
														d="M15.764 6.779l-3.76 3.765c-.428.43-.555.567-.667.713a1.666 1.666 0 0 0-.208.348c-.076.167-.137.344-.314.926l-.073.243.242-.074c.58-.177.757-.238.925-.314.13-.06.232-.12.347-.209.146-.112.282-.239.712-.668l3.759-3.766-.963-.964zm.963-.965l.963.965.685-.686c.167-.168.227-.263.253-.349a.187.187 0 0 0 0-.12c-.026-.086-.086-.18-.253-.348l-.148-.148c-.167-.167-.262-.228-.348-.254a.187.187 0 0 0-.12 0c-.085.026-.18.087-.347.254l-.685.686zm.87 5.471l1.702-1.705v5.549c0 1.52-.158 2.07-.455 2.626a3.096 3.096 0 0 1-1.287 1.29c-.555.297-1.105.455-2.623.455h-5.57c-1.517 0-2.068-.158-2.622-.455a3.096 3.096 0 0 1-1.287-1.29C5.158 17.2 5 16.65 5 15.13v-5.58c0-1.52.158-2.071.455-2.627a3.096 3.096 0 0 1 1.287-1.289c.554-.297 1.105-.455 2.622-.455h3.497l-1.702 1.705H9.364c-1.126 0-1.47.066-1.82.254-.258.138-.45.33-.588.59-.188.35-.254.694-.254 1.822v5.58c0 1.128.066 1.472.254 1.822.138.259.33.452.588.59.35.188.694.254 1.82.254h5.57c1.127 0 1.47-.066 1.82-.254.258-.138.45-.331.589-.59.187-.35.253-.694.253-1.822v-3.844zm1.593-7.121l.148.147c.33.33.502.616.594.918.09.301.09.61 0 .911-.092.302-.265.587-.594.917l-5.408 5.416c-.486.487-.648.635-.845.786a3.02 3.02 0 0 1-.614.37c-.226.102-.433.176-1.091.376l-.852.26a1.021 1.021 0 0 1-1.275-1.277l.26-.854c.2-.659.273-.866.375-1.092.103-.227.218-.418.369-.616.15-.197.299-.36.785-.846l5.407-5.416c.33-.33.614-.504.915-.595.301-.092.61-.092.91 0 .301.09.586.264.916.595z"
													></path>
												</svg>
												<div class="GlobalWrite-navTitle">写文章</div>
											</a>
											<div class="GlobalWrite-navItem">
												<svg class="Zi Zi--WritePin GlobalWrite-navIcon" fill="currentColor" viewBox="0 0 24 24" width="24" height="24">
													<path
														d="M17.13 5.52V3.5h1.35v2.02h2.02v1.35h-2.02V8.9h-1.35V6.86H15.1V5.52h2.03zm-.17 4.9h1.7v4.76c0 1.5-.17 2.05-.46 2.6-.3.55-.73.98-1.28 1.27-.54.3-1.1.45-2.6.45h-5.5c-1.5 0-2.05-.16-2.6-.45-.55-.3-.98-.72-1.27-1.27-.3-.55-.45-1.1-.45-2.6v-5.5c0-1.5.16-2.06.45-2.6.3-.55.72-.98 1.27-1.28.55-.3 1.1-.45 2.6-.45h4.78v1.7H8.8c-1.12 0-1.46.05-1.8.24-.26.1-.45.3-.58.55-.2.35-.26.7-.26 1.8v5.5c0 1.13.07 1.47.26 1.8.13.27.32.46.58.6.34.18.68.25 1.8.25h5.5c1.12 0 1.46-.06 1.8-.25.27-.13.46-.32.6-.58.18-.34.24-.68.24-1.8V10.4l.02.02zm-3.86-.22c.7-.16 1.45.06 1.98.6.83.83.83 2.2 0 3.04l-.03.03c-.84.85-2.2.85-3.04 0l-1.92-2a.628.628 0 0 0-.88 0l-.04.04c-.25.28-.25.7 0 .95.15.16.37.22.57.17.4-.1.82.18.9.58.1.4-.16.82-.57.9-.7.17-1.46-.04-1.98-.58-.83-.85-.83-2.2 0-3.06l.03-.02c.86-.85 2.2-.85 3.05 0l1.93 1.95c.24.25.63.25.87 0l.03-.02a.67.67 0 0 0 0-.93.687.687 0 0 0-.58-.17c-.4.1-.8-.16-.9-.57-.1-.4.16-.8.57-.9l.01-.01z"
													></path>
												</svg>
												<div class="GlobalWrite-navTitle">写想法</div>
											</div>
										</div>
										<div class="GlobalWriteAnswerLater GlobalWrite-answerLater">
											<a class="GlobalSideBar-navLink" href="/question/later" target="_blank" title="我的稍后答" data-za-detail-view-id="5370">
												<div class="GlobalWriteAnswerLater-text" style="transform: scale(1);">
													<svg class="Zi Zi--Later GlobalWriteAnswerLater-icon" fill="currentColor" viewBox="0 0 24 24" width="24" height="24">
														<path
															d="M5.591 10.714C6.373 7.434 9.257 5 12.696 5c4.04 0 7.314 3.358 7.314 7.5 0 4.142-3.274 7.5-7.314 7.5-2.483 0-4.755-1.28-6.1-3.363a.816.816 0 0 1 .22-1.114.772.772 0 0 1 1.086.227c1.058 1.638 2.842 2.643 4.794 2.643 3.174 0 5.747-2.638 5.747-5.893s-2.573-5.893-5.747-5.893c-2.713 0-4.988 1.93-5.59 4.523l1.145.315a.418.418 0 0 1 .102.762l-2.36 1.397a.418.418 0 0 1-.577-.154l-1.362-2.42a.418.418 0 0 1 .475-.608l1.062.292zm7.987 1.376l2.794 1.654a.784.784 0 0 1 .283 1.059l-.015.027a.781.781 0 0 1-1.08.29l-3.112-1.844a.784.784 0 0 1-.145-.092.784.784 0 0 1-.292-.757V8.784a.784.784 0 1 1 1.567 0v3.306z"
														></path>
													</svg>
													<div class="GlobalSideBar-navText">我的稍后答</div>
												</div>
											</a>
										</div>
										<div class="GlobalWrite-draft">
											<a class="GlobalSideBar-navLink" href="/draft" target="_blank" title="草稿" data-za-not-track-link="true">
												<svg class="Zi Zi--Draft" fill="currentColor" viewBox="0 0 24 24" width="18" height="18">
													<path
														d="M7.958 13.23c.588 1.704 2.176 2.924 4.042 2.924 1.866 0 3.454-1.22 4.042-2.923h4.53c.788 0 1.428.64 1.428 1.428v5.912c0 .79-.64 1.429-1.429 1.429H3.43C2.639 22 2 21.36 2 20.571V14.66c0-.789.64-1.428 1.429-1.428h4.53zm11.185-2h-4.526l-.466 1.348c-.325.943-1.186 1.576-2.151 1.576-.965 0-1.826-.633-2.151-1.576l-.466-1.347H4.857V4.46C4.857 3.655 5.511 3 6.32 3h11.395c.79 0 1.429.64 1.429 1.429v6.802z"
													></path>
												</svg>
												<div class="GlobalSideBar-navText">我的草稿</div>
											</a>
										</div>
									</div>
								</div>
								<div class="Card CreatorEntrance">
									<a class="CreatorEntrance-link CreatorEntrance-Link--smallIcon" href="/creator" target="_blank" data-za-detail-view-id="6848">
										<div class="CreatorEntrance-hint ProfileSideCreator-creatorEntranceHint CreatorEntrancePage-hint--smallIcon">
											<svg class="Zi Zi--Creator CreatorEntrance-creator" fill="currentColor" viewBox="0 0 24 24" width="24" height="24">
												<path
													d="M15.075 15.388l-3.024 3.024a4.041 4.041 0 0 0-1.014 1.697l-.26.868C7.844 20.986 4.91 21 2 21c.026-3.325 0-3.304.59-3.956 1.237-1.368 6.251-.68 6.44-2.976.043-.518-.36-1.06-.725-1.69C6.285 8.87 5.512 2 11.5 2c5.988 0 5.15 7.072 3.246 10.378-.357.62-.795 1.217-.724 1.77.073.571.477.958 1.053 1.24zm5.402 1.672c.523.55.523.646.523 3.94a535.11 535.11 0 0 0-4.434-.028l3.911-3.912zm-7.88 2.699c.111-.37.312-.705.584-.978l4.76-4.76a.291.291 0 0 1 .412 0l1.626 1.626a.291.291 0 0 1 0 .411l-4.76 4.76c-.272.273-.608.474-.978.585l-1.96.588a.219.219 0 0 1-.272-.272l.589-1.96zm9.157-6.742a.839.839 0 0 1 0 1.187l-.94.94a.28.28 0 0 1-.395 0l-1.563-1.563a.28.28 0 0 1 0-.395l.94-.94a.839.839 0 0 1 1.187 0l.771.771z"
													fill-rule="evenodd"
												></path>
											</svg>
											<div class="CreatorEntrance-text">
												<div class="CreatorEntrance-indexPageTitle">
													<div class="css-3j2kqe">
														创作者中心
														<span class="css-1ntg9ig">去开通</span>
													</div>
												</div>
											</div>
											<svg
												class="Zi Zi--ArrowRight CreatorEntrance-arrow CreatorEntrance-arrow--smallIcon"
												fill="currentColor"
												viewBox="0 0 24 24"
												width="24"
												height="24"
											>
												<path
													d="M9.218 16.78a.737.737 0 0 0 1.052 0l4.512-4.249a.758.758 0 0 0 0-1.063L10.27 7.22a.737.737 0 0 0-1.052 0 .759.759 0 0 0-.001 1.063L13 12l-3.782 3.716a.758.758 0 0 0 0 1.063z"
													fill-rule="evenodd"
												></path>
											</svg>
										</div>
									</a>
								</div>
								<div class="StoryCompetitionBanner">
									<a data-za-not-track-link="true" target="_blank" href="https://www.zhihu.com/xen/market/story-competition"></a>
								</div>
								<div class="Card">
									<ul class="GlobalSideBar-categoryList">
										<li class="GlobalSideBar-categoryItem">
											<a
												href="/lives"
												target="_blank"
												title="Live"
												data-za-not-track-link="true"
												type="button"
												class="Button Button--plain"
												style="color: rgb(255, 207, 0);"
											>
												<span class="GlobalSideBar-categoryIcon">
													<svg class="Zi Zi--Live" fill="currentColor" viewBox="0 0 24 24" width="24" height="24">
														<path
															d="M13.693 10.354l1.634-7.542c.195-.901-.16-1.083-.798-.39l-9.18 9.97c-.638.693-.377 1.254.582 1.254h5.376l-1.634 7.542c-.195.901.16 1.083.798.39l9.18-9.97c.638-.693.377-1.254-.582-1.254h-5.376z"
														></path>
													</svg>
												</span>
												<span class="GlobalSideBar-categoryLabel">Live</span>
											</a>
										</li>
										<li class="GlobalSideBar-categoryItem">
											<a
												href="/pub/"
												target="_blank"
												title="书店"
												data-za-not-track-link="true"
												type="button"
												class="Button Button--plain"
												style="color: rgb(67, 212, 128);"
											>
												<span class="GlobalSideBar-categoryIcon">
													<svg class="Zi Zi--Ebook" fill="currentColor" viewBox="0 0 24 24" width="24" height="24">
														<path
															d="M16 17.649V2.931a.921.921 0 0 0-.045-.283.943.943 0 0 0-1.182-.604L4.655 5.235A.932.932 0 0 0 4 6.122v14.947c0 .514.421.931.941.931H19.06c.52 0 .941-.417.941-.93V7.292a.936.936 0 0 0-.941-.931h-.773v12.834a.934.934 0 0 1-.83.924L6.464 21.416c-.02.002 2.94-.958 8.883-2.881a.932.932 0 0 0 .653-.886z"
															fill-rule="evenodd"
														></path>
													</svg>
												</span>
												<span class="GlobalSideBar-categoryLabel">书店</span>
											</a>
										</li>
										<li class="GlobalSideBar-categoryItem">
											<a
												href="/roundtable"
												target="_blank"
												title="圆桌"
												data-za-not-track-link="true"
												type="button"
												class="Button Button--plain"
												style="color: rgb(0, 132, 255);"
											>
												<span class="GlobalSideBar-categoryIcon">
													<svg class="Zi Zi--Org" fill="currentColor" viewBox="0 0 24 24" width="24" height="24">
														<path
															d="M10.786 8.41a8.938 8.938 0 0 0-3.968-2.528c-.305-1.719.814-3.337 2.442-3.741 1.221-.405 2.646.101 3.46 1.011 1.045 1.38.915 3.64.814 4.348-.102 1.315-1.221 3.034-1.323 3.135-.305-.809-.814-1.517-1.425-2.225zm-2.442 2.832c-1.526.202-3.052 1.01-4.171 2.123-1.12-.404-1.934-1.314-2.137-2.427-.316-2.427 1.526-3.64 2.849-3.842 1.628-.371 2.849.505 4.07 1.415 1.146 1.012 2.035 2.63 2.035 2.73-.916-.202-1.832-.1-2.646 0zm4.986.303c.509-.607.931-1.586 1.12-2.225.318-1.039.61-3.134.203-4.651 1.323-1.011 3.154-1.011 4.477.303 1.235 1.146 1.017 2.933.814 3.438-.663 1.581-1.933 2.326-3.256 2.832-1.221.404-3.256.303-3.358.303zm-2.645 1.011c-.51.607-.916 1.416-1.221 2.326-.407 1.314-.643 3.06-.102 4.55-1.323 1.011-3.256 1.011-4.477-.202-1.198-1.124-1.018-2.932-.814-3.438.599-1.605 1.933-2.326 3.256-2.831.916-.304 3.256-.405 3.358-.405zm9.259-1.82c1.017.404 1.933 1.315 2.035 2.427.233 2.57-1.526 3.64-2.849 3.842-1.526 0-2.85-.505-4.07-1.415-1.018-.81-2.035-2.528-2.035-2.63.916.203 1.831.102 2.645 0 1.628-.404 3.053-1.112 4.274-2.224zm-6.716 4.854c1.065 1.08 2.442 2.022 4.07 2.528.306 1.719-.814 3.235-2.442 3.741-1.22.405-2.645-.101-3.46-1.011-1.1-1.481-1.017-3.54-.915-4.247.102-1.315 1.221-3.034 1.323-3.135.305.708.721 1.44 1.424 2.124z"
														></path>
													</svg>
												</span>
												<span class="GlobalSideBar-categoryLabel">圆桌</span>
											</a>
										</li>
										<li class="GlobalSideBar-categoryItem">
											<a
												href="//zhuanlan.zhihu.com"
												target="_blank"
												title="专栏"
												data-za-not-track-link="true"
												type="button"
												class="Button Button--plain"
												style="color: rgb(15, 136, 235);"
											>
												<span class="GlobalSideBar-categoryIcon">
													<svg class="Zi Zi--Edit" fill="currentColor" viewBox="0 0 24 24" width="24" height="24">
														<path
															d="M4.076 16.966a4.19 4.19 0 0 1 1.05-1.76l8.568-8.569a.524.524 0 0 1 .741 0l2.928 2.927a.524.524 0 0 1 0 .74l-8.568 8.57c-.49.49-1.096.852-1.761 1.051l-3.528 1.058a.394.394 0 0 1-.49-.488l1.06-3.53zM20.558 4.83c.59.59.59 1.546 0 2.136l-1.693 1.692a.503.503 0 0 1-.712 0l-2.812-2.812a.504.504 0 0 1 0-.712l1.693-1.693a1.51 1.51 0 0 1 2.135 0l1.389 1.389z"
														></path>
													</svg>
												</span>
												<span class="GlobalSideBar-categoryLabel">专栏</span>
											</a>
										</li>
										<li class="GlobalSideBar-categoryItem">
											<a
												href="/consult"
												target="_blank"
												title="付费咨询"
												data-za-not-track-link="true"
												type="button"
												class="Button Button--plain"
												style="color: rgb(84, 120, 240);"
											>
												<span class="GlobalSideBar-categoryIcon">
													<svg class="Zi Zi--Infinity" fill="currentColor" viewBox="0 0 24 24" width="24" height="24">
														<path
															d="M11.267 10.188h-2.69a.26.26 0 0 0-.261.26v.508c0 .149.117.26.262.26h2.896v1.54H8.578a.26.26 0 0 0-.262.259v.508c0 .15.117.26.262.26h2.896v2.31c0 .139.119.257.265.257h.522a.258.258 0 0 0 .265-.257v-2.31h2.896a.26.26 0 0 0 .262-.26v-.508a.257.257 0 0 0-.262-.26h-2.896v-1.54h2.896a.26.26 0 0 0 .262-.26v-.507a.257.257 0 0 0-.262-.26h-2.69l2.51-2.636a.26.26 0 0 0-.004-.366l-.423-.413a.253.253 0 0 0-.36.01L12 9.418 9.545 6.784a.248.248 0 0 0-.36-.011l-.423.413a.264.264 0 0 0-.004.366l2.509 2.636zM12 19.973c-1.101 0-2.16-.15-3.152-.43-.532.18-5.27 2.177-4.743 1.179.527-.998 1.58-2.746.806-3.25C3.11 15.936 2 13.822 2 11.486 2 6.8 6.477 3 12 3s10 3.8 10 8.487-4.477 8.486-10 8.486z"
														></path>
													</svg>
												</span>
												<span class="GlobalSideBar-categoryLabel">付费咨询</span>
											</a>
										</li>
										<li class="GlobalSideBar-categoryItem">
											<a
												href="/wiki"
												target="_blank"
												title="百科"
												data-za-not-track-link="true"
												type="button"
												class="Button Button--plain"
												style="color: rgb(88, 104, 209);"
											>
												<span class="GlobalSideBar-categoryIcon">
													<svg class="Zi Zi--KnowledgeBase" fill="currentColor" viewBox="0 0 24 24" width="24" height="24">
														<path
															d="M21 9.749v9.91c0 .74-.604 1.341-1.35 1.341H4.35C3.604 21 3 20.4 3 19.659V9.319c0-.503.283-.963.733-1.193l4.892-2.5V3.341c0-.74.604-1.341 1.35-1.341.267 0 .527.078.749.225l9.675 6.408c.375.249.601.668.601 1.116zM8.297 8.307L5.372 9.802A.223.223 0 0 0 5.25 10v8.54c0 .124.1.224.225.224h8.586a.223.223 0 1 0 .124-.41l-4.959-3.259a1.339 1.339 0 0 1-.601-1.116V8.506a.224.224 0 0 0-.328-.199z"
														></path>
													</svg>
												</span>
												<span class="GlobalSideBar-categoryLabel">百科</span>
											</a>
										</li>
									</ul>
								</div>
								<div class="Pc-card Card">
									<a
										class="Banner-link"
										href="https://e.cn.miaozhen.com/r/k=2146194&amp;p=7UgW3&amp;dx=__IPDX__&amp;rt=2&amp;ns=223.104.4.44&amp;ni=__IESID__&amp;v=__LOC__&amp;xa=__ADPLATFORM__&amp;tr=__REQUESTID__&amp;mo=3&amp;m0=__OPENUDID__&amp;m0a=__DUID__&amp;m1=__ANDROIDID1__&amp;m1a=__ANDROIDID__&amp;m2=__IMEI__&amp;m4=__AAID__&amp;m5=__IDFA__&amp;m6=__MAC1__&amp;m6a=__MAC__&amp;m11=__OAID__&amp;vv=1&amp;vo=38096a7b9&amp;vr=2&amp;o=https%3A%2F%2Fstore.playstation.com%2Fzh-hans-hk%2Fgrid%2FSTORE-MSF86012-BLACKFRIDAY19%3Femcid%3Ddi-st-225629%26utm_medium%3DDisplay%26utm_campaign%3D20191122_sieja_display_blackfriday_zhihupcbr%26utm_source%3D%26utm_term%3Ddi-st-225629%26utm_content%3DBlack_Friday"
										target="_blank"
									></a>
								</div>
								<div class="Card">
									<ul class="GlobalSideBar-navList">
										<li class="GlobalSideBar-navItem GlobalSideBar-starItem">
											<a target="_blank" data-za-not-track-link="true" type="button" class="Button GlobalSideBar-navLink Button--plain" href="/collections">
												<svg class="Zi Zi--Star GlobalSideBar-navIcon" fill="currentColor" viewBox="0 0 24 24" width="18" height="18">
													<path
														d="M5.515 19.64l.918-5.355-3.89-3.792c-.926-.902-.639-1.784.64-1.97L8.56 7.74l2.404-4.871c.572-1.16 1.5-1.16 2.072 0L15.44 7.74l5.377.782c1.28.186 1.566 1.068.64 1.97l-3.89 3.793.918 5.354c.219 1.274-.532 1.82-1.676 1.218L12 18.33l-4.808 2.528c-1.145.602-1.896.056-1.677-1.218z"
														fill-rule="evenodd"
													></path>
												</svg>
												<span class="GlobalSideBar-navText">我的收藏</span>
												<span class="GlobalSideBar-navNumber">0</span>
											</a>
										</li>
										<li class="GlobalSideBar-navItem GlobalSideBar-questionListItem">
											<a
												target="_blank"
												data-za-not-track-link="true"
												type="button"
												class="Button GlobalSideBar-navLink Button--plain"
												href="/people/shi-gan-dang-29-47/following/questions"
											>
												<svg class="Zi Zi--HelpBubble GlobalSideBar-navIcon" fill="currentColor" viewBox="0 0 24 24" width="18" height="18">
													<path
														d="M5.74 4h12.52c.961 0 1.74.775 1.74 1.73V16.27c0 .955-.779 1.73-1.74 1.73h-3.825l-1.658 2.044a1 1 0 0 1-1.554 0l-1.658-2.044H5.74C4.78 18 4 17.224 4 16.27V5.73C4 4.775 4.778 4 5.74 4zM12 16a.976.976 0 0 0 .705-.287.951.951 0 0 0 .295-.712.954.954 0 0 0-.295-.714A.976.976 0 0 0 12 14a.962.962 0 0 0-.705.295A.961.961 0 0 0 11 15c0 .284.098.522.295.713A.975.975 0 0 0 12 16zm1.278-4.924a36.81 36.81 0 0 0 1.023-.975c.19-.193.354-.422.492-.688.138-.266.207-.575.207-.928 0-.448-.12-.864-.363-1.246a2.517 2.517 0 0 0-1.029-.906C13.164 6.111 12.652 6 12.072 6c-.624 0-1.17.133-1.638.399-.468.265-.824.6-1.068 1.005-.244.405-.366.804-.366 1.2 0 .19.077.368.231.531a.747.747 0 0 0 .567.246c.38 0 .638-.234.774-.703.144-.449.32-.788.528-1.019.208-.23.532-.345.972-.345.376 0 .683.114.921.342.238.229.357.51.357.841 0 .17-.039.328-.117.473a1.782 1.782 0 0 1-.288.396c-.114.118-.3.294-.555.526a9.71 9.71 0 0 0-.696.688c-.172.194-.31.418-.414.673a2.391 2.391 0 0 0-.156.906c0 .278.071.488.213.63a.716.716 0 0 0 .525.211c.4 0 .638-.216.714-.648.044-.203.077-.345.099-.426.022-.081.053-.162.093-.243.04-.081.101-.17.183-.268.082-.098.191-.21.327-.34z"
														fill-rule="evenodd"
													></path>
												</svg>
												<span class="GlobalSideBar-navText">我关注的问题</span>
												<span class="GlobalSideBar-navNumber">1</span>
											</a>
										</li>
										<li class="GlobalSideBar-navItem GlobalSideBar-inviteItem">
											<a
												target="_blank"
												data-za-not-track-link="true"
												type="button"
												class="Button GlobalSideBar-navLink Button--plain"
												href="/question/invited"
											>
												<svg class="Zi Zi--Invite GlobalSideBar-navIcon" fill="currentColor" viewBox="0 0 24 24" width="18" height="18">
													<path
														d="M4 10V8a1 1 0 1 1 2 0v2h2a1 1 0 0 1 0 2H6v2a1 1 0 0 1-2 0v-2H2a1 1 0 0 1 0-2h2zm10.455 2c-2.21 0-4-1.79-4-4s1.79-4 4-4 4 1.79 4 4-1.79 4-4 4zm-7 6c0-2.66 4.845-4 7.272-4C17.155 14 22 15.34 22 18v1.375c0 .345-.28.625-.625.625H8.08a.625.625 0 0 1-.625-.625V18z"
														fill-rule="evenodd"
													></path>
												</svg>
												<span class="GlobalSideBar-navText">我的邀请</span>
												<span class="GlobalSideBar-navNumber">172</span>
											</a>
										</li>
										<li class="GlobalSideBar-navItem GlobalSideBar-couponItem">
											<a target="_blank" data-za-not-track-link="true" type="button" class="Button GlobalSideBar-navLink Button--plain" href="/coupon">
												<svg class="Zi Zi--Coupon GlobalSideBar-navIcon" fill="currentColor" viewBox="0 0 24 24" width="18" height="18">
													<path
														d="M21.515 10.131c-1.1.567-1.471.996-1.471 1.869s.388 1.348 1.471 1.869c.356.26.485.429.485.934v2.803c0 .766-.647 1.394-1.471 1.394H3.47C2.663 19 2 18.387 2 17.606v-2.803c0-.26.08-.674.517-.934.615-.2 1.456-.613 1.456-1.869 0-.965-.793-1.578-1.472-1.869-.452-.23-.485-.52-.485-.934V6.394C2.016 5.628 2.663 5 3.487 5H20.53C21.337 5 22 5.613 22 6.394v2.803c0 .398 0 .628-.485.934zM10.5 12c0 .834.672 1.5 1.5 1.5.834 0 1.5-.672 1.5-1.5 0-.834-.672-1.5-1.5-1.5-.834 0-1.5.672-1.5 1.5zm5 0c0 .834.672 1.5 1.5 1.5.834 0 1.5-.672 1.5-1.5 0-.834-.672-1.5-1.5-1.5-.834 0-1.5.672-1.5 1.5zm-10 0c0 .834.672 1.5 1.5 1.5.834 0 1.5-.672 1.5-1.5 0-.834-.672-1.5-1.5-1.5-.834 0-1.5.672-1.5 1.5z"
													></path>
												</svg>
												<span class="GlobalSideBar-navText">我的礼券</span>
											</a>
										</li>
										<li class="GlobalSideBar-navItem GlobalSideBar-serviceItem">
											<a target="_blank" data-za-not-track-link="true" type="button" class="Button GlobalSideBar-navLink Button--plain" href="/community">
												<svg class="Zi Zi--Community GlobalSideBar-navIcon" fill="currentColor" viewBox="0 0 24 24" width="18" height="18">
													<path
														d="M5.74 4h12.52c.961 0 1.74.775 1.74 1.73V16.27c0 .955-.779 1.73-1.74 1.73h-3.825l-1.658 2.044a1 1 0 0 1-1.554 0l-1.658-2.044H5.74C4.78 18 4 17.224 4 16.27V5.73C4 4.775 4.778 4 5.74 4zM7 8.98c0 .554.449.996 1.003.996h4.994A.992.992 0 0 0 14 8.981a.997.997 0 0 0-1.003-.995H8.003A.992.992 0 0 0 7 8.98zm0 4c0 .554.446.996.995.996h8.01a.993.993 0 0 0 .995-.995.993.993 0 0 0-.995-.995h-8.01A.993.993 0 0 0 7 12.98z"
														fill-rule="evenodd"
													></path>
												</svg>
												<span class="GlobalSideBar-navText">站务中心</span>
											</a>
										</li>
										<li class="GlobalSideBar-navItem GlobalSideBar-copyrightItem">
											<a target="_blank" data-za-not-track-link="true" type="button" class="Button GlobalSideBar-navLink Button--plain" href="/copyright">
												<svg class="Zi Zi--Copyright GlobalSideBar-navIcon" fill="currentColor" viewBox="0 0 24 24" width="18" height="18">
													<path
														d="M16.517 15.815a5.871 5.871 0 0 1-4.481 2.078 5.865 5.865 0 0 1-5.859-5.857 5.865 5.865 0 0 1 5.859-5.859c1.63 0 3.204.7 4.319 1.919.085.093.24.432.209.797a1.086 1.086 0 0 1-.436.779c-.248.193-.516.29-.797.29-.402 0-.7-.198-.814-.314A3.473 3.473 0 0 0 12 8.575a3.464 3.464 0 0 0-3.46 3.461 3.464 3.464 0 0 0 3.46 3.46 3.63 3.63 0 0 0 2.654-1.181c.136-.152.458-.306.806-.306.274 0 .542.095.773.274.35.269.45.588.473.809.032.308-.072.585-.188.723m4.686-7.699C20.67 6.883 19.96 5.82 19.07 4.929c-.891-.89-1.954-1.601-3.188-2.133A9.728 9.728 0 0 0 12 2a9.733 9.733 0 0 0-3.883.796c-1.234.532-2.297 1.243-3.186 2.133-.891.891-1.602 1.954-2.134 3.187A9.713 9.713 0 0 0 2 12a9.752 9.752 0 0 0 .797 3.883c.531 1.233 1.242 2.296 2.134 3.186.89.891 1.953 1.602 3.186 2.134A9.725 9.725 0 0 0 12 22a9.72 9.72 0 0 0 3.883-.797c1.233-.532 2.296-1.243 3.188-2.134.89-.89 1.601-1.953 2.132-3.186A9.73 9.73 0 0 0 22 12a9.69 9.69 0 0 0-.797-3.884"
														fill-rule="evenodd"
													></path>
												</svg>
												<span class="GlobalSideBar-navText">版权服务中心</span>
											</a>
										</li>
									</ul>
								</div>
							</div>
						</div>
						<audio controls="controls">
							<source src="../../music.mp3" type="audio/ogg" autoplay="autoplay" />
						</audio>
						</div>
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
			articles: [],
			users: [],
			topics: []
		};
	},
	created() {
		this.axios.get(this.GLOBAL.baseUrl + '/article').then(res => {
			// console.log(res.data.data);
			this.articles = res.data.data;
			for (var i = 0; i < this.articles.length; i++) {
				this.articles[i].thumbnail = this.getImage(this.articles[i].thumbnail);
			}
		});
		this.axios.get(this.GLOBAL.baseUrl + '/user').then(res => {
			console.log(res.data.data);
			this.users = res.data.data;
		});
		this.axios.get(this.GLOBAL.baseUrl + '/topic').then(res => {
			console.log(res.data.data);
			this.topics = res.data.data;
		});
	},
	methods: {
		getImage(url) {
			return 'https://images.weserv.nl/?url=' + url;
		}
	}
};
</script>

<style scoped="scoped">
@font-face {
	font-family: 'iconfont'; /* project id 1434148 */
	src: url('//at.alicdn.com/t/font_1434148_ipcx04sb44o.eot');
	src: url('//at.alicdn.com/t/font_1434148_ipcx04sb44o.eot?#iefix') format('embedded-opentype'), url('//at.alicdn.com/t/font_1434148_ipcx04sb44o.woff2') format('woff2'),
		url('//at.alicdn.com/t/font_1434148_ipcx04sb44o.woff') format('woff'), url('//at.alicdn.com/t/font_1434148_ipcx04sb44o.ttf') format('truetype'),
		url('//at.alicdn.com/t/font_1434148_ipcx04sb44o.svg#iconfont') format('svg');
}
.iconfont {
	font-family: 'iconfont' !important;
	font-size: 17px;
	font-style: normal;
	-webkit-font-smoothing: antialiased;
	-webkit-text-stroke-width: 0.4px;
	-moz-osx-font-smoothing: grayscale;
} 
.back img {
	width: 100%;
	height: 800px;
	background-size: 100%;
}
.logo:hover {
	opacity: 0.6;
}
audio {
	background-color: rgb(245, 245, 240);
}
.time {
	margin-left: 50px;
	font-size: 13px;
}

.box {
	display: flex;
	justify-content: space-around;
	height: 120px;
	padding: 10px;
}
.btn-follow {
	background-color: #42c02e;
	font-weight: 400;
	font-size: 15px;
	color: #fff;
	padding: 5px 0;
	width: 80px;
	height: 30px;
	border-radius: 40px;
	display: inline-block;
	text-align: center;
}

.GlobalWrite-card {
	overflow: visible;
}
.GlobalSideBar {
	-webkit-box-flex: 1;
	-ms-flex: 1 1;
	flex: 1 1;
	font-size: 14px;
}

.GlobalWrite-nav {
	-webkit-box-pack: center;
	-ms-flex-pack: center;
	justify-content: center;
}
.GlobalWrite-nav,
.GlobalWrite-navItem {
	display: -webkit-box;
	display: -ms-flexbox;
	display: flex;
}
.Card {
	margin-bottom: 10px;
	overflow: hidden;
	border-radius: 2px;
	-webkit-box-shadow: 0 1px 3px rgba(26, 26, 26, 0.1);
	box-shadow: 0 1px 3px rgba(26, 26, 26, 0.1);
	-webkit-box-sizing: border-box;
	box-sizing: border-box;
}
a {
	color: inherit;
	text-decoration: none;
}

a:-webkit-any-link {
	color: -webkit-link;
	cursor: pointer;
	text-decoration: underline;
}
.GlobalWriteAnswerLater .GlobalWriteAnswerLater-icon {
	margin-left: -4px;
}
.GlobalWrite-navTitle {
	color: #444;
	font-size: 16px;
}
a {
	color: inherit;
	text-decoration: none;
}
.GlobalWriteAnswerLater-text {
	-webkit-box-align: center;
	-ms-flex-align: center;
	align-items: center;
	display: -webkit-box;
	display: -ms-flexbox;
	display: flex;
	margin-right: auto;
}
.CreatorEntrance-Link--smallIcon .CreatorEntrancePage-hint--smallIcon {
	height: 52px;
	width: 100%;
	padding: 0;
	margin: 0 16px;
}
.GlobalWrite-navItem {
	-webkit-box-align: center;
	-ms-flex-align: center;
	align-items: center;
	cursor: pointer;
	-webkit-box-orient: vertical;
	-webkit-box-direction: normal;
	-ms-flex-direction: column;
	flex-direction: column;
	margin: 23px;
	position: relative;
}
.GlobalWrite-navIcon {
	color: #8590a6;
	margin-bottom: 6px;
}
.CreatorEntrance-creator {
	width: 18px;
	height: 18px;
	margin-left: 3px;
	color: #8590a6;
}
.ProfileSideCreator-creatorEntranceHint {
	padding: 0 20px 0 4px;
}
.GlobalWrite-navItem {
	-webkit-box-align: center;
	-ms-flex-align: center;
	align-items: center;
	cursor: pointer;
	-webkit-box-orient: vertical;
	-webkit-box-direction: normal;
	-ms-flex-direction: column;
	flex-direction: column;
	margin: 23px;
	position: relative;
}
.GlobalWrite-navIcon {
	color: #8590a6;
	margin-bottom: 6px;
}
.GlobalWriteAnswerLater {
	-webkit-box-align: center;
	-ms-flex-align: center;
	align-items: center;
	color: #8590a6;
	display: -webkit-box;
	display: -ms-flexbox;
	display: flex;
	height: 48px;
	margin: 0 20px;
	position: relative;
}
.GlobalWrite-navTitle {
	color: #444;
	font-size: 16px;
}
.GlobalWriteAnswerLater .GlobalSideBar-navLink {
	margin: 0 -20px;
	width: 100%;
}

.GlobalSideBar-navLink:hover {
	background: #f6f6f6;
}
.GlobalWrite-draft {
	-webkit-box-align: center;
	-ms-flex-align: center;
	align-items: center;
	border-top: 1px solid #f0f2f7;
	color: #8590a6;
	display: -webkit-box;
	display: -ms-flexbox;
	display: flex;
	height: 48px;
	margin: 0 20px;
}
.GlobalWrite-draft .GlobalSideBar-navLink {
	margin: 0 -20px;
	width: 100%;
}
CreatorEntrance-Link--smallIcon {
	padding: 0 17px;
	-webkit-box-sizing: border-box;
	box-sizing: border-box;
}
.GlobalSideBar-categoryList {
	display: -webkit-box;
	display: -ms-flexbox;
	display: flex;
	-ms-flex-wrap: wrap;
	flex-wrap: wrap;
	margin: 20px 0 -5px;
	padding: 0 10px;
}
.GlobalSideBar-categoryItem {
	width: 33%;
	display: -webkit-box;
	display: -ms-flexbox;
	display: flex;
	margin-bottom: 25px;
}
.GlobalSideBar-navList {
	width: 100%;
	padding: 8px 0;
}
li {
	list-style-type: none;
}
li {
	display: list-item;
	text-align: -webkit-match-parent;
}
.GlobalSideBar-navLink {
	display: -webkit-box;
	display: -ms-flexbox;
	display: flex;
	-webkit-box-align: center;
	-ms-flex-align: center;
	align-items: center;
	padding: 0 20px;
	height: 40px;
	overflow: hidden;
}
</style>
