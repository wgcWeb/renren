<template>
	<view class="swipercontent ">
		<swiper class="swiper" :indicator-dots="false" :autoplay="true" :interval="2000" :duration="1000" :circular="true" @change="onSwiperChange">
			<swiper-item v-for="(item,index) in swiperList" :key="index" class="swiper-item">
				<navigator url="/pages/TvDetail/TvDetail" hover-class="none">
					<image :src="item.img" mode="widthFix"></image>
				</navigator>
				<text>{{item.msg}}</text>
			</swiper-item>
		</swiper>
		<view class="dots">
		  <block v-for="(item1,index1) in swiperList" :key="index1">
		    <view class="dot" :class="{'active' : index1 == swiperCurrent}"></view>
		  </block>
		</view>
	</view>
</template>

<script>
	export default{
		name: 'Carousel',
		props: ['swiperList'],
		data(){
			return {
				swiperCurrent: 0,
			}
		},
		methods:{
			onSwiperChange(e){
				this.swiperCurrent = e.target.current || e.detail.current
			},
		}
	}
</script>

<style lang="scss" scoped>
	.swipercontent{
		position: relative;
		margin: 0 40rpx;
		.swiper {
			height: 350rpx;
			border-radius: 10rpx;
			overflow: hidden;
		
			.swiper-item {
				position: relative;
				image {
					width: 100%;
					margin-top: -30rpx;
				}
		
				text {
					position: absolute;
					left: 20rpx;
					bottom: 20rpx;
					color: #fff;
					font-size: 34rpx;
				}
			}
		}
		.dots{
		  position: absolute;
		  // left: 0;
		  right: 20rpx;
		  bottom: 20rpx;
		  display: flex;
		  justify-content: center;
			.dot{
			  margin: 0 8rpx;
			  width: 14rpx;
			  height: 14rpx;
			  background: #fff;
			  border-radius: 8rpx;
			  transition: all .6s;
			}
			.active{
			  width: 24rpx;
			  background: #f80;
			}
		}
	}
</style>
