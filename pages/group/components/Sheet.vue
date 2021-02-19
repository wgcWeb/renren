<template>
	<view class="group-item">
		<navigator url="/pages/list/list" hover-class="none">
			<view class="item-top">
				<image :src="img" mode="widthFix"></image>
				<!-- <image class="item-bg" :src="img" mode="widthFix"/> -->
				<view class="item-title">
					<view class="title-left">
						<text>{{title}}</text>
						<text>《{{text[0]}}》《{{text[1]}}》《{{text[2]}}》</text>
					</view>
					<view class="title-right">
						共{{length}}部
					</view>
				</view>
			</view>
		</navigator>
		<scroll-view class="scroll" scroll-x="true">
			<view class="scroll-box">
				<view class="scroll-item" v-for="(item1,index1) in list" :key="index1">
					<view class="img-content">
						<image :src="item1.img" mode=""></image>
					</view>
					<view class="img-bottom">{{item1.title}}</view>
				</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default{
		name: 'Sheet',
		props:['title','list','length','img','text']
	}
</script>

<style lang="scss" scoped>
	.group-item {
		width: 100%;
		height: 100%;
		border-radius: 10rpx;
		overflow: hidden;
		margin-bottom: 40rpx;
					
		.item-top {
			position: relative;
			width: 100%;
			height: 140rpx;
			overflow: hidden;
					
			image {
				width: 100%;
				transform: translateY(-50rpx);
				filter: blur(5px);
			}
					
			.item-title {
				position: absolute;
				top: 0;
				left: 0;
				color: #fff;
				padding: 20rpx;
				width: 100%;
				box-sizing: border-box;
				display: flex;
				justify-content: space-between;
				align-items: center;
					
				.title-left {
					display: flex;
					flex-direction: column;
					justify-content: space-between;
					
					text:nth-child(1) {
						font-size: 36rpx;
						font-weight: 700;
						white-space: nowrap;
						overflow: hidden;
						text-overflow: ellipsis;
					}
					text:nth-child(2) {
						width: 500rpx;
						white-space: nowrap;
						overflow: hidden;
						text-overflow: ellipsis;
					}
				}
					
				.title-right {
					width: 130rpx;
					height: 60rpx;
					line-height: 60rpx;
					text-align: center;
					border-radius: 30rpx;
					background-color: rgba($color: #fff, $alpha: .3);
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
		.scroll {
			width: 100%;
			background-color: #fff;
					
			.scroll-box {
				display: flex;
				padding: 30rpx 30rpx 20rpx 30rpx;
					
				.scroll-item {
					width: 200rpx;
					display: flex;
					flex-direction: column;
					padding-right: 30rpx;
					
					.img-content {
						width: 200rpx;
						height: 296rpx;
						border-radius: 10rpx;
						overflow: hidden;
					
						image {
							width: 100%;
							height: 100%;
						}
					}
					
					.img-bottom {
						display: inline-block;
						width: 200rpx;
						line-height: 48rpx;
						padding: 5rpx 0;
						white-space: nowrap;
						overflow: hidden;
						text-overflow: ellipsis;
					}
				}
			}
		}
	}
</style>
