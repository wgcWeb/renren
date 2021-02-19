<template>
	<view class="concentration">
		<!-- 轮播图 -->
		<carousel :swiper-list="swiperList"></carousel>
		
		<!-- 导航栏 -->
		<view class="nav">
			<navigator url="/pages/classification/classification" hover-class="none">
				<view class="nav-item">
					<text class="iconfont icon-fenlei"></text>
					<text>影视分类</text>
				</view>
			</navigator>
			<navigator url="/pages/Schedule/Schedule" hover-class="none">
				<view class="nav-item">
					<text class="iconfont icon-yudingdanpaiqibiao"></text>
					<text>排期表</text>
				</view>
			</navigator>
			<navigator url="/pages/RankingList/RankingList" hover-class="none">
				<view class="nav-item">
					<text class="iconfont icon-ziyuan"></text>
					<text>排行榜</text>
				</view>
			</navigator>
			<navigator url="/pages/BingeWatching/BingeWatching" hover-class="none">
				<view class="nav-item">
					<text class="iconfont icon-tv"></text>
					<text>追剧</text>
				</view>
			</navigator>
		</view>
		<!-- 大家都在看 -->
		<tv-scroll class="tv-list" :tv-list="allWatch" title="大家都在看" :arrow_show="true"></tv-scroll>
		
		<!-- 进站必刷美剧 -->
		<tv-scroll class="tv-list" :tv-list="americanTV" title="进站必刷美剧" :arrow_show="false"></tv-scroll>
		<!-- 抖音爆火神剧 -->
		<tv-scroll class="tv-list" :tv-list="douyinWatch" title="抖音爆火神剧" :arrow_show="false"></tv-scroll>
		
		<!-- 排行榜 -->
		<list-scroll class="tv-list" :list="listScroll" :tv-list="allWatch"></list-scroll>
		<!-- 热门口碑电影 -->
		<tv-group class="tv-list" :tv-list="sweetGroup" title="热门口碑电影"></tv-group>
		<!-- 一起get成吨快乐 -->
		<tv-scroll class="tv-list" :tv-list="douyinWatch" title="一起get成吨快乐" :arrow_show="false"></tv-scroll>
		<!-- 十万人打分9分以上 -->
		<tv-scroll class="tv-list" :tv-list="americanTV" title="十万人打分9分以上" :arrow_show="false"></tv-scroll>
		<!-- 我爱上的人是奇葩 -->
		<tv-scroll class="tv-list" :tv-list="allWatch" title="我爱上的人是奇葩" :arrow_show="false"></tv-scroll>
		<!-- 口碑新剧 -->
		<title-group :tv-list="allWatch" title="人人都在看 . 口碑新剧"></title-group>
		
		<!-- 情报站 -->
		<!-- <info-station title="韩剧情报站"></info-station> -->
		
		<!-- 经典殿堂 -->
		<classic :tv-list="americanTV" title="经典殿堂"></classic>
	</view>
</template>

<script>
	import TvScroll from './child/TvScroll.vue'
	import TvGroup from './child/TvGroup.vue'
	import TitleGroup from './child/TitleGroup.vue'
	import ListScroll from './child/ListScroll.vue'
	import Classic from './child/Classic.vue'
	import Carousel from '../../../components/Carousel.vue'
	import concentration from 'data/concentration.json'
	export default {
		name: 'Concentration',
		components: {
			TvScroll,
			TvGroup,
			TitleGroup,
			ListScroll,
			Classic,
			Carousel
		},
		data() {
			return {
				// boxStyle: {
				// 	marginBottom: '100rpx'
				// },
				swiperList: [],
				allWatch: [],
				sweetGroup: [],
				americanTV: [],
				douyinWatch: [],
				listScroll: []
			};
		},
		created(){
			this.getData()
		},
		methods:{
			getData(){
				this.swiperList = concentration.swiperList
				this.allWatch = concentration.allWatch
				this.sweetGroup = concentration.sweetGroup
				this.americanTV = concentration.americanTV
				this.douyinWatch = concentration.douyinWatch
				this.listScroll = concentration.listScroll
			},
		}
	}
</script>

<style lang="scss" scoped>
	.concentration {
		overflow: hidden;
		.nav{
			margin: 30rpx 40rpx 20rpx 40rpx;
			display: flex;
			justify-content: space-between;
			.nav-item{
				display: flex;
				flex-direction: column;
				justify-content: space-between;
				align-items: center;
				text:nth-child(1){
					font-size: 46rpx;
					color: #007AFF;
				}
				text:nth-child(2){
					font-size: 28rpx;
					color: #808080;
				}
			}
		}
		.tv-list{
			margin-bottom: 40rpx;
		}
	}

	// #ifdef MP-WEIXIN
	
	// #endif
</style>
