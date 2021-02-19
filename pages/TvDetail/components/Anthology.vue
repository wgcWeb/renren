<template>
	<view class="all-watch">
		<view class="watch-title">
			<text class="tv-title">选集</text>
			<view class="tv-list" @tap="handleChooseShow">
				<text>已完结</text>
				<text class="iconfont icon-down"></text>
			</view>
		</view>
		<scroll-view class="scroll" scroll-x="true">
			<view class="scroll-box">
				<view class="scroll-item" :class="{'active': current == index}" v-for="(item,index) in tvList" :key="index" @tap="handleChoose(index)">
					{{index}}
				</view>
				<view class="last"></view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		name: 'Anthology',
		data(){
			return {
				currentIndex: 0,
				choose_show: false
			}
		},
		props: {
			tvList: Array,
			current: Number
		},
		methods:{
			handleChoose(index){
				this.currentIndex = index
				this.$emit('chooseIndex',this.currentIndex)
			},
			handleChooseShow(){
				this.choose_show = true
				this.$emit('chooseShow', this.choose_show)
			},
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

			.tv-title {
				font-size: 36rpx;
				font-weight: 700;
			}
			.tv-list{
				text{
					font-size: 32rpx;
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
			.scroll-box {
				display: flex;
				white-space: nowrap;
				padding: 20rpx 30rpx;

				.scroll-item:last-child {
					margin-right: 40rpx;
				}

				.scroll-item {
					margin: 0 10rpx;
					display: inline-block;
					width: 100rpx;
					height: 100rpx;
					flex-shrink: 0;
					line-height: 100rpx;
					text-align: center;
					box-shadow: 5px 5px 10px rgba(0, 0, 0, .1);
				}
				.last{
					padding: 20rpx;
				}
				.active{
					color: #007AFF
				}
			}
		}
	}
</style>
