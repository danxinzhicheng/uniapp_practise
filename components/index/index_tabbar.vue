<template>
	<!-- 顶部tabbar 横向滚动scrollview -->
	<scroll-view class='uni-swiper-tab' scroll-x>
		<block v-for="(tabitem,index) in tabBars" :key="tabitem.id">
			<view class="swiper-tab-list" :class="{'active':tabDefIndex==index}" @tap="tabtap(index)">
				{{tabitem.name}}
				<view class="swipe-tab-line"></view>
			</view>
		</block>
	</scroll-view>
</template>

<script>
	export default {
		props:{
			tabBars : Array,
			tabDefIndex : Number
		},
		methods:{
			tabtap(index){
				this.$emit("tabtap",index);
			}
		}
	}
</script>

<style scoped>
	.uni-swiper-tab {
		border-bottom: 1rpx solid #EEEEEE;
	}
	.swiper-tab-list {
		color: #969696;
		font-weight: bold;
	}
	.uni-tab-bar .active {
		color: #343434;
	}
	
	.active .swipe-tab-line {
		border-bottom: 6rpx solid #FEDE33;
		border-top: 6rpx solid #FEDE33;
		width: 70rpx;
		margin: auto;
		border-radius: 20rpx;
	}
	
</style>
