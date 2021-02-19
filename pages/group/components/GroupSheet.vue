<template>
	<view class="group-scroll">
		<view class="group-title">{{title}}</view>
		<view class="group-content">
			<!-- 片单组件 -->
			<sheet v-for="(item,index) in tvList" :key="index" :list="item.child" :title="item.name" :length="item.child.length" :img="item.child[0].img" :text="[item.child[0].title,item.child[1].title,item.child[2].title]"></sheet>
		</view>
	</view>
</template>

<script>
	import Sheet from './Sheet.vue'
	export default{
		name: 'GroupSheet',
		props: ['tvList','title'],
		components:{
			Sheet
		},
		data(){
			return{}
		}
	}
</script>

<style lang="scss" scoped>
	.group-scroll {
		margin-top: 115rpx;
		.group-title {
			font-size: 46rpx;
			font-weight: 700;
			padding: 20rpx 100rpx 30rpx 40rpx;
			background-color: #fff;
		}
	
		.group-content {
			margin: 0 40rpx;
		}
	}
</style>
