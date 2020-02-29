<template>
	<!-- <view class="content">
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title" :selectable="true">{{title}}</text>
		</view>
	</view> -->
	
	<view >
		<view class="box">
			
			<view class="box-item">1111</view>
			<view class="box-item">2222</view>
			<!-- <view class="box-item">3333</view> -->
			<!-- <view class="box-item">4444</view>
			<view class="box-item">5555</view>
			<view class="box-item">6666</view> -->
		</view>
	</view>
	
</template>

<script>
	export default {
		data() {
			return {
				title: 'HelloFen'
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		/* margin-top: 200rpx;
		margin-bottom: 50rpx; */
	}

	.text-area {
		display: flex;
		margin-left: 20rpx;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
	.view-box {
		background-color: #007AFF;
		width: 200upx;
		height: 200upx;
		color: #09BB07;
		margin: 100upx;
	}
	
	.box {
		width: 100%;
		height: 500upx;
		display: flex;
		flex-direction: column;
		border: 1upx solid #007AFF;
		align-items: center;
		justify-content: center;
	}
	.box-item{
		background: #2C405A;
		color: #FFFFFF;
		width: 200upx;
		font-size: 30upx;
		font-weight: bold;
		text-align: center;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.box-item:nth-of-type(odd){
		
	}
	.box-item:nth-of-type(even){
		background: #09BB07;
	}
	.box-item:nth-of-type(1){
		flex: 1;
	}
	.box-item:nth-of-type(2){
		flex: 2;
		align-self: flex-end;
	}
		
</style>
