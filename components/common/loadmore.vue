<template>
		<view class="load_more">{{loadtext}}</view>
</template>

<script>
	
	export default {
		props:{
			loadtext:String
		},
		methods: {
		},
	}
</script>

<style scoped>
	.load_more {
		text-align: center;
		color: #AAAAAA;
		padding: 10rpx;
	}
</style>
