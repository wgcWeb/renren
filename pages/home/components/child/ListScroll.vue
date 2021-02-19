<template>
	<view class="list" :style="{marginBottom: outstyle}">
		<view class="list-title">
			<text :class="{'act': currentIndex == index}" v-for="(item,index) in list" :key="index" @click="tabClick(index)">{{item.name}}</text>
		</view>
		<scroll-view v-show="currentIndex == index1" class="scroll" scroll-x="true" v-for="(item1,index1) in list" :key="index1">
			<view class="scroll-box">
				<view class="scroll-item" v-for="(item,index) in item1.child" :key="index">
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
		</scroll-view>
	</view>
</template>

<script>
	export default{
		name: 'ListScroll',
		props: ['list','tvList','outstyle'],
		data(){
			return {
				currentIndex: 0,
			}
		},
		methods: {
			tabClick(index){
				this.currentIndex = index
			}
		}
	}
</script>

<style lang="scss" scoped>
	// 排行榜
	.list{
		.list-title{
			padding: 20rpx 0 20rpx 20rpx;
			text{
				font-size: 30rpx;
				padding: 0 20rpx;
			}
			.act{
				font-size: 32rpx;
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
						position: relative;
						line-height: 0;
						border-radius: 10rpx;
						overflow: hidden;
						image {
							width: 100%;
							height: 100%;
						}
		
						.sea-coll {
							height: 60rpx;
							line-height: 60rpx;
							position: absolute;
							left: 0;
							bottom: 0;
							color: #C8C7CC;
							width: 100%;
							display: flex;
							align-items: center;
							justify-content: space-between;
							background-color: rgba($color: #000000, $alpha: .6);
		
							text:nth-child(1) {
								font-size: 28rpx;
							}
		
							text:nth-child(2) {
								font-size: 34rpx;
								line-height: 30rpx;
								margin-right: 20rpx;
							}
						}
					}
					.content-title{
						font-size: 32rpx;
						white-space:nowrap;
						overflow:hidden;
						text-overflow:ellipsis;
					}
					.content-bottom {
						display: flex;
						line-height: 30rpx;
		
						text:nth-child(1) {
							color: #007AFF;
							margin-right: 10rpx;
						}
						text:nth-child(2) {
							white-space:nowrap;
							overflow:hidden;
							text-overflow:ellipsis;
						}
						text {
							font-size: 24rpx;
						}
					}
				}
			}
		}
	}
</style>
