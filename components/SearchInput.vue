<template>
	<!-- 搜索栏 -->
	<view class="search">
		<image src="https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=1429871452,4246708244&fm=26&gp=0.jpg" mode="heightFix"></image>
		<view class="search-input" @tap="handleSearch">
			<text class="iconfont icon-chaxun"></text>
			<text>哲仁王后</text>
		</view>
		<view class="search-right">
			<slot></slot>
		</view>
	</view>
</template>

<script>
	export default {
		name: 'SearchInput',
		data() {
			return {

			}
		},
		methods:{
			handleSearch(){
				uni.navigateTo({
					url: '/pages/SearchBox/SearchBox'
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.search {
		display: flex;
		align-items: center;
		background-color: #F9F9F9;
		padding: 0 30rpx;

		image {
			display: inline-block;
			height: 100rpx;
		}

		.search-input {
			background-color: #E9E9E9;
			color: #808080;
			flex: 1;
			margin: 0 30rpx;
			padding: 10rpx 0 10rpx 20rpx;
			border-radius: 30rpx;

			text:nth-child(1) {
				margin-right: 10rpx;
			}
		}

		.search-right {
			color: #808080;
			// width: 110rpx;

		}
	}
</style>
