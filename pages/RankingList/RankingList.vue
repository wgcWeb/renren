<template>
	<view class="rankingList">
		<view class="active" :style="{'background':navbg.topbg}">
			<navigator open-type="navigateBack" hover-class="none">
				<text class="iconfont icon-arrow-l" style="transition: color 1s;font-size: 48rpx;" :style="{'color':navbg.iconCol}"></text>
			</navigator>
			<view class="top-title" :style="{'opacity':navbg.titleCol}">每日排行榜</view>
		</view>
		<view class="list-bg">
			<view class="bg" :style="{'background':UrlImg}"></view>
			<view class="bg-w" :style="{'background':navbg.conbg, 'z-index':navbg.conzindex}"></view>
			<view class="bg-content">
				<view class="bg-left">
					<view class="left-title">每日排行榜</view>
					<view class="left-num">昨日播放量top99</view>
					<view class="left-bottom" @tap="handleBottomShow">
						<text>{{msg}}</text>
						<text class="iconfont icon-zhuanhuan1"></text>
					</view>
				</view>
				<view class="bg-right">
					<image :src="img" mode=""></image>
				</view>
			</view>
		</view>
		<scroll-view class="scroll-view" scroll-x="true" >
			<view class="nav-fixed">
				<text :class="{'act': currentIndex == index}" v-for="(item,index) in navList" :key="index" @tap="handleChange(index)">{{item}}</text>
			</view>
		</scroll-view>
		
		<swiper @change="onSwiperChange" :current="currentIndex" class="tab-box" :duration="300">
			<swiper-item class="swiper-item" v-for="(item1,index1) in itemList" :key="index1">
				<scroll-view class="scroll" scroll-y="true" >
					<view class="scroll-box">
						<view class="scroll-item" v-for="(item2,index2) in item1.child" :key="index2">
							<text class="item-id">{{index2 + 1}}</text>
							<view class="item-right">
								<image :src="item2.img" mode=""></image>
								<view class="right-content">
									<text>旺达幻视</text>
									<text>2021/美国/动作/科幻/悬疑/喜剧/爱情</text>
									<text>更新至4集</text>
								</view>
							</view>
						</view>
					</view>
				</scroll-view>
			</swiper-item>
		</swiper>
		<btn-mask @changeTitle="changeTitle" ref="mask" :choose-list="chooseList"></btn-mask>
	</view>
</template>

<script>
	import BtnMask from '../../components/BtnMask.vue'
	import concentration from 'data/concentration.json'
	export default {
		name: 'RankingList',
		components:{
			BtnMask
		},
		data() {
			return {
				navbg: {
					topbg: '',
					iconCol: '#fff',
					titleCol: '0.0',
					conbg: '',
					conzindex: '-1'
				},
				navList: ['美剧','韩剧','日剧','泰剧','英剧'],
				chooseList: ['日排行','周排行','月排行','全部排行'],
				itemList: [],
				currentIndex : 0,
				msg: '日排行',
				img: ''
			}
		},
		onLoad() {
			this.itemList = concentration.listScroll
			this.img = this.itemList[this.currentIndex].child[0].img
			this.UrlImg = `url(${this.img}) no-repeat top`
		},
		onPageScroll(e) {
			if(e.scrollTop>=50){
				this.navbg.topbg = '#fff'
				this.navbg.iconCol = '#808080'
				this.navbg.titleCol = '1.0'
			}else if(e.scrollTop<50){
				this.navbg.topbg = ''
				this.navbg.iconCol = '#fff'
				this.navbg.titleCol = '0.0'
			}
			
			if(e.scrollTop>=70){
				this.navbg.conbg = '#fff'
				this.navbg.conzindex = '9'
			}else if(e.scrollTop<70){
					this.navbg.conbg = ''
					this.navbg.conzindex = '-1'
			}
		},
		methods: {
			// 切换分类标题
			handleChange(index){
				this.currentIndex = index
			},
			onSwiperChange(e){
				this.currentIndex = e.target.current || e.detail.current
				
				this.img = this.itemList[this.currentIndex].child[0].img
				this.UrlImg = `url(${this.img}) no-repeat top`
			},
			changeTitle(item){
				this.msg = item
			},
			handleBottomShow(){
				this.$refs.mask.handleBottom()
			},
		}
	}
</script>

<style lang="scss" scoped>
.rankingList{
	.active{
		width: 100%;
		padding: 30rpx 0 30rpx 40rpx;
		position: fixed;
		left: 0;
		top: 0;
		z-index: 99;
		transition: background-color 1s;
		.top-title {
			position: fixed;
			top: 30rpx;
			left: 50%;
			transform: translateX(-50%);
			color: #808080;
			transition: opacity 2s;
		}
	}
	.list-bg{
		position: relative;
		width: 100%;
		height: 460rpx;
		// background: url('http://www.zzrbl.com/wordpress/wp-content/uploads/2020/12/tianguoyudiyu.jpg') no-repeat top;
		overflow: hidden;
		.bg{
			position: absolute;
			top: -50rpx;
			left: -1100rpx;
			width: 400%;
			height: 400%;
			background: url('http://www.zzrbl.com/wordpress/wp-content/uploads/2020/12/tianguoyudiyu.jpg') no-repeat top;
			filter: blur(10px);
		}
		.bg-w{
			position: absolute;
			top: 0;
			left: 0;
			width: 100%;
			height: 460rpx;
			// z-index: 9;
			transition: background-color 1s;
		}
		.bg-content{
			width: 100%;
			height: 460rpx;
			position: absolute;
			top: 0;
			left: 0;
			color: #fff;
			padding: 100rpx 50rpx 0 40rpx;
			display: flex;
			justify-content: space-between;
			box-sizing: border-box;
			.bg-left{
				display: flex;
				flex-direction: column;
				.left-title{
					font-size: 48rpx;
				}
				.left-num{
					padding: 40rpx 0 70rpx 0;
				}
				.left-bottom{
					display: flex;
					align-items: center;
					font-size: 26rpx;
					text:nth-child(1){
						margin-right: 20rpx;
					}
				}
			}
			.bg-right{
				width: 260rpx;
				height: 360rpx;
				overflow: hidden;
				border-radius: 10rpx;
				image{
					width: 100%;
					height: 100%;
				}
			}
		}
	}
	.scroll-view ::-webkit-scrollbar {
		width: 0 !important;
		display: none;
		height: 0 !important;
		-webkit-appearance: none;
		background: transparent;
	}
	.scroll-view{
		width: 100%;
		background-color: #fff;
	}
	.nav-fixed{
		display: flex;
		white-space: nowrap;
		// border-bottom: 1rpx solid #C8C7CC;
		text{
			font-size: 34rpx;
			padding: 30rpx 55rpx;
		}
		.act{
			font-size: 40rpx;
			font-weight: 700;
		}
	}
	.tab-box{
		width: 100%;
		height: calc(100vh - 216rpx);
		background-color: #fff;
		.swiper-item{
			.scroll{
				width: 100%;
				height: 100%;
				.scroll-box{
					background-color: #fff;
					.scroll-item{
						width: 100%;
						display: flex;
						align-items: center;
						// padding-right: 30rpx;
						.item-id{
							padding: 0 30rpx;
						}
						.item-right{
							display: flex;
							width: 600rpx;
							padding: 30rpx 0;
							border-bottom: 1rpx solid #C8C7CC;
							image{
								width: 150rpx;
								height: 200rpx;
								border-radius: 10rpx;
							}
							.right-content{
								display: flex;
								flex-direction: column;
								padding: 10rpx 0 0 20rpx;
								text:nth-child(1){
									font-size: 32rpx;
									font-weight: 700;
									white-space: nowrap;
									overflow: hidden;
									text-overflow: ellipsis;
								}
								text:nth-child(2){
									font-size: 26rpx;
									color: #808080;
									white-space: nowrap;
									overflow: hidden;
									text-overflow: ellipsis;
								}
								text:nth-child(3){
									font-size: 26rpx;
									color: #808080;
									padding-top: 50rpx;
								}
							}
						}
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
		}
	}
}
</style>
