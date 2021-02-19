<template>
	<view class="list">
		<view class="list-top">
			<text class="iconfont icon-arrow-l" @tap="back"></text>
			<view class="top-right">
				<text class="iconfont icon-Collect"></text>
				<text class="iconfont icon-fenxiang"></text>
			</view>
		</view>
		<view class="list-box">
			<view class="list-title">
				那些年,KSWL的荧幕CP
			</view>
			<view class="list-detail">
				<text>甜死我啦甜死我了</text>
				<text>共19部</text>
			</view>
			<view class="scroll-box">
				<view class="scroll-item" v-for="(item,index) in tvList" :key="index">
					<image :src="item.img"></image>
					<view class="sea-coll">
						<view class="content-title">
							<text>{{item.title}}</text>
							<text>第一季</text>
						</view>
						<view class="content-middle">
							<text>2021/美国/剧情/喜剧</text>
							<text>虐恋深情之直女X基佬</text>
						</view>
						<view class="content-bottom">
							<text>8.0</text>
							<text>10集全</text>
						</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import concentration from 'data/concentration.json'
	export default {
		name: 'list',
		data() {
			return {
				tvList: []
			}
		},
		created() {
			this.tvList = concentration.allWatch
		},
		methods: {
			back(){
				uni.navigateBack()
			}
		}
	}
</script>

<style lang="scss" scoped>
	.list {
		padding: 0 40rpx;

		.list-top {
			display: flex;
			justify-content: space-between;
			margin-top: 30rpx;
			text{
				font-size: 48rpx;
			}

			.top-right {
				text{
					font-size: 40rpx;
				}
				text:nth-child(2) {
					margin-left: 50rpx;
				}
			}
		}

		.list-box {
			.list-title {
				font-size: 46rpx;
				font-weight: 700;
				padding: 40rpx 0;
			}

			.list-detail {
				display: flex;
				flex-direction: column;
				color: #999999;
			}

			.scroll-box {
				width: 100%;

				.scroll-item {
					width: 100%;
					display: flex;
					padding: 25rpx 0;
					image{
						width: 200rpx;
						height: 296rpx;
						border-radius: 10rpx;
					}
					.sea-coll{
						width: 470rpx;
						padding-left: 20rpx;
						.content-title{
							width: 100%;
							display: flex;
							justify-content: space-between;
							align-items: center;
							font-size: 32rpx;
							text:nth-child(1){
								// margin-right: 40rpx;
								width: 330rpx;
								white-space:nowrap;
								overflow:hidden;
								text-overflow:ellipsis;
							}
							text:nth-child(2){
								width: 100rpx;
								text-align: center;
							}
						}
						.content-middle{
							display: flex;
							flex-direction: column;
							color: #8F8F94;
							margin: 20rpx 0 30rpx 0;
							text:nth-child(2){
								height: 48rpx;
								white-space:nowrap;
								overflow:hidden;
								text-overflow:ellipsis;
							}
						}
						
						.content-bottom{
							text:nth-child(1){
								margin-right: 10rpx;
								color: #007AFF;
							}
							text:nth-child(2){
								color: #8F8F94;
							}
						}
					}
				}
			}
		}
	}
</style>
