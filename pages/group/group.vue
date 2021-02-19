<template>
	<!-- 片单列表 -->
	<view class="group">
		<view class="group-top">
			<view class="iconfont icon-arrow-l" @tap="back"></view>
			<view class="top-title" :style="{'opacity': titleCol}">{{title}}</view>
		</view>
		<!-- 片单 -->
		<group-sheet :tv-list="tvList" :title="title"></group-sheet>
	</view>
</template>

<script>
	
	import GroupSheet from './components/GroupSheet.vue'
	import concentration from 'data/concentration.json'
	export default {
		name: 'group',
		components: {
			GroupSheet,
		},
		data() {
			return {
				tvList: [],
				title: '',
				titleCol: '0.0',
			}
		},
		onLoad(option) {
			this.tvList = concentration.listScroll
			this.title = option.title
		},
		onReady() {
			uni.pageScrollTo({
				scrollTop: 0,
				duration: 300
			});
		},
		onPageScroll(e) {
			if (e.scrollTop >= 20) {
				this.titleCol = '1.0'
			} else if (e.scrollTop < 20) {
				this.titleCol = '0.0'
			}
		},
		methods: {
			back(){
				uni.navigateBack()
			}
		}
	}
</script>

<style lang="scss" scoped>
	.group {
		.group-top {
			background-color: #fff;
			padding: 30rpx 40rpx;
			position: fixed;
			left: 0;
			right: 0;
			top: 0;
			z-index: 99;

			.iconfont {
				font-size: 48rpx;
				display: inline-block;
			}

			.top-title {
				position: fixed;
				top: 30rpx;
				left: 50%;
				transform: translateX(-50%);
				transition: opacity 2s; 
			}

		}

		
	}
</style>
