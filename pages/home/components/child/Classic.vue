<template>
	<view class="all-watch">
		<view class="watch-title">
			<text>{{title}}</text>
			<text class="iconfont icon-down" v-if="arrow_show"></text>
		</view>
		<view class="scroll-box">
			<view class="scroll-item" v-for="(item,index) in tvList" :key="index">
				<view class="img-content">
					<image :src="item.img"></image>
					<view class="sea-coll">
						<text>{{item.season}}</text>
						<text class="iconfont icon-Collect"></text>
					</view>
				</view>
				<text class="content-title">{{item.title}}</text>
				<view class="content-bottom">
					<text>{{item.point}}</text>
					<text>{{item.content}}</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: 'Classic',
		props: {
			tvList: Array,
			title: String,
			arrow_show: {
				type: Boolean,
				default: true
			}
		},
	}
</script>

<style lang="scss" scoped>
	.all-watch {
		width: 100vw;

		.watch-title {
			padding: 20rpx 40rpx;
			display: flex;
			justify-content: space-between;

			text:nth-child(1) {
				font-size: 36rpx;
				font-weight: 700;
			}
		}

		.scroll-box {
			width: 100%;
			display: flex;
			flex-wrap: wrap;
			padding: 0 30rpx;

			.scroll-item:last-child {
				padding-right: 40rpx;
			}

			.scroll-item {
				display: flex;
				flex-direction: column;
				padding: 0 10rpx 25rpx 10rpx;
				width: 210rpx;

				.img-content {
					width: 210rpx;
					height: 296rpx;
					position: relative;
					line-height: 0;
					border-radius: 10rpx;
					overflow: hidden;

					image {
						width: 100%;
						height: 100%;
					}

					.sea-coll {
						line-height: 60rpx;
						position: absolute;
						left: 0;
						bottom: 0;
						color: #C8C7CC;
						width: 100%;
						display: flex;
						align-items: center;
						justify-content: space-around;
						background-color: rgba($color: #000000, $alpha: .6);

						text:nth-child(1) {
							font-size: 28rpx;
						}

						text:nth-child(2) {
							font-size: 34rpx;
							line-height: 30rpx;
							padding-left: 10rpx;
							border-left: 2rpx solid rgba($color: #fff, $alpha: .6);
						}
					}
				}

				.content-title {
					font-size: 32rpx;
					white-space: nowrap;
					overflow: hidden;
					text-overflow: ellipsis;
				}

				.content-bottom {
					display: flex;
					line-height: 30rpx;

					text:nth-child(1) {
						color: #007AFF;
					}

					text:nth-child(2) {
						white-space: nowrap;
						overflow: hidden;
						text-overflow: ellipsis;
					}

					text {
						font-size: 24rpx;
					}
				}
			}
		}
	}
</style>
