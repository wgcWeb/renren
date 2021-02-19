<template>
	<scroll-view class="scroll" scroll-x="true">
		<view class="scroll-item">
			<text :class="{'active': currentIndex == index}" v-for="(item,index) in cateList" @tap="handleChange(index)">{{item}}</text>
			<text class="mask">&nbsp;</text>
		</view>
	</scroll-view>
</template>

<script>
	export default{
		name: 'CateList',
		props: ['cateList'],
		data(){
			return {
				currentIndex: 0
			}
		},
		methods: {
			handleChange(index){
				this.currentIndex = index
			}
		}
	}
</script>

<style lang="scss" scoped>
	.scroll ::-webkit-scrollbar{
		width: 0 !important;
		display: none;
		height: 0 !important;
		-webkit-appearance: none;
		background: transparent;
	}
	.scroll{
		width: 100%;
		box-sizing: border-box;
		
		
		.scroll-item{
			padding: 0 20rpx;
			display: flex;
			white-space: nowrap;	
			text{
				padding: 10rpx 30rpx;
				border-radius: 40rpx;
				// background-color: #F8F8F8;
				margin-right: 10rpx;
			}
			text:last-child{
				background-color: white;
				padding: 10rpx 10rpx;	
			}
			.active{
				background-color: #F8F8F8;
				color: #007AFF;
			}
		}
	}
</style>
