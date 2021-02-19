<template>
	<view class="schedule">
		<view class="active">
			<navigator open-type="navigateBack" hover-class="none">
				<text class="iconfont icon-arrow-l"></text>
			</navigator>
			<text class="iconfont icon-xia_zai" @tap="handleBottomShow"></text>
			<view class="top-title" :style="{'display':navbg.titleCol}">每日排行榜</view>
		</view>
		<view class="schedule-title">{{msg}}排期</view>
		<scroll-view class="scroll-view" scroll-x="true">
			<view class="nav-fixed">
				<text :class="{'act': currentIndex == index}" v-for="(item,index) in dateList" :key="index" @tap="handleChange(index)">{{item}}</text>
			</view>
		</scroll-view>
		<swiper @change="onSwiperChange" :current="currentIndex" class="tab-box" :duration="300">
			<swiper-item class="swiper-item" v-for="(item1,index1) in itemList" :key="index1">
				<scroll-view class="scroll" scroll-y="true">
					<view class="scroll-box">
						<!-- <view class="scroll-title">
							<text>综合</text>
							<text class="iconfont icon-xia_zai"></text>
						</view> -->
						<view class="scroll-item" v-for="(item2,index2) in item1.child" :key="index2">
							<image :src="item2.img" mode=""></image>
							<view class="right-content">
								<text>旺达幻视</text>
								<text>2021/美国/动作/科幻/悬疑/喜剧/爱情</text>
								<text>更新至4集</text>
							</view>
						</view>
					</view>
				</scroll-view>
			</swiper-item>
		</swiper>
		<btn-mask @changeTitle="changeTitle" ref="mask" :choose-list="chooseList"></btn-mask>
	</view>
</template>

<script>
	import BtnMask from '../../components/BtnMask.vue'
	import concentration from 'data/concentration.json'
	export default {
		name: 'schedule',
		components: {
			BtnMask
		},
		data() {
			return {
				navbg: {
					titleCol: 'none',
					conzindex: '-1'
				},
				navList: ['美剧', '韩剧', '日剧', '泰剧'],
				dateList: ['周一', '周二', '周三', '周四', '周五', '周六', '周日'],
				chooseList: ['1月', '2月', '3月'],
				msg: '2月',
				itemList: [],
				currentIndex: 0,
				tabIndex: 0,
				bottomShow: false,
				bottombg: '-9'
			}
		},
		onLoad() {
			this.itemList = concentration.dateList
			// this.itemList.push(concentration.listScroll[3],concentration.listScroll[4])
			// console.log(this.itemList)
		},
		onPageScroll(e) {
			console.log(e.scrollTop)
			if (e.scrollTop >= 40) {
				this.navbg.titleCol = 'inline-block'
			} else if (e.scrollTop < 40) {
				this.navbg.titleCol = 'none'
			}
		},
		methods: {
			// 切换分类标题
			handleChange(index) {
				this.currentIndex = index
			},
			onSwiperChange(e) {
				this.currentIndex = e.target.current || e.detail.current
			},
			changeTitle(item) {
				this.msg = item
			},
			handleBottomShow() {
				this.$refs.mask.handleBottom()
			},
		}
	}
</script>

<style lang="scss" scoped>
	.schedule {
		.active {
			width: 100%;
			padding: 30rpx 40rpx;
			position: fixed;
			left: 0;
			top: 0;
			z-index: 99;
			background-color: #fff;
			color: #808080;
			display: flex;
			justify-content: space-between;
			box-sizing: border-box;

			.top-title {
				position: fixed;
				top: 30rpx;
				left: 50%;
				transform: translateX(-50%);
				transition: color 2s;
			}
		}

		.schedule-title {
			margin-top: 108rpx;
			font-size: 46rpx;
			font-weight: 700;
			padding: 20rpx 0 30rpx 30rpx;
			background-color: #fff;
		}

		.scroll-view ::-webkit-scrollbar {
			width: 0 !important;
			display: none;
			height: 0 !important;
			-webkit-appearance: none;
			background: transparent;
		}

		.scroll-view {
			width: 100%;
			background-color: #fff;
			
			.nav-fixed {
				display: flex;
				white-space: nowrap;
				

				text {
					font-size: 28rpx;
					padding: 30rpx 40rpx;
				}

				.act {
					font-size: 34rpx;
					font-weight: 700;
				}
			}
		}

		.tab-box {
			width: 100%;
			height: calc(100vh - 216rpx);
			background-color: #fff;

			.swiper-item {
				.scroll {
					width: 100%;
					height: 100%;

					.scroll-box {
						background-color: #fff;

						// .scroll-title{
						// 	width: 100%;
						// 	display: flex;
						// 	justify-content: space-between;
						// 	box-sizing: border-box;
						// 	padding: 20rpx 40rpx 0 40rpx;
						// 	font-size: 36rpx;
						// }
						.scroll-item {
							width: 100%;
							display: flex;
							align-items: center;
							padding: 30rpx 40rpx;

							image {
								width: 150rpx;
								height: 200rpx;
								border-radius: 10rpx;
							}

							.right-content {
								display: flex;
								flex-direction: column;
								justify-content: space-around;
								height: 200rpx;
								padding: 10rpx 30rpx;

								text:nth-child(1) {
									font-size: 32rpx;
									font-weight: 700;
									white-space: nowrap;
									overflow: hidden;
									text-overflow: ellipsis;
								}

								text:nth-child(2) {
									font-size: 26rpx;
									color: #808080;
									white-space: nowrap;
									overflow: hidden;
									text-overflow: ellipsis;
								}

								text:nth-child(3) {
									font-size: 26rpx;
									color: #808080;
								}
							}
						}
					}
				}

				.scroll ::-webkit-scrollbar {
					width: 0 !important;
					display: none;
					height: 0 !important;
					-webkit-appearance: none;
					background: transparent;
				}
			}
		}

		// .bottom{
		// 	width: 100%;
		// 	height: 100vh;
		// 	position: fixed;
		// 	left: 0;
		// 	top: 0;
		// 	background-color: rgba($color: #000000, $alpha: .6);
		// 	z-index: 999;
		// 	.bottom-content{
		// 		width: 100%;
		// 		position: absolute;
		// 		left: 0;
		// 		bottom: 0;
		// 		background-color: #fff;
		// 		.bottom-list{
		// 			height: 500rpx;
		// 			display: flex;
		// 			flex-direction: column;
		// 			justify-content: space-evenly;
		// 			align-items: center;
		// 			border-bottom: 1rpx solid #C8C7CC;
		// 			text{
		// 				font-size: 32rpx;
		// 			}
		// 			.choose{
		// 				color: #007AFF;
		// 			}
		// 		}
		// 		.bottom-btn{
		// 			text-align: center;
		// 			padding: 30rpx 0;
		// 			color: #808080;
		// 		}
		// 	}
		// }
	}
</style>
