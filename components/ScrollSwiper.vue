<template>
	<!-- tab栏绑定swiper滑动 -->
	<view class="scroll-swiper" :style="{height: height}">
		<!-- 标题分类栏 -->
		<scroll-view class="nav-fixed" scroll-x="true" >
			<view class="scroll-box">
				<text class="scroll-item" :class="{'act': currentIndex == index}" v-for="(item,index) in navList" :key="index" @tap="handleChange(index)">{{item}}</text>
			</view>
		</scroll-view>
		<!-- 滑动页面 -->
		<swiper @change="onSwiperChange" :current="currentIndex" class="tab-box" :duration="300">
			<swiper-item class="swiper-item" v-for="(item1,index1) in navList" :key="index1">
				<scroll-view class="scroll" scroll-y="true">
					<!-- h5和微信小程序动态绑定slot -->
					<!-- #ifdef H5 -->
					<slot :name="'' + item1"></slot>
					<!-- #endif -->
					<!-- #ifndef H5-->
					<slot name="{{item1}}"></slot>
					<!-- #endif -->
				</scroll-view>
			</swiper-item>
		</swiper>
	</view>
</template>

<script>
	export default {
		name: 'ScrollSwiper',
		props: ['navList','height'],
		data() {
			return {
				currentIndex: 0
			};
		},
		methods: {
			// 切换分类标题
			handleChange(index) {
				this.currentIndex = index
			},
			onSwiperChange(e) {
				this.currentIndex = e.target.current || e.detail.current
			}
		}
	}
</script>

<style lang="scss" scoped>
	.scroll-swiper{
		display: flex;
		flex-direction: column;
		.nav-fixed ::-webkit-scrollbar {
			width: 0 !important;
			display: none;
			height: 0 !important;
			-webkit-appearance: none;
			background: transparent;
		}
		.nav-fixed {
			width: 100%;
			border-bottom: 1rpx solid #CCCCCC;
			.scroll-box{
				display: flex;
				white-space: nowrap;
				padding: 0 20rpx;
				.scroll-item {
					font-size: 30rpx;
					padding: 20rpx 20rpx;
				}
			}
			.act {
				font-size: 40rpx !important;
				font-weight: 700;
			}
		}
		
		.tab-box {
			width: 100%;
			flex: 1;
			// height: calc(100vh - 216rpx);
			// background-color: #fff;
		
			.swiper-item {
				.scroll {
					width: 100%;
					height: 100%;
				}
		
				.scroll ::-webkit-scrollbar {
					width: 0 !important;
					display: none;
					height: 0 !important;
					-webkit-appearance: none;
					background: transparent;
				}
			}
		}
	}
</style>
