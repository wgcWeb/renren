<template>
	<view class="cate-item">
		<view class="img-content">
			<image :src="list.img" mode=""></image>
			<text class="iconfont icon-Collect cate-icon"></text>
			<text class="cate-point">{{list.point}}</text>
		</view>
		<view class="img-bottom">{{list.title}}</view>
	</view>
</template>

<script>
	export default{
		name: 'CateItem',
		props: ['list'],
		data(){
			return {}
		}
	}
</script>

<style lang="scss" scoped>
	.cate-item {
		width: 210rpx;
		display: flex;
		flex-direction: column;
		
		.img-content {
			width: 210rpx;
			height: 296rpx;
			border-radius: 10rpx;
			overflow: hidden;
			position: relative;
			image {
				width: 100%;
				height: 100%;
			}
			.cate-icon{
				position: absolute;
				top: 10rpx;
				left: 10rpx;
				color: #fff;
			}
			.cate-point{
				position: absolute;
				bottom: 10rpx;
				right: 10rpx;
				color: #007AFF;
				font-weight: 700;
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
</style>
