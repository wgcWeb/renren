<template>
	<view>
		<view class="bottom" :style="{'z-index':bottombg}" @touchmove.stop.prevent="moveHandle" @tap.stop="handleBottom">
			<view class="bottom-content">
				<view class="bottom-list">
					<text :class="{'choose': tabIndex == index}" v-for="(item,index) in chooseList" :key="index" @tap.stop="handleChoose(index,item)">{{item}}</text>
				</view>
				<view class="bottom-btn" @tap.stop="handleBottom">取消</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: 'BtnMask',
		props: ['chooseList'],
		data() {
			return {
				tabIndex: 0,
				bottomShow: false,
				bottombg: '-9'
			};
		},
		methods:{
			// 切换排行分类
			handleChoose(index,item){
				this.tabIndex = index
				this.$emit('changeTitle', item)
				this.bottomShow = !this.bottomShow
				this.bottombg = '-9'
			},
			// 显示排行分类
			handleBottom(){
				if(this.bottomShow){
					this.bottomShow = !this.bottomShow
					this.bottombg = '-9'
				}else{
					this.bottomShow = !this.bottomShow
					this.bottombg = '9999'
				}
			},
			// 禁止蒙布下页面滑动
			moveHandle(){
			},
		}
	}
</script>

<style lang="scss" scoped>
.bottom{
		width: 100%;
		height: 100vh;
		position: fixed;
		left: 0;
		top: 0;
		background-color: rgba($color: #000000, $alpha: .6);
		z-index: 999;
		.bottom-content{
			width: 100%;
			position: absolute;
			left: 0;
			bottom: 0;
			background-color: #fff;
			.bottom-list{
				height: 500rpx;
				display: flex;
				flex-direction: column;
				justify-content: space-evenly;
				align-items: center;
				border-bottom: 1rpx solid #C8C7CC;
				text{
					font-size: 32rpx;
				}
				.choose{
					color: #007AFF;
				}
			}
			.bottom-btn{
				text-align: center;
				padding: 30rpx 0;
				color: #808080;
			}
		}
	}
</style>
