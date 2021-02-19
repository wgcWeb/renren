<template>
	<view class="all-watch">
		<view class="watch-title" @tap="handleChangeView">
			<text>{{title}}</text>
			<text class="iconfont icon-down" v-if="arrow_show"></text>
		</view>
		<scroll-view class="scroll" scroll-x="true">
			<view class="scroll-box">
				<view class="scroll-item" v-for="(item,index) in tvList" :key="index">
					<view class="img-content" @tap="handleChange">
						<image :src="item.img" mode="widthFix"></image>
						<view class="sea-coll">
							<text>{{item.title}}</text>
							<text>{{item.content}}</text>
							<text>共{{item.num}}部</text>
						</view>
					</view>
				</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		name: 'TvGroup',
		props: {
			tvList: Array,
			title: String,
			arrow_show: {
				type: Boolean,
				default: true
			}
		},
		methods:{
			handleChangeView(){
				if(this.arrow_show){
					uni.navigateTo({
						url: `/pages/group/group?title=${this.title}`
					})
				}
			},
			handleChange(){
				uni.navigateTo({
					url: '/pages/list/list'
				})
			}
		}
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
						position: relative;
						height: 230rpx;
						border-radius: 10rpx;
						overflow: hidden;
						image {
							width: 500rpx;
							border-radius: 10rpx;
						}

						.sea-coll {
							width: 500rpx;
							height: 230rpx;
							background-color: rgba($color: #000000, $alpha: .4);
							color: #fff;
							position: absolute;
							left: 0;
							bottom: 0;
							display: flex;
							flex-direction: column;
							padding: 30rpx 0 20rpx 30rpx;
							box-sizing: border-box;
							text{
								display: inline-block;
							}
							text:nth-child(1){
								width: 300rpx;
								font-size: 36rpx;
								font-weight: 700;
								white-space:nowrap;
								overflow:hidden;
								text-overflow:ellipsis;
							}
							text:nth-child(2){
								width: 300rpx;
								font-size: 26rpx;
								color: #C8C7CC;
								line-height: 38rpx;
								// margin-top: 30rpx;
								white-space:nowrap;
								overflow:hidden;
								text-overflow:ellipsis;
							}
							text:nth-child(3){
								width: 100rpx;
								font-size: 28rpx;
								background-color: rgba($color: #000000, $alpha: .1);
								text-align: center;
								border-radius: 40rpx;
								margin-top: 25rpx;
							}
						}
					}
				}
			}
		}
	}
</style>
