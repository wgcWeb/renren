<template>
	<view class="simple-scroll">
		<view class="watch-title">
			<text>{{title}}</text>
		</view>
		<scroll-view class="scroll" scroll-x="true">
			<view class="scroll-box">
				<view class="scroll-item" v-for="(item,index) in tvList" :key="index">
					<view class="img-content">
						<image :src="item.img"></image>
					</view>
					<text class="content-title">{{item.title}}</text>
					<view class="content-bottom">
						<text>{{item.content}}</text>
					</view>
				</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		name: 'SimpleScroll',
		props: {
			tvList: Array,
			title: String,
		},
		methods:{
		}
	}
</script>

<style lang="scss" scoped>
	.simple-scroll {
		width: 100vw;
		.watch-title {
			padding: 20rpx 40rpx;
			text{
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
					width: 200rpx;
					.img-content {
						width: 200rpx;
						height: 296rpx;
						line-height: 0;
						border-radius: 10rpx;
						overflow: hidden;
						image {
							width: 100%;
							height: 100%;
						}
					}
					.content-title{
						font-size: 32rpx;
						white-space:nowrap;
						overflow:hidden;
						text-overflow:ellipsis;
					}
					.content-bottom {
						line-height: 30rpx;
						text{
							font-size: 24rpx;
							color: #808080;
							white-space:nowrap;
							overflow:hidden;
							text-overflow:ellipsis;
						}
					}
				}
			}
		}
	}
</style>
