<template>
	<view class="tv-detail">
		<text class="back-to iconfont icon-arrow-l" @tap.stop="back"></text>
		<video id="myVideo" src="https://img.cdn.aliyun.dcloud.net.cn/guide/uniapp/%E7%AC%AC1%E8%AE%B2%EF%BC%88uni-app%E4%BA%A7%E5%93%81%E4%BB%8B%E7%BB%8D%EF%BC%89-%20DCloud%E5%AE%98%E6%96%B9%E8%A7%86%E9%A2%91%E6%95%99%E7%A8%8B@20200317.mp4"
		 @error="videoErrorCallback" :danmu-list="danmuList" :enable-danmu="true" :danmu-btn="true" controls></video>
		<view class="danmu-box" :style="{top: top}">
			<input :class="{'active': danmu_show}" v-model="danmuValue" class="danmu-input" type="text" placeholder="点我发弹幕" />
			<text @tap="sendDanmu" class="danmu-btn iconfont icon-tv"></text>
		</view>
		<!-- 滑动标签栏 -->
		<scroll-swiper class="scroll-swiper" :style="{top: setTop}" :nav-list="navList" :height="height">
			<view class="scroll-box-detail" slot="详情">
				<view class="detail-top">
					<view class="detail-title">
						<text>写不出来</text>
						<text class="iconfont icon-down"></text>
					</view>
					<view class="detail-text">
						<text>8.8</text>
						<text>VIP</text>
						<text>2021/日本/喜剧</text>
					</view>
					<view class="detail-icon">
						<view class="icon-left">
							<text class="iconfont icon-Collect"></text>
							<text>人人视频日剧</text>
						</view>
						<view class="icon-right">
							<text class="iconfont icon-tv"></text>
							<text class="iconfont icon-Collect"></text>
							<text class="iconfont icon-xia_zai"></text>
							<text class="iconfont icon-Collect"></text>
						</view>
					</view>
				</view>
				<view class="detail-content">
					<anthology :current="currentIndex" :tv-list="tvList" @chooseShow="chooseShow" @chooseIndex="chooseIndex"></anthology>
					<tv-scroll title="为你推荐" :tv-list="tvList" :arrow_show="false"></tv-scroll>
				</view>
			</view>
			<view class="scroll-box-comment" slot="讨论">
				<view class="comment">
					<image src="https://i1.hdslb.com/bfs/face/3f84f9f0e34153971f6ebd62790eaf5b4490d3d5.png@162w_162h.webp" />
					<view class="comment-item">
						<view class="username-box">
							<text>人人君的托</text>
							<text class="iconfont icon-Collect"></text>
						</view>
						<text class="date">01-13</text>
						<view class="comment-content">同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步</view>
						<view class="comment-bottom">
							<view class="bottom-reply">
								<text>renren_155555555</text>
								<text>: 最近那个"事情"</text>
							</view>
							<view class="reply-num" @tap="handleShowReply">查看全部23条回复</view>
						</view>
						<view class="good_num">
							<text class="iconfont icon-down"></text>
							<text>1777</text>
							<text class="iconfont icon-Collect"></text>
						</view>
					</view>
				</view>
			</view>
		</scroll-swiper>
		<!-- 回复详情 -->
		<view class="reply" v-show="reply_show" @scroll.stop.prevent="moveHandle">
			<view class="reply-box" :style="{'height': height}">
				<view class="box-top">
					<view class="top-title">详情</view>
					<view class="top-icon">
						<text class="iconfont icon-Collect"></text>
						<text class="iconfont icon-Collect" @tap="handleExitReply"></text>
					</view>
				</view>
				<scroll-view class="scroll" scroll-y="true" >
					<view class="scroll-box">
						<view class="scroll-top">
							<view class="img-content">
								<image src="https://i1.hdslb.com/bfs/face/3f84f9f0e34153971f6ebd62790eaf5b4490d3d5.png@162w_162h.webp" mode=""></image>
								<view class="content-userInfo">
									<text>人人君的托</text>
									<text>01-21</text>
								</view>
							</view>
							<view class="scroll-content">
								同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步
							</view>
						</view>
						<view class="scroll-bottom">
							<view class="">23条回复</view>
							<view class="reply-item">
								<image src="https://i1.hdslb.com/bfs/face/3f84f9f0e34153971f6ebd62790eaf5b4490d3d5.png@162w_162h.webp" />
								<view class="comment-item">
									<text class="username-box">人人君的托</text>
									<text class="date">01-13</text>
									<view class="comment-content">同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步同步</view>
									<view class="good_num">
										<text class="iconfont icon-down"></text>
										<text>1777</text>
										<text class="iconfont icon-Collect"></text>
									</view>
								</view>
							</view>
						</view>
					</view>
				</scroll-view>
				<input class="reply-input" type="text">
			</view>
		</view>
		<!-- 剧集集数列表显示 -->
		<view class="choose-list" v-show="choose_show" @scroll.stop.prevent="moveHandle">

			<view class="list-bottom" :style="{'height': height}">
				<view class="list-title">
					<text>选集</text>
					<text class="iconfont icon-xia_zai" @tap="handleExit"></text>
				</view>
				<view class="list-content">
					<view class="list-item" :class="{'active': currentIndex == index}" v-for="(item,index) in tvList" :key="index"
					 @tap="handleChoose(index)">
						{{index}}
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import ScrollSwiper from '../../components/ScrollSwiper.vue'
	import TvScroll from '../home/components/child/TvScroll.vue'
	import Anthology from './components/Anthology.vue'
	import concentration from 'data/concentration.json'
	export default {
		name: 'TvDetail',
		components: {
			ScrollSwiper,
			TvScroll,
			Anthology
		},
		data() {
			return {
				navList: ['详情', '讨论'],
				tvList: [],
				height: '',
				danmuList: [{
						text: '第 1s 出现的弹幕',
						color: '#ff0000',
						time: 1
					},
					{
						text: '第 3s 出现的弹幕',
						color: '#ff00ff',
						time: 3
					}
				],
				danmuValue: '',
				danmu_show: false,
				currentIndex: 0,
				// 显示集数列表
				choose_show: false,
				// 显示评论列表
				reply_show: false,
				// 视频下模块的高度
				setTop: '',
				// 发送弹幕模块的固定高度
				top: ''
			}
		},
		onLoad() {
			this.tvList = concentration.douyinWatch
		},
		onReady() {
			let div = document.getElementById('myVideo');
			this.height = `calc(100vh - ${div.offsetHeight}px)`
			this.setTop = div.offsetHeight + 'px'
			this.top = (div.offsetHeight + 9) + 'px'
			this.videoContext = uni.createVideoContext('myVideo')
		},
		methods: {
			back() {
				uni.navigateBack()
			},
			sendDanmu() {
				this.videoContext.sendDanmu({
					text: this.danmuValue,
					color: this.getRandomColor()
				});
				this.danmuValue = '';
				this.danmu_show = !this.danmu_show
			},
			videoErrorCallback(e) {
				uni.showModal({
					content: e.target.errMsg,
					showCancel: false
				})
			},
			getRandomColor() {
				const rgb = []
				for (let i = 0; i < 3; ++i) {
					let color = Math.floor(Math.random() * 256).toString(16)
					color = color.length == 1 ? '0' + color : color
					rgb.push(color)
				}
				return '#' + rgb.join('')
			},
			chooseShow(choose_show) {
				this.choose_show = choose_show
			},
			chooseIndex(current) {
				this.currentIndex = current
			},
			handleChoose(index) {
				this.currentIndex = index
			},
			handleExit() {
				this.choose_show = false
			},
			moveHandle() {
			},
			handleShowReply(){
				this.reply_show = true
			},
			handleExitReply(){
				this.reply_show = false
			}
		}
	}
</script>

<style lang="scss" scoped>
	.tv-detail {
		width: 100vw;

		.back-to {
			position: fixed;
			top: 30rpx;
			left: 10rpx;
			z-index: 99;
			color: #C0C0C0;
			font-size: 56rpx;
		}

		#myVideo {
			width: 100%;
			margin-bottom: 0;
		}

		.danmu-box {
			height: 50rpx;
			display: flex;
			align-items: center;
			border-radius: 40rpx;
			background-color: #F1F1F1;
			border: 1rpx solid #CCCCCC;
			overflow: hidden;
			position: fixed;
			// top: 480rpx;
			right: 20rpx;
			z-index: 999;

			.danmu-input {
				font-size: 26rpx;
				width: 170rpx;
				height: 100%;
				color: #808080;
				padding-left: 20rpx;
				transition: width 1s;
			}

			.active {
				width: 0;
				padding: 0;
				opacity: 0;
			}

			.danmu-btn {
				width: 70rpx;
				height: 100%;
				display: flex;
				justify-content: center;
				align-items: center;
				// transform: translateY(20rpx);
				font-size: 36rpx;
				text-align: center;
				background-color: #fff;
			}
		}

		.scroll-swiper {
			width: 100%;
			position: fixed;
			// top: 450rpx;
			left: 0;

			.scroll-box-detail {
				.detail-top {
					padding: 30rpx 40rpx;
					border-bottom: 1rpx solid #CCCCCC;

					.detail-title {
						display: flex;
						justify-content: space-between;
						align-items: center;

						text:nth-child(1) {
							font-size: 36rpx;
							font-weight: 700;
							white-space: nowrap;
							overflow: hidden;
							text-overflow: ellipsis;
						}

						text:nth-child(2) {
							font-size: 36rpx;
						}
					}

					.detail-text {
						font-size: 24rpx;
						color: #8F8F94;
						padding: 5rpx 0;

						text:nth-child(1) {
							color: #007AFF;
						}

						text:nth-child(2) {
							padding: 0 20rpx;
							margin: 0 20rpx;
							border-left: 1rpx solid #C0C0C0;
							border-right: 1rpx solid #C0C0C0;
							color: #F0AD4E;
						}

					}

					.detail-icon {
						display: flex;
						align-items: center;
						justify-content: space-between;
						color: #8F8F94;

						.icon-left {
							display: flex;
							align-items: center;
							font-size: 24rpx;

							text:nth-child(1) {
								padding-right: 10rpx;
							}
						}

						.icon-right {
							text {
								font-size: 42rpx;
								margin-left: 25rpx;
							}
						}
					}
				}
			}

			.scroll-box-comment {
				padding: 0 40rpx;

				.comment {
					display: flex;
					border-bottom: 1rpx solid #CCCCCC;
					padding-top: 20rpx;
					image {
						width: 100rpx;
						height: 100rpx;
						border-radius: 50%;
					}

					.comment-item {
						flex: 1;
						display: flex;
						flex-direction: column;
						justify-content: center;

						.username-box {
							display: flex;
							justify-content: space-between;
							align-items: center;

							text {
								font-size: 24rpx;
							}
						}

						.date {
							font-size: 24rpx;
							color: #808080;
						}

						.comment-content {
							font-size: 28rpx;
							padding: 20rpx 0;
						}
						.comment-bottom{
							background-color: #F1F1F1;
							border-radius: 20rpx;
							padding: 15rpx 20rpx;
							height: 100rpx;
							display: flex;
							flex-direction: column;
							justify-content: space-between;
							.bottom-reply{
								display: flex;
								align-items: center;
								text{
									font-size: 28rpx;
								}
								text:nth-child(1){
									display: inline-block;
									width: 150rpx;
									color: #007AFF;
									white-space: nowrap;
									overflow: hidden;
									text-overflow: ellipsis;
								}
							}
							.reply-num{
								font-size: 28rpx;
								color: #808080;
							}
						}
						.good_num{
							display: flex;
							align-self:flex-end;
							padding: 20rpx 0;
							text{
								font-size: 26rpx;
								color: #808080;
							}
							text:nth-child(3){
								padding-left: 40rpx;
							}
						}
					}
				}
			}
		}
		.reply{
			width: 100vw;
			height: 100vh;
			position: fixed;
			top: 0;
			left: 0;
			z-index: 999999;
			.reply-box{
				width: 100%;
				position: absolute;
				bottom: 0;
				left: 0;
				background-color: #fff;
				display: flex;
				flex-direction: column;
				.box-top{
					display: flex;
					justify-content: space-between;
					align-items: center;
					flex-shrink: 0;
					height: 120rpx;
					padding: 0 40rpx;
					.top-title{
						font-size: 34rpx;
						font-weight: 700;
					}
					.top-icon{
						text{
							font-size: 34rpx;
							color: #808080;
						}
						text:nth-child(1){
							padding-right: 30rpx;
						}
					}
				}
				.scroll ::-webkit-scrollbar{
					width: 0 !important;
					display: none;
					height: 0 !important;
					-webkit-appearance: none;
					background: transparent;
				}
				.scroll{
					// flex: 1;
					height: calc(100% - 220rpx);
					width: 100%;
					.scroll-box{
						padding: 0 40rpx;
						.scroll-top{
							padding-bottom: 40rpx;
							.img-content{
								display: flex;
								align-items: center;
								image{
									width: 100rpx;
									height: 100rpx;
								}
								.content-userInfo{
									display: flex;
									flex-direction: column;
									justify-content: center;
									text{
										font-size: 24rpx;
									}
									text:nth-child(2){
										color: #808080;
									}
								}
							}
							.scroll-content{
								font-size: 28rpx;
								padding: 20rpx 0;
							}
						}
						.scroll-bottom{
							.reply-item{
								display: flex;
								border-bottom: 1rpx solid #CCCCCC;
								padding-top: 20rpx;
								image {
									width: 100rpx;
									height: 100rpx;
									border-radius: 50%;
								}
								
								.comment-item {
									flex: 1;
									display: flex;
									flex-direction: column;
									justify-content: center;
								
									.username-box {
										font-size: 24rpx;
									}
								
									.date {
										font-size: 24rpx;
										color: #808080;
									}
								
									.comment-content {
										font-size: 28rpx;
										padding: 20rpx 0;
									}
									.good_num{
										display: flex;
										align-self:flex-end;
										padding: 20rpx 0;
										text{
											font-size: 26rpx;
											color: #808080;
										}
										text:nth-child(3){
											padding-left: 40rpx;
										}
									}
								}
							}
						}
					}
				}
				.reply-input{
					width: 100%;
					height: 100rpx;
				}
			}
		}
		.choose-list {
			width: 100vw;
			height: 100vh;
			position: fixed;
			top: 0;
			left: 0;
			z-index: 999999;

			.list-bottom {
				width: 100%;
				position: absolute;
				bottom: 0;
				left: 0;
				background-color: #fff;

				.list-title {
					display: flex;
					align-items: center;
					justify-content: space-between;
					padding: 30rpx 40rpx;

					text:nth-child(1) {
						font-size: 34rpx;
						font-weight: 700;
					}
				}

				.list-content {
					.list-item {
						margin: 0 10rpx;
						display: inline-block;
						width: 100rpx;
						height: 100rpx;
						flex-shrink: 0;
						line-height: 100rpx;
						text-align: center;
						box-shadow: 5px 5px 10px rgba(0, 0, 0, .1);
					}

					.active {
						color: #007AFF
					}
				}
			}
		}
	}
</style>
