<template>
	<view class="content">
		<view class="top">登录糗百，体验更多功能</view>

		<view class="other_login">

			<view class="view_wx1">
				<view class="view_wx icon iconfont icon-weixin"></view>
			</view>
			<view class="view_wx1">
				<view class="view_wx icon iconfont icon-xinlangweibo"></view>
			</view>
			<view class="view_wx1">
				<view class="view_wx icon iconfont icon-QQ"></view>
			</view>

		</view>

		<view class="top">
			账号密码登录
			<view class="icon iconfont icon-jinru"></view>
		</view>
		
		<view class="homedata">
			
			<view class="area">
				<view class="area_num">0</view>
				<view class="area_txt">糗事</view>
			</view>
			
			<view class="area">
				<view class="area_num">10</view>
				<view class="area_txt">动态</view>
			</view>
			
			<view class="area">
				<view class="area_num">10</view>
				<view class="area_txt">评论</view>
			</view>
			
			<view class="area">
				<view class="area_num">30</view>
				<view class="area_txt">收藏</view>
			</view>
			
		</view>
		
		<view class="img_ad_view">
			<image class="img_ad"  src="../../static/demo/datapic/1.jpg" mode="widthFix" lazy-load></image>
			
		</view>
		
		
		<view class="home-list">
			<view class="item1" hover-class="item_h">
				<view class="item_left">  
				 <view class="icon iconfont icon-liulan"></view>
				 浏览历史
				 </view>
				<view class="item_right icon iconfont icon-jinru"></view>
			</view>
			
			
			<view class="item1" hover-class="item_h">
				<view class="item_left">  
				 <view class="icon iconfont icon-liulan"></view>
				 糗百认证
				 </view>
				<view class="item_right icon iconfont icon-jinru"></view>
			</view>
			
			<view class="item1" hover-class="item_h">
				<view class="item_left">  
				 <view class="icon iconfont icon-liulan"></view>
				 浏览历史
				 </view>
				<view class="item_right icon iconfont icon-jinru"></view>
			</view>
			
			
			<view class="item1" hover-class="item_h">
				<view class="item_left">  
				 <view class="icon iconfont icon-liulan"></view>
				 糗百认证
				 </view>
				<view class="item_right icon iconfont icon-jinru"></view>
			</view>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		methods: {

		}
	}
</script>

<style>
	.top {
		display: flex;
		justify-content: center;
	}
	.view_wx1{
		flex: 1;
		display: flex;
		justify-content: center;
	}

	.other_login {
		width: 100%;
		padding: 20upx;
		display: flex;
		flex-direction: row;
		justify-content: center;
	}

	.view_wx {
		width: 100upx;
		height: 100upx;
		font-size: 55upx;
		border-radius: 100%;
		color: white;
	}

	.icon {
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.icon-weixin {
		background: #2BD19B;
	}

	.icon-xinlangweibo {
		background: #FC7729;
	}

	.icon-QQ {
		background: #2CAEFC;
	}
	
	.homedata{
		display: flex;
		justify-content: center;
		flex-direction: row;
		align-items: center;
		padding: 20rpx 40rpx;
		
	}
	.area{
		display: flex;
		justify-content: center;
		flex-direction: column;
		align-items: center;
		flex: 1;
	}
	.area_num{
		font-size: 32rpx;
		
	}
	.area_txt{
		color: #989898;
	}
	.img_ad_view{
		width: 100%;
		height: auto;
		display: flex;
		justify-content: center;
		padding: 20upx;
	}
	.img_ad{
		border-radius: 20rpx;
		height: 150rpx;
	}
	.home-list{
		display: flex;
		flex-direction: column;
		padding: 20rpx;
		justify-content: center;
	}
	.item1{
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		padding: 20upx;
		border-top: 1upx solid #EEEEEE;
		border-bottom: 1upx solid #EEEEEE;
	}
	.item_left{
		display: flex;
		flex-direction: row;
		color: #333333;
	}
	.item_right{
		color: #CCCCCC;
	}
	.item_h{
		background-color: #F4F4F4;
	}
	.item_left > view:first-child{
		margin-right: 10rpx;
	}
</style>
