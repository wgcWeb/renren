<template>
	<view class="all-watch">
		<view class="watch-title">
			<text>{{title}}</text>
			<text class="iconfont icon-down" v-if="arrow_show"></text>
		</view>
		<scroll-view class="scroll" scroll-x="true">
			<view class="scroll-box">
				<view class="scroll-item" v-for="(item,index) in tvList" :key="index">
					<view class="img-content">
						<image :src="item.img" ></image>
						<view class="sea-coll">
							<view class="content-title">
								<text>{{item.title}}</text>
								<text class="iconfont icon-Collect"></text>
							</view>
							<view>{{item.season}}</view>
							<view class="content-middle">
								<text>{{item.point}}</text>
								<text>{{item.cate}}</text>
							</view>
							<text class="content-bottom">{{item.content}}</text>
						</view>
					</view>
				</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		name: 'TitleGroup',
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
		.scroll ::-webkit-scrollbar{
			width: 0 !important;
			display: none;
			height: 0 !important;
			-webkit-appearance: none;
			background: transparent;
		}
		.scroll {
			width: 100%;
			.scroll-box {
				display: flex;
				padding: 0 30rpx;

				.scroll-item:last-child {
					padding-right: 40rpx;
				}

				.scroll-item {
					display: flex;
					flex-direction: column;
					padding: 0 10rpx;

					.img-content {
						display: flex;
						width: 600rpx;
						height: 296rpx;
						border-radius: 10rpx;
						overflow: hidden;
						image {
							width: 200rpx;
							height: 100%;
							border-radius: 10rpx;
						}

						.sea-coll {
							width: 400rpx;
							height: 100%;
							display: flex;
							flex-direction: column;
							justify-content: space-around;
							padding: 30rpx;
							box-sizing: border-box;
							background-color: #fff;
							color: #808080;
							text{
								display: inline-block;
							}
							.content-title{
								display: flex;
								justify-content: space-between;
								align-items: center;
								text:nth-child(1){
									font-size: 36rpx;
									font-weight: 700;
									color: #000;
									white-space:nowrap;
									overflow:hidden;
									text-overflow:ellipsis;
								}
								text:nth-child(2){
									font-size: 34rpx;
								}
								
							}
							.content-middle{
								display: flex;
								text:nth-child(1){
									color: #007AFF;
									margin-right: 10rpx;
								}
								text:nth-child(2){
									white-space:nowrap;
									overflow:hidden;
									text-overflow:ellipsis;
								}
							}
							.content-bottom{
								white-space:nowrap;
								overflow:hidden;
								text-overflow:ellipsis;
							}
						}
					}
				}
			}
		}
	}
</style>
