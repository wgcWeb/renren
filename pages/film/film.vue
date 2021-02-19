<template>
	<view class="film">
		<search-input class="search">
			<navigator url="/pages/classification/classification" hover-class="none">
				<view class="cate-all">
					<text class="iconfont icon-fenlei"></text>
					<text>全部</text>
				</view>
			</navigator>
		</search-input>
		<!-- 轮播图 -->
		<carousel class="carousel" :swiper-list="swiperList"></carousel>
		<!-- 正在热播 -->
		<simple-scroll class="ma-top" :tv-list="tvList" title="正在热播"></simple-scroll>
		<!-- 最近更新 -->
		<simple-scroll class="ma-top" :tv-list="updateList" title="最近更新"></simple-scroll>
		<!-- 专属片单 -->
		<group-sheet :tv-list="listScroll" title="专属片单"></group-sheet>
	</view>
</template>

<script>
	import Carousel from '../../components/Carousel.vue'
	import SearchInput from '../../components/SearchInput.vue'
	import SimpleScroll from './components/SimpleScroll.vue'
	import GroupSheet from '../group/components/GroupSheet.vue'
	import Sheet from '../group/components/Sheet.vue'
	import concentration from 'data/concentration.json'
	
	export default {
		name: 'film',
		components:{
			Carousel,
			SearchInput,
			SimpleScroll,
			GroupSheet,
			Sheet
		},
		data() {
			return {
				swiperList: [],
				tvList: [],
				updateList: [],
				listScroll: []
			}
		},
		onLoad() {
			this.swiperList = concentration.swiperList
			this.tvList = concentration.allWatch
			this.updateList = concentration.douyinWatch
			this.listScroll = concentration.listScroll
		},
		methods: {
			
		}
	}
</script>

<style lang="scss" scoped>
.film{
	.search{
		.cate-all{
			width: 110rpx;
			display: flex;
			justify-content: space-between;
			align-items: center;
			padding: 10rpx 20rpx;
			background-color: #E9E9E9;
			border-radius: 40rpx;
			font-size: 30rpx;
		}
	}
	.carousel,.ma-top{
		margin-top: 20rpx;
	}
}
</style>
