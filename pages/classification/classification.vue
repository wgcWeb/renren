<template>
	<view class="classification">
		<view id="active">
			<navigator open-type="navigateBack" hover-class="none">
				<text class="iconfont icon-arrow-l"></text>
			</navigator>
			<navigator url="/pages/SearchBox/SearchBox" hover-class="none">
				<text class="iconfont icon-chaxun"></text>
			</navigator>
			<view class="top-title">影视分类</view>
		</view>
		<view id="cate-box">
			<cate-list class="cate-top" :cate-list="cateList[0]"></cate-list>
			<cate-list class="cate" :cate-list="cateList[1]"></cate-list>
			<cate-list class="cate" :cate-list="cateList[2]"></cate-list>
			<cate-list class="cate" :cate-list="cateList[3]"></cate-list>
			<cate-list class="cate" :cate-list="cateList[4]"></cate-list>
			<cate-list class="cate" :cate-list="cateList[5]"></cate-list>
		</view>
		<view class="select-fixed">
			<view class=""  v-show="is_select" @tap="handleShowCate">
				全部/全部/全部
				<text class="iconfont icon-Collect"></text>
			</view>
			<view id="cate-box" :style="{'display': is_hidden}">
				<cate-list class="cate-top" :cate-list="cateList[0]"></cate-list>
				<cate-list class="cate" :cate-list="cateList[1]"></cate-list>
				<cate-list class="cate" :cate-list="cateList[2]"></cate-list>
				<cate-list class="cate" :cate-list="cateList[3]"></cate-list>
				<cate-list class="cate" :cate-list="cateList[4]"></cate-list>
				<cate-list class="cate" :cate-list="cateList[5]"></cate-list>
				</view>
		</view>
		
		<view class="cate-content">
			<cate-item class="cate-item"  v-for="(item,index) in list" :key="index" :list="item"></cate-item>
		</view>
	</view>
</template>

<script>
	import CateList from './components/CateList.vue'
	import CateItem from './components/CateItem.vue'
	import concentration from 'data/concentration.json'
	export default {
		name: 'classification',
		components:{
			CateList,
			CateItem
		},
		data() {
			return {
				cateList: [
					['最热播放','最近更新','最近好评','本季新剧'],
					['全部','电视剧','电影','综艺','脱口秀','纪录片','动漫','迷你剧','网剧'],
					['全部','美国','英国','韩国','日本','泰国','内地','中国香港','中国台湾','其他'],
					['全部','剧情','喜剧','动作','冒险','爱情','歌舞','恐怖','科幻','奇幻','动画','悬疑','惊悚','犯罪','同性','传记','历史','战争','灾难','美食','真人秀'],
					['全部','2021','2020','2019','2018','2017','2016','2015','2014-2011','2010-2000','90年代','80年代'],
					['全部','连载','完结','未开播'],
				],
				list: [],
				is_select: false,
				is_hidden: 'none'
			}
		},
		onLoad() {
			this.list.push(...concentration.allWatch,...concentration.douyinWatch) 
		},
		onPageScroll(e) {
			this.is_hidden = 'none'
			let search_box = document.getElementById("active");
			let cate_box = document.getElementById("cate-box");
			if(e.scrollTop >= (search_box.offsetHeight + cate_box.offsetHeight)){
				this.is_select = true
			}else{
				this.is_select = false
			}
		},
		methods: {
			handleShowCate(){
				this.is_select = false
				this.is_hidden = 'block'
			}
		}
	}
</script>

<style lang="scss" scoped>
.classification{
	background-color: #fff;
	padding-top: 108rpx;
	#active{
		width: 100%;
		padding: 30rpx 40rpx;
		position: fixed;
		left: 0;
		top: 0;
		z-index: 99;
		background-color: #fff;
		color: #808080;
		display: flex;
		justify-content: space-between;
		box-sizing: border-box;
		text{
			font-size: 48rpx;
		}
		.top-title {
			position: fixed;
			top: 30rpx;
			left: 50%;
			transform: translateX(-50%);
			transition: color 2s;
		}
	}
	#cate-box{
		// .cate-top{
		// 	margin-top: 108rpx;
		// }
		.cate{
			margin-top: 30rpx;
		}
	}
	.select-fixed{
		width: 100%;
		position: fixed;
		left: 0;
		top: 115rpx;
		text-align: center;
		z-index: 9;
		background-color: #fff;
		display: flex;
		flex-direction: column;
	}
	.cate-content{
		margin: 0 40rpx;
		display: flex;
		justify-content: space-between;
		flex-wrap: wrap;
		.cate-item{
			margin-top: 40rpx;
		}
	}
}
</style>
