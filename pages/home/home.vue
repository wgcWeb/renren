<template>
	<view class="home">
		<!-- 搜索栏 -->
		<search-input class="search">
			<view class="search-box">
				<navigator url="/pages/WatchHistory/WatchHistory" hover-class="none">
					<text class="iconfont icon-shijianicon"></text>
				</navigator>
			</view>
		</search-input>

		<!-- 分类导航 -->
		<scroll-view class="tabbar" scroll-x="true" :scroll-into-view="toview" scroll-with-animation="true">
			<view @tap="onTabTap(index)" v-for="(item,index) in tabbar" :id="item.id" :key="item.id">
				<text :class="{'active': tabIndex == index}">{{item.name}}</text>
			</view>
		</scroll-view>
		<!-- 内容 -->
		<swiper @change="onSwiperChange" :current="tabIndex" class="tab-box" :duration="300">
			<swiper-item class="swiper-item">
				<scroll-view class="scroll" scroll-y="true">
					<Concentration></Concentration>
				</scroll-view>
			</swiper-item>
			<swiper-item class="swiper-item">
			</swiper-item>
			<swiper-item class="swiper-item">
			</swiper-item>
			<swiper-item class="swiper-item">
			</swiper-item>
			<swiper-item class="swiper-item">
			</swiper-item>
			<swiper-item class="swiper-item">
			</swiper-item>
			<swiper-item class="swiper-item">
			</swiper-item>
			<swiper-item class="swiper-item">
			</swiper-item>
		</swiper>
	</view>
</template>

<script>
	import Concentration from './components/Concentration.vue'
	import SearchInput from '../../components/SearchInput.vue'
	export default {
		name: 'home',
		data() {
			return {
				tabbar: [{
						name: '精选',
						id: "tab01",
					},
					{
						name: '美剧',
						id: "tab02",
					},
					{
						name: '英剧',
						id: "tab03",
					},
					{
						name: '韩剧',
						id: "tab04",
					},
					{
						name: '日剧',
						id: "tab05",
					},
					{
						name: '泰剧',
						id: "tab06",
					},
					{
						name: '国产剧',
						id: "tab07",
					}
				],
				tabIndex: 0,
				toview: ""
			}
		},
		components: {
			Concentration,
			SearchInput
		},
		methods: {
			onTabTap(index) {
				this.tabIndex = index
			},
			onSwiperChange(e) {
				this.tabIndex = e.target.current || e.detail.current

				this.toview = this.tabbar[this.tabIndex].id

			}
		}
	}
</script>

<style lang="scss" scoped>
	.home {
		// height: 100vh;
		display: flex;
		flex-direction: column;

		.search {
			.search-box {
				// width: 100rpx;
				// display: flex;
				// justify-content: space-between;
				// align-items: center;

				text {
					font-size: 40rpx;
				}

			}
		}

		.tabbar {
			white-space: nowrap;
			background-color: #F9F9F9;

			view {
				display: inline-block;
				padding: 35rpx 0 35rpx 40rpx;

				text {
					padding: 0 10rpx;
				}
			}

			view:last-child {
				padding-right: 40rpx;
			}
		}

		.tabbar ::-webkit-scrollbar {
			width: 0 !important;
			display: none;
			height: 0 !important;
			-webkit-appearance: none;
			background: transparent;
		}

		.tab-box {
			flex: 1;

			// background-color: #4CD964;
			.swiper-item {

				// height: 100%;
				.scroll {
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

	.active {
		font-size: 36rpx;
		font-weight: 700;
	}

	// #ifdef MP-WEIXIN
	.home {
		height: 100vh;
	}

	// #endif
	// #ifdef H5
	.home {
		height: 92.5vh;
	}

	// #endif
</style>
