<template>
	<view class="my">
		<view class="sign-box">
			<!-- <view class="sign-title">
				<text>登陆 / 注册</text>
				<text>快来开启视频之旅</text>
			</view> -->
			<view class="sign-title">
				<text>快乐的风</text>
				<text>此处应有个性签名</text>
				<view class="sign-btn-box">
					<view class="sign-btn">
						<text class="iconfont icon-Collect"></text>
						<text>签到</text>
					</view>
					<view class="sign-btn">
						<text class="iconfont icon-Collect"></text>
						<text>消息</text>
					</view>
				</view>
			</view>
			<image src="https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=191757928,2533871883&fm=15&gp=0.jpg" mode=""></image>
		</view>
		<view class="common">
			<text class="common-title">常用功能</text>
			<view class="common-box">
				<navigator :url="item.url" hover-class="none" class="common-item" v-for="(item,index) in commonList" :key="index">
					<text class="iconfont" :class="item.icon"></text>
					<text>{{item.text}}</text>
				</navigator>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				commonList: [
					{
						icon: 'icon-Collect',
						text: '观看历史',
						url: '/pages/WatchHistory/WatchHistory'
					},
					{
						icon: 'icon-Collect',
						text: '我的追剧',
						url: '/pages/BingeWatching/BingeWatching'
					},
					{
						icon: 'icon-Collect',
						text: '我的收藏',
						url: ''
					},
					{
						icon: 'icon-Collect',
						text: '离线缓存',
						url: ''
					}
				]
			}
		},
		methods: {
			
		}
	}
</script>

<style lang="scss" scoped>
.my{
	padding: 100rpx 0 20rpx 0;
	.sign-box{
		padding: 0 40rpx;
		display: flex;
		justify-content: space-between;
		align-items: center;
		.sign-title{
			display: flex;
			flex-direction: column;
			text:nth-child(1){
				font-size: 40rpx;
				font-weight: 700;
			}
			text:nth-child(2){
				font-size: 26rpx;
				color: #808080;
			}
			.sign-btn-box{
				display: flex;
				margin-top: 10rpx;
				.sign-btn{
					padding:  5rpx 20rpx;
					margin-right: 20rpx;
					background-color: #F1F1F1;
					border-radius: 30rpx;
					text{
						font-size: 26rpx;
						color: #808080;
					}
					text:nth-child(1){
						padding-right: 10rpx;
					}
				}
			}
		}
		image{
			width: 170rpx;
			height: 170rpx;
			border-radius: 50%;
		}
	}
	.common{
		margin-top: 40rpx;
		.common-title{
			display: inline-block;
			font-size: 30rpx;
			padding: 20rpx 40rpx;
		}
		.common-box{
			display: flex;
			flex-wrap: wrap;
			.common-item{
				width: 25%;
				display: flex;
				flex-direction: column;
				align-items: center;
				margin-bottom: 20rpx;
				text:nth-child(1){
					font-size: 38rpx;
				}
				text:nth-child(2){
					font-size: 26rpx;
					color: #808080;
				}
			}
		}
	}
}
</style>
