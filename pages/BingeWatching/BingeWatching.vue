<template>
	<view class="binge-watching">
		<navigator open-type="navigateBack" hover-class="none">
			<view class="active">
				<text class="iconfont icon-arrow-l"></text>
			</view>
		</navigator>
		<scroll-swiper height="calc(100vh - 86rpx)" class="scroll-swiper" :nav-list="navList">
			<view class="scroll-box" slot="剧集">
				<view class="scroll-title">
					<text @tap="handleBottomShow(msg_type)">{{msg_type}}</text>
					<text @tap="handleBottomShow(msg_lately)">{{msg_lately}}</text>
				</view>
				<view class="scroll-item" v-for="(item,index) in itemList[0].child" :key="index">
					<view class="img-content">
						<image :src="item.img"></image>
						<view class="sea-coll">
							<text v-if="item.is_end">{{item.set_num}}集全</text>
							<text v-else>更新至{{item.set_num}}集</text>
						</view>
					</view>
					<text class="content-title">{{item.title}}</text>
					<view class="content-bottom">
						<text v-if="item.watched">已看至{{item.watched}}集{{item.percentage}}</text>
						<text v-else>无观看记录</text>
					</view>
				</view>
			</view>
			
			<view class="scroll-box" slot="片单">
				暂无收藏的片单
			</view>
		</scroll-swiper>
		
		<btn-mask @changeTitle="changeTitleType" ref="maskType" :choose-list="chooseListType"></btn-mask>
		<btn-mask @changeTitle="changeTitleLately" ref="maskLately" :choose-list="chooseListLately"></btn-mask>
	</view>
</template>

<script>
	import BtnMask from '../../components/BtnMask.vue'
	import ScrollSwiper from '../../components/ScrollSwiper.vue'
	export default {
		name: 'BingeWatching',
		components: {
			ScrollSwiper,
			BtnMask
		},
		data() {
			return {
				navList: ['剧集', '片单'],
				itemList: [{
						name: '剧集',
						child: [
							{
								img: 'https://images.cnblogsc.com/pic/upload/vod/2020-08/1596450723.jpg',
								set_num: '8',
								is_end: false,
								title: '妖怪合租屋',
								watched: '1',
								percentage: '75%'
							},
							{
								img: 'https://images.cnblogsc.com/pic/upload/vod/2019-05/15592881935.jpg',
								set_num: '20',
								is_end: true,
								title: '吻我',
								watched: '1',
								percentage: '15%'
							},
							{
								img: 'https://images.cnblogsc.com/pic/upload/vod/2020-08/1596450723.jpg',
								set_num: '8',
								is_end: false,
								title: '妖怪合租屋',
								watched: '1',
								percentage: '75%'
							},
							{
								img: 'https://images.cnblogsc.com/pic/upload/vod/2019-05/15592881935.jpg',
								set_num: '20',
								is_end: true,
								title: '吻我',
								watched: '1',
								percentage: '15%'
							},
							{
								img: 'https://images.cnblogsc.com/pic/upload/vod/2020-08/1596450723.jpg',
								set_num: '8',
								is_end: false,
								title: '妖怪合租屋',
								watched: '1',
								percentage: '75%'
							},
							{
								img: 'https://images.cnblogsc.com/pic/upload/vod/2019-05/15592881935.jpg',
								set_num: '20',
								is_end: true,
								title: '吻我',
								watched: '1',
								percentage: '15%'
							},
							{
								img: 'https://images.cnblogsc.com/pic/upload/vod/2020-08/1596450723.jpg',
								set_num: '8',
								is_end: false,
								title: '妖怪合租屋',
								watched: '1',
								percentage: '75%'
							},
							{
								img: 'https://images.cnblogsc.com/pic/upload/vod/2019-05/15592881935.jpg',
								set_num: '20',
								is_end: true,
								title: '吻我',
								watched: '1',
								percentage: '15%'
							},
							{
								img: 'https://images.cnblogsc.com/pic/upload/vod/2020-08/1596450723.jpg',
								set_num: '8',
								is_end: false,
								title: '妖怪合租屋',
								watched: '1',
								percentage: '75%'
							},
							{
								img: 'https://images.cnblogsc.com/pic/upload/vod/2019-05/15592881935.jpg',
								set_num: '20',
								is_end: true,
								title: '吻我',
								watched: '1',
								percentage: '15%'
							},
							{
								img: 'https://images.cnblogsc.com/pic/upload/vod/2020-08/1596450723.jpg',
								set_num: '8',
								is_end: false,
								title: '妖怪合租屋',
								watched: '1',
								percentage: '75%'
							},
							{
								img: 'https://images.cnblogsc.com/pic/upload/vod/2019-05/15592881935.jpg',
								set_num: '20',
								is_end: true,
								title: '吻我',
								watched: '1',
								percentage: '15%'
							},
							{
								img: 'https://images.cnblogsc.com/pic/upload/vod/2020-08/1596450723.jpg',
								set_num: '8',
								is_end: false,
								title: '妖怪合租屋',
								watched: '1',
								percentage: '75%'
							},
							{
								img: 'https://images.cnblogsc.com/pic/upload/vod/2019-05/15592881935.jpg',
								set_num: '20',
								is_end: true,
								title: '吻我',
								watched: '1',
								percentage: '15%'
							},
							{
								img: 'https://images.cnblogsc.com/pic/upload/vod/2020-08/1596450723.jpg',
								set_num: '8',
								is_end: false,
								title: '妖怪合租屋',
								watched: '1',
								percentage: '75%'
							},
							{
								img: 'https://images.cnblogsc.com/pic/upload/vod/2019-05/15592881935.jpg',
								set_num: '20',
								is_end: true,
								title: '吻我',
								watched: '1',
								percentage: '15%'
							},
							{
								img: 'https://images.cnblogsc.com/pic/upload/vod/2020-08/1596450723.jpg',
								set_num: '8',
								is_end: false,
								title: '妖怪合租屋',
								watched: '1',
								percentage: '75%'
							},
							{
								img: 'https://images.cnblogsc.com/pic/upload/vod/2019-05/15592881935.jpg',
								set_num: '20',
								is_end: true,
								title: '吻我',
								watched: '1',
								percentage: '15%'
							},
							{
								img: 'https://images.cnblogsc.com/pic/upload/vod/2020-08/1596450723.jpg',
								set_num: '8',
								is_end: false,
								title: '妖怪合租屋',
								watched: '1',
								percentage: '75%'
							},
							{
								img: 'https://images.cnblogsc.com/pic/upload/vod/2019-05/15592881935.jpg',
								set_num: '20',
								is_end: true,
								title: '吻我',
								watched: '1',
								percentage: '15%'
							},
							{
								img: 'https://images.cnblogsc.com/pic/upload/vod/2020-08/1596450723.jpg',
								set_num: '8',
								is_end: false,
								title: '妖怪合租屋',
								watched: '1',
								percentage: '75%'
							},
							{
								img: 'https://images.cnblogsc.com/pic/upload/vod/2019-05/15592881935.jpg',
								set_num: '20',
								is_end: true,
								title: '吻我',
								watched: '1',
								percentage: '15%'
							},
							{
								img: 'https://images.cnblogsc.com/pic/upload/vod/2020-08/1596450723.jpg',
								set_num: '8',
								is_end: false,
								title: '妖怪合租屋',
								watched: '1',
								percentage: '75%'
							},
							{
								img: 'https://images.cnblogsc.com/pic/upload/vod/2019-05/15592881935.jpg',
								set_num: '20',
								is_end: true,
								title: '吻我',
								watched: '1',
								percentage: '15%'
							},
							{
								img: 'https://images.cnblogsc.com/pic/upload/vod/2020-08/1596450723.jpg',
								set_num: '8',
								is_end: false,
								title: '妖怪合租屋',
								watched: '1',
								percentage: '75%'
							},
							{
								img: 'https://images.cnblogsc.com/pic/upload/vod/2019-05/15592881935.jpg',
								set_num: '20',
								is_end: true,
								title: '吻我',
								watched: '1',
								percentage: '15%'
							},
						]
					},
					{
						name: '片单',
						child: []
					},
				],
				msg_type: '综合',
				msg_lately: '最近追剧排序',
				chooseListType: ['综合','美剧','日剧','韩剧','泰剧'],
				chooseListLately: ['最近追剧排序','最近更新排序'],
			}
		},
		methods: {
			handleBottomShow(msg){
				let str = msg.length
				if(str>2){
					this.$refs.maskLately.handleBottom()
				}else{
					this.$refs.maskType.handleBottom()
				}
			},
			changeTitleType(item){
				this.msg_type = item
			},
			changeTitleLately(item){
				this.msg_lately = item
			}
		}
	}
</script>

<style lang="scss" scoped>
	.binge-watching {
		height: 100vh;
		display: flex;
		flex-direction: column;
		background-color: #F9F9F9;
		.active{
			width: 100%;
			padding: 30rpx 40rpx 0 40rpx;
			color: #808080;
			text{
				font-size: 48rpx;
			}
		}
		.scroll-swiper {
			.scroll-box{
				display: flex;
				flex-wrap: wrap;
				padding: 108rpx 30rpx 0 30rpx;
				.scroll-title{
					width: 100%;
					padding: 30rpx 10rpx;
					position: fixed;
					left: 30rpx;
					top: 0;
					z-index: 9;
					background-color: #F9F9F9;
					text{
						padding: 10rpx 20rpx;
						background-color: #F1F1F1;
						color: #666666;
						margin-right: 20rpx;
						border-radius: 40rpx;
					}
				}
				.scroll-item {
					display: flex;
					flex-direction: column;
					width: 210rpx;
					padding: 0 10rpx;
					margin-bottom: 20rpx;
					.img-content {
						width: 210rpx;
						height: 296rpx;
						position: relative;
						line-height: 0;
						border-radius: 10rpx;
						overflow: hidden;
				
						image {
							width: 100%;
							height: 100%;
						}
				
						.sea-coll {
							line-height: 50rpx;
							position: absolute;
							left: 0;
							bottom: 0;
							color: #fff;
							width: 100%;
							display: flex;
							align-items: center;
							justify-content: space-between;
							background-color: rgba($color: #000000, $alpha: .6);
				
							text{
								padding-left: 20rpx;
								font-size: 26rpx;
							}
						}
					}
				
					.content-title {
						font-size: 32rpx;
						white-space: nowrap;
						overflow: hidden;
						text-overflow: ellipsis;
					}
				
					.content-bottom {
						line-height: 30rpx;
				
						text {
							font-size: 26rpx;
							color: #808080;
							white-space: nowrap;
							overflow: hidden;
							text-overflow: ellipsis;
						}
					}
				}
			}
		}
	}
</style>
