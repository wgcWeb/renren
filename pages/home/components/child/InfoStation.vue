<template>
	<view class="info">
		<view class="info-title">
			<text>{{title}}</text>
			<text class="iconfont icon-down" v-if="arrow_show"></text>
		</view>
		<view class="info-box">
			<view class="info-item">
				<view class="info-content">
					<text>阵容太强大,宫九出品必属精品421421412414124</text>
					<view class="content-bottom">
						<text class="iconfont icon-xia_zai"></text>
						<text>爱吃西瓜的葫芦娃</text>
						<text>2021-2-1 21:06:32</text>
					</view>
				</view>
				<view class="img-content">
					<image src="http://www.zzrbl.com/wordpress/wp-content/uploads/2020/12/wojiadegushi.jpg" mode=""></image>
				</view>
			</view>
			<view class="info-item">
				<view class="info-content">
					<text>阵容太强大,宫九出品必属精品421421412414124ddasdsadasdasdad</text>
					<view class="content-bottom">
						<text class="iconfont icon-xia_zai"></text>
						<text>爱吃西瓜的葫芦娃</text>
						<text>2021-2-1 21:06:32</text>
					</view>
				</view>
				<view class="img-content">
					<image src="http://www.zzrbl.com/wordpress/wp-content/uploads/2020/12/wojiadegushi.jpg" mode=""></image>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		name: 'InfoStation',
		props: {
			title: String,
			arrow_show: {
				type: Boolean,
				default: true
			}
		},
		data(){
			return {
				
			}
		},
	}
</script>

<style lang="scss" scoped>
	.info{
		width: 100vw;
		.info-title {
			padding: 20rpx 40rpx;
			display: flex;
			justify-content: space-between;
		
			text:nth-child(1) {
				font-size: 36rpx;
				font-weight: 700;
			}
		}
		.info-box{
			padding: 0 40rpx;
			.info-item:nth-child(1){
				border-bottom: 1rpx solid #C8C7CC;
			}
			.info-item{
				display: flex;
				justify-content: space-between;
				align-items: top;
				padding: 20rpx 0;
				.info-content{
					width: 410rpx;
					display: flex;
					flex-direction: column;
					justify-content: space-between;
					text{
						word-break: break-all;
						text-overflow: ellipsis;
						overflow: hidden;
						display: -webkit-box;
						-webkit-line-clamp: 2;
						-webkit-box-orient: vertical;
					}
					.content-bottom{
						display: flex;
						align-items: center;
						text{
							font-size: 24rpx;
							color: #999999;
						}
						text:nth-child(1){
							line-height: 24rpx;
							margin-right: 10rpx;
						}
						text:nth-child(2){
							display: inline-block;
							margin-right: 25rpx;
							width: 140rpx;
							white-space:nowrap;
							overflow:hidden;
							text-overflow:ellipsis;
						}
					}
				}
				.img-content{
					width: 230rpx;
					height: 140rpx;
					image{
						width: 100%;
						height: 100%;
					}
				}
				
			}
		}
	}
</style>
