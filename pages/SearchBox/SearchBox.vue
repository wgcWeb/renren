<template>
	<view class="search-box">
		<!-- 返回按钮 -->
		<navigator open-type="navigateBack" hover-class="none">
			<view class="back iconfont icon-arrow-l"></view>
		</navigator>
		<!-- 顶部背景图 -->
		<image src="http://www.zzrbl.com/wordpress/wp-content/uploads/2020/12/wojiadegushi.jpg"></image>
		<view class="search-content">
			<!-- input搜索栏 -->
			<view class="search-input">
				<text class="iconfont icon-chaxun"></text>
				<input type="text" placeholder-style="color:#ccc" v-model="input_inner" placeholder="钢琴家"/>
				<text v-show="input_inner.length>0" class="iconfont icon-chaxun" @tap="handleInputClean"></text>
			</view>
			<!-- 历史记录 -->
			<view class="history-box" v-show="!is_history">
				<view class="history-title">
					<text>历史搜索</text>
					<text class="iconfont icon-Collect" @tap="handleDelete"></text>
				</view>
				<view class="his-list">
					<text v-for="(item,index) in historyList" :key="index">{{item}}</text>
				</view>
			</view>
			<!-- 底部滑动推荐列表 -->
			<scroll-swiper class="scroll-swiper" :nav-list="navList" >
				<view class="scroll-box" v-for="(item,index) in navList" :key="index" :slot="item">
					<view class="scroll-item" v-for="(item1,index1) in recommendList" :key="index1">
						<text class="item-index" :class="{'active': index1 <= 2}">{{index1+1}}</text>
						<view class="item-right">
							<view class="right-title">
								<text>{{item1.title}}</text>
								<text :style="{'backgroundColor': getbgc(item1.title_icon)}">{{item1.title_icon}}</text>
							</view>
							<text class="item-content">{{item1.content}}</text>
						</view>
					</view>
					
				</view>
			</scroll-swiper>
		</view>
	</view>
</template>

<script>
	import ScrollSwiper from '../../components/ScrollSwiper.vue'
	export default {
		name: 'SearchBox',
		components:{
			ScrollSwiper
		},
		data() {
			return {
				// input输入内容
				input_inner: '',
				// 是否显示历史记录
				is_history: false,
				// 历史记录
				historyList: ['触不可及','上升','罢工','上班不上','花君','哲仁王后'],
				// 推荐列表分类
				navList: ['热搜','电影','美剧','英剧','韩剧','日剧','泰剧'],
				// 推荐列表
				recommendList: [
					{
						title: '旺达幻视',
						title_icon: '新',
						content: '是糖是刀准备好了吗'
					},
					{
						title: '高桥一生我老婆',
						title_icon: '热',
						content: '男女互换超级带感'
					},
					{
						title: '女神降临',
						title_icon: '热',
						content: '甜甜的恋爱永不完结'
					},
					{
						title: '曼达洛人',
						title_icon: '荐',
						content: '最强科幻之作'
					},
					{
						title: '奶狗男主又甜又攻',
						title_icon: '热',
						content: '小白兔女主无力抵抗'
					},
					{
						title: 'Run on',
						title_icon: '热',
						content: '双向奔赴的爱情完结撒花'
					},
					{
						title: '18勿入',
						title_icon: '热',
						content: '意乱情迷时被带上手铐'
					},
					{
						title: '重口味神剧',
						title_icon: '荐',
						content: '一心想嫁入豪门的后果'
					},
				],
			}
		},
		methods: {
			// 控制推荐列表标签旁小字背景颜色
			getbgc(text) {
				let bgc = ''
				switch(text){
					case '新':
						bgc = '#4CD964';
					break;
					case '热':
						bgc = '#C9394A';
					break;
					case '荐':
						bgc = '#F0AD4E';
					break;
				}
				return bgc
			},
			// 点击清除input文字
			handleInputClean(){
				this.input_inner = ''
			},
			// 历史记录删除
			handleDelete(){
				this.is_history = true
			}
		}
	}
</script>

<style lang="scss" scoped>
.search-box{
	display: flex;
	flex-direction: column;
	.back{
		position: fixed;
		top: 40rpx;
		left: 30rpx;
		z-index: 9;
		font-size: 40rpx;
		color: #fff;
		background-color: rgba($color: #000000, $alpha: .6);
		display: inline-block;
		width: 50rpx;
		height: 50rpx;
		line-height: 50rpx;
		text-align: center;
		border-radius: 50%;
	}
	image{
		width: 100%;
		height: 400rpx;
	}
	.search-content{
		position: relative;
		flex: 1;
		padding-top: 60rpx;
		.search-input{
			position: absolute;
			top: -35rpx;
			left: 50%;
			transform: translateX(-50%);
			display: flex;
			align-items: center;
			width: 500rpx;
			height: 70rpx;
			box-sizing: border-box;
			background-color: #fff;
			border-radius: 40rpx;
			padding: 0 40rpx;
			input{
				width: 100%;
				margin: 0 20rpx;
				// color: #CCCCCC;
			}
		}
		.history-box{
			padding: 0 40rpx 20rpx 40rpx;
			.history-title{
				display: flex;
				justify-content: space-between;
				text:nth-child(1){
					font-size: 36rpx;
					font-weight: 700;
				}
				text:nth-child(2){
					font-size: 32rpx;
					color: #808080;
				}
			}
			.his-list{
				display: flex;
				flex-wrap: wrap;
				text{
					font-size: 24rpx;
					padding: 5rpx 30rpx;
					color: #808080;
					background-color: #F1F1F1;
					border-radius: 30rpx;
					margin-right: 30rpx;
					margin-top: 15rpx;
				}
			}
		}
		.scroll-swiper{
			width: 100%;
			height: calc(100vh - 668rpx);
			.scroll-box{
				display: flex;
				flex-wrap: wrap;
				padding: 30rpx 40rpx;
				// height: 100%;
				.scroll-item{
					display: flex;
					width: 50%;
					padding-bottom: 30rpx;
					.item-index{
						font-size: 28rpx;
						color: #808080;
						padding-right: 10rpx;
					}
					.active{
						color: #C9394A;
					}
					.item-right{
						display: flex;
						flex-direction: column;
						.right-title{
							display: flex;
							align-items: center;
							text{
								font-size: 28rpx;
							}
							text:nth-child(2){
								font-size: 22rpx;
								margin-left: 10rpx;
								background-color: #4CD964;
								display: inline-block;
								text-align: center;
								color: #fff;
								border-radius: 10rpx;
								width: 35rpx;
								height: 35rpx;
								line-height: 35rpx;
							}
						}
						.item-content{
							font-size: 24rpx;
							color: #808080;
							line-height: 0;
							padding-top: 15rpx;
						}
					}
				}
			}	
		}
	}
}

</style>
