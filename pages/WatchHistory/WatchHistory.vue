<template>
	<view class="watch-history">
		<!-- 抬头悬浮标题 -->
		<view class="active">
			<navigator open-type="navigateBack" hover-class="none">
				<text class="iconfont icon-arrow-l" style="font-size: 48rpx; color: #808080;"></text>
			</navigator>
			<view class="top-title" :style="{'opacity': titleCol}">每日排行榜</view>
		</view>
		<view class="his-title">观看历史</view>
		<view class="his-condition">
			<text @tap="handleShowCheck" v-show="!is_show">管理</text>
			<text @tap="handleShowCheck" v-show="is_show">完成</text>
			<!-- <text>隐藏短视频</text> -->
		</view>
		<scroll-view class="scroll" scroll-y="true">
			<view class="scroll-box">
				<view class="scroll-item" v-for="(item,index) in his_list" :key="index">
					<view class="item-id">
						<label class="radio" v-show="is_show" @tap="handleCheck(index)">
							<radio value="" :checked="item.is_checked"/>
						</label>
						<!-- <view v-show="is_show" class="check-box" @tap="handleCheck(index)">
							<view :class="{'act': item.is_checked}" class="check-item iconfont icon-Collect">
							</view>
						</view> -->
					</view>
					<view class="item-right">
						<view class="img-content">
							<image :src="item.img" mode="widthFix"></image>
						</view>
						<view class="right-content">
							<view class="content-top">
								<text>{{item.title}}</text>
								<text>{{item.season}}</text>
								<text>第{{item.watched}}集</text>
							</view>
							<text class="content-bottom">已观看{{item.percentage}}</text>
						</view>
					</view>
				</view>
			</view>
		</scroll-view>
		<view class="bottom-fixed" v-if="is_show">
			<view class="bottom-left">
				<!-- <view class="check-box" @tap="handleAllCheck">
					<view :class="{'act': is_checked}" class="check-item iconfont icon-Collect">
					</view>
				</view> -->
				<label class="radio" @tap="handleAllCheck">
					<radio value="" :checked="is_checked"/>
				</label>
				<text>全选</text>
			</view>
			<view @tap="handleDele">删除<text v-show="checked_num>0">({{checked_num}})</text></view>
		</view>
	</view>
</template>

<script>
	export default {
		name: 'WatchHistory',
		data() {
			return {
				titleCol: '0.0',
				is_show: false,
				is_checked: false,
				checked_num: 0,
				his_list: [{
						img: 'https://images.cnblogsc.com/pic/upload/vod/2020-08/1596450723.jpg',
						set_num: '8',
						is_end: false,
						title: '妖怪合租屋',
						is_checked: false,
						season: '第一季',
						watched: '1',
						percentage: '75%'
					},
					{
						img: 'https://images.cnblogsc.com/pic/upload/vod/2019-05/15592881935.jpg',
						set_num: '20',
						is_end: true,
						title: '吻我',
						is_checked: false,
						season: '第一季',
						watched: '1',
						percentage: '15%'
					},
					{
						img: 'https://images.cnblogsc.com/pic/upload/vod/2020-08/1596450723.jpg',
						set_num: '8',
						is_end: false,
						title: '妖怪合租屋',
						is_checked: false,
						season: '第一季',
						watched: '1',
						percentage: '75%'
					},
					{
						img: 'https://images.cnblogsc.com/pic/upload/vod/2019-05/15592881935.jpg',
						set_num: '20',
						is_end: true,
						title: '吻我',
						is_checked: false,
						season: '第一季',
						watched: '1',
						percentage: '15%'
					},
					{
						img: 'https://images.cnblogsc.com/pic/upload/vod/2020-08/1596450723.jpg',
						set_num: '8',
						is_end: false,
						title: '妖怪合租屋',
						is_checked: false,
						season: '第一季',
						watched: '1',
						percentage: '75%'
					},
					{
						img: 'https://images.cnblogsc.com/pic/upload/vod/2019-05/15592881935.jpg',
						set_num: '20',
						is_end: true,
						title: '吻我',
						is_checked: false,
						season: '第一季',
						watched: '1',
						percentage: '15%'
					},
					{
						img: 'https://images.cnblogsc.com/pic/upload/vod/2020-08/1596450723.jpg',
						set_num: '8',
						is_end: false,
						title: '妖怪合租屋',
						is_checked: false,
						season: '第一季',
						watched: '1',
						percentage: '75%'
					},
					{
						img: 'https://images.cnblogsc.com/pic/upload/vod/2019-05/15592881935.jpg',
						set_num: '20',
						is_end: true,
						title: '吻我',
						is_checked: false,
						season: '第一季',
						watched: '1',
						percentage: '15%'
					},
					{
						img: 'https://images.cnblogsc.com/pic/upload/vod/2020-08/1596450723.jpg',
						set_num: '8',
						is_end: false,
						title: '妖怪合租屋',
						is_checked: false,
						season: '第一季',
						watched: '1',
						percentage: '75%'
					},
					{
						img: 'https://images.cnblogsc.com/pic/upload/vod/2019-05/15592881935.jpg',
						set_num: '20',
						is_end: true,
						title: '吻我',
						is_checked: false,
						season: '第一季',
						watched: '1',
						percentage: '15%'
					},
					{
						img: 'https://images.cnblogsc.com/pic/upload/vod/2020-08/1596450723.jpg',
						set_num: '8',
						is_end: false,
						title: '妖怪合租屋',
						is_checked: false,
						season: '第一季',
						watched: '1',
						percentage: '75%'
					},
					{
						img: 'https://images.cnblogsc.com/pic/upload/vod/2019-05/15592881935.jpg',
						set_num: '20',
						is_end: true,
						title: '吻我',
						is_checked: false,
						season: '第一季',
						watched: '1',
						percentage: '15%'
					},
					{
						img: 'https://images.cnblogsc.com/pic/upload/vod/2020-08/1596450723.jpg',
						set_num: '8',
						is_end: false,
						title: '妖怪合租屋',
						is_checked: false,
						season: '第一季',
						watched: '1',
						percentage: '75%'
					},
					{
						img: 'https://images.cnblogsc.com/pic/upload/vod/2019-05/15592881935.jpg',
						set_num: '20',
						is_end: true,
						title: '吻我',
						is_checked: false,
						season: '第一季',
						watched: '1',
						percentage: '15%'
					},
				]
			}
		},
		onPageScroll(e) {
			if (e.scrollTop >= 20) {
				this.titleCol = '1.0'
			} else if (e.scrollTop < 20) {
				this.titleCol = '0.0'
			}
		},
		methods: {
			// 显示管理
			handleShowCheck() {
				this.is_show = !this.is_show
				this.is_checked = false
				this.checked_num = 0
				this.his_list.forEach(item => {
					item.is_checked = false
				})
			},
			// 单个选中
			handleCheck(index) {
				let num = 0
				let newarr = []
				this.his_list[index].is_checked = !this.his_list[index].is_checked
				this.his_list.forEach(item => {
					if (item.is_checked) {
						newarr.push(item)

						this.checked_num = newarr.length
						if (newarr.length == this.his_list.length) {
							this.is_checked = true
						} else {
							this.is_checked = false
						}
					} else {
						this.checked_num = newarr.length
					}
				})
			},
			// 全选
			handleAllCheck() {
				this.is_checked = !this.is_checked
				if (this.is_checked) {
					this.checked_num = this.his_list.length
				} else {
					this.checked_num = 0
				}
				this.his_list.forEach(item => {
					if (this.is_checked) {
						item.is_checked = true
					} else {
						item.is_checked = false
					}
				})
			},
			// 删除按钮
			handleDele() {
				if (this.is_checked) {
					this.his_list = []
				} else {
					this.his_list.forEach((item, index) => {
						if (item.is_checked) {
							this.his_list.splice(index, 1)
						}
					})
				}
				this.checked_num = 0
				this.is_show = !this.is_show
			}
		}
	}
</script>

<style lang="scss" scoped>
	.watch-history {
		.active {
			width: 100%;
			padding: 30rpx 0 30rpx 40rpx;
			position: fixed;
			left: 0;
			top: 0;
			z-index: 99;
			background-color: #F9F9F9;

			.top-title {
				position: fixed;
				top: 30rpx;
				left: 50%;
				transform: translateX(-50%);
				color: #808080;
				transition: opacity 2s;
			}
		}

		.his-title {
			font-size: 44rpx;
			font-weight: 700;
			margin-top: 70rpx;

			padding: 42rpx 40rpx 20rpx 40rpx;
			border-bottom: 1rpx solid #CCCCCC;
		}

		.his-condition {
			width: 100%;
			padding: 30rpx;
			z-index: 9;
			background-color: #F9F9F9;

			text {
				padding: 10rpx 20rpx;
				background-color: #F1F1F1;
				color: #666666;
				margin-right: 20rpx;
				border-radius: 40rpx;
			}
		}

		.scroll {
			width: 100%;
			height: calc(100vh - 220rpx);

			.scroll-box {
				padding-bottom: 94rpx;
				.scroll-item {
					width: 100%;
					display: flex;
					align-items: center;

					.item-id {
						padding-left: 40rpx;
					}

					.item-right {
						display: flex;
						// width: 600rpx;
						flex: 1;
						margin-left: 40rpx;
						padding: 30rpx 0;

						// border-bottom: 1rpx solid #C8C7CC;
						.img-content {
							width: 250rpx;
							height: 150rpx;
							overflow: hidden;
							border-radius: 10rpx;

							image {
								width: 100%;
							}
						}

						.right-content {
							display: flex;
							flex-direction: column;
							padding: 10rpx 0 0 20rpx;

							.content-top {
								font-size: 32rpx;

								text {
									margin-right: 10rpx;
								}
							}

							.content-bottom {
								color: #808080;
								font-size: 28rpx;
							}
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

		.bottom-fixed {
			position: fixed;
			left: 0;
			bottom: 0;
			width: 100%;
			box-sizing: border-box;
			display: flex;
			justify-content: space-between;
			padding: 20rpx 40rpx;
			background-color: #F9F9F9;
			border-top: 1rpx solid #CCCCCC;
			.bottom-left {
				display: flex;
				align-items: center;

				text {
					padding-left: 20rpx;
				}
			}
		}
	}

	.check-box {
		width: 50rpx;
		height: 50rpx;
		border: 1rpx solid #C0C0C0;
		border-radius: 50%;
		overflow: hidden;
		position: relative;

		.check-item {
			width: 60rpx;
			height: 60rpx;
			line-height: 60rpx;
			transform: translateX(-6rpx);
			text-align: center;
			opacity: 0.0;
		}

		.act {
			color: #fff;
			background-color: #007AFF;
			opacity: 1.0;
		}
	}
</style>
