<template>
	<view>
		<block v-for="(item,index) in itemList" :key="index">
			<view class="content">
				<view class="left">
					<image class="user_avatar" :src="item.userAvatar" mode="widthFix" lazy-load></image>
				</view>
				<view class="middle">
					<view class="user_name">{{item.userName}}</view>
					<view class="user_mark">{{item.userMark}}</view>
				</view>
				<view class="right">
					<view class="user_time">{{item.userTime}}</view>
					<view class="user_num" @tap="testauth()">{{item.userNum}}</view>
				</view>
			</view>
		</block>

		<loadMore :loadtext="loadtext"></loadMore>

	</view>

</template>

<script>
	import loadMore from '../../components/common/loadmore.vue';

	export default {
		components: {
			loadMore
		},

		data() {
			return {
				loadtext: "上拉加载更多",
				itemList: [{
						userAvatar: "../../static/demo/demo66.jpg",
						userName: "小王",
						userMark: "今天天气不错你那边呢",
						userTime: "9:30",
						userNum: 30


					},
					{
						userAvatar: "../../static/demo/demo66.jpg",
						userName: "小王",
						userMark: "今天天气不错你那边呢",
						userTime: "9:30",
						userNum: 30
					},
					{
						userAvatar: "../../static/demo/demo66.jpg",
						userName: "小王",
						userMark: "今天天气不错你那边呢",
						userTime: "9:30",
						userNum: 30
					},
					{
						userAvatar: "../../static/demo/demo66.jpg",
						userName: "小王",
						userMark: "今天天气不错你那边呢",
						userTime: "9:30",
						userNum: 30
					},
					{
						userAvatar: "../../static/demo/demo66.jpg",
						userName: "小王",
						userMark: "今天天气不错你那边呢",
						userTime: "9:30",
						userNum: 30
					},
					{
						userAvatar: "../../static/demo/demo66.jpg",
						userName: "小王",
						userMark: "今天天气不错你那边呢",
						userTime: "9:30",
						userNum: 30
					},
					{
						userAvatar: "../../static/demo/demo66.jpg",
						userName: "小王",
						userMark: "今天天气不错你那边呢",
						userTime: "9:30",
						userNum: 30
					},
					{
						userAvatar: "../../static/demo/demo66.jpg",
						userName: "小王",
						userMark: "今天天气不错你那边呢",
						userTime: "9:30",
						userNum: 30
					},
					{
						userAvatar: "../../static/demo/demo66.jpg",
						userName: "小王",
						userMark: "今天天气不错你那边呢",
						userTime: "9:30",
						userNum: 30
					}
				]
			}
		},
		onLoad() {

		},
		onPullDownRefresh() {
			this.refreshData()
		},
		onReachBottom() {
			this.addData();
		},
		methods: {

			testauth() {
				//微信授权
				uni.getProvider({
					service: 'oauth',
					success: function(res) {
						console.log(res.provider);
						uni.login({
							provider: "weixin",
							success: function(loginRes) {
								console.log('-------获取openid(unionid)-----');
								console.log(JSON.stringify(loginRes));
								uni.getUserInfo({
									provider: 'weixin',
									success: function(infoRes) {
										console.log('-------获取微信用户所有-----');
										console.log(infoRes);
										let a = JSON.parse(infoRes.rawData);
										let username = a.nickName;
										console.log("----获取微信用户名：" + username);

									}
								})
							},

						})
					}
				})
			},
			addData() {
				var _this = this;
				setTimeout(function() {
					if (_this.loadtext != "上拉加载更多") {
						return false; //等于上拉加载触发方法，不等于就阻止触发
					}
					// _this.loadtext = "加载中。。。";

					let obj = {
						userAvatar: "../../static/demo/demo66.jpg",
						userName: "小王333",
						userMark: "今天天气不错你那边呢",
						userTime: "9:30",
						userNum: 30
					}

					_this.itemList.push(obj);
					// _this.loadtext = "我是有底线的~";
				}, 1000);

			},
			refreshData() {

				setTimeout(() => {
					let list = [{
							userAvatar: "../../static/demo/demo66.jpg",
							userName: "小王111",
							userMark: "今天天气不错你那边呢",
							userTime: "9:30",
							userNum: 30
						},
						{
							userAvatar: "../../static/demo/demo66.jpg",
							userName: "小王111",
							userMark: "今天天气不错你那边呢",
							userTime: "9:30",
							userNum: 30
						},
						{
							userAvatar: "../../static/demo/demo66.jpg",
							userName: "小王111",
							userMark: "今天天气不错你那边呢",
							userTime: "9:30",
							userNum: 30
						},
						{
							userAvatar: "../../static/demo/demo66.jpg",
							userName: "小王222",
							userMark: "今天天气不错你那边呢",
							userTime: "9:30",
							userNum: 30
						}
					]

					this.itemList = list;
					uni.stopPullDownRefresh();
				}, 1000);




			}
		}
	}
</script>

<style>
	.content {
		background-color: white;
		display: flex;
		width: 100%;
		flex-direction: row;
		padding: 20rpx 10rpx;
		align-items: center;
		border-bottom: 1rpx solid #D9D9D9;
		position: relative;
	}

	.left>image {
		width: 80rpx;
		border-radius: 40rpx;
	}

	.middle {
		display: flex;
		flex-direction: column;
		margin-left: 10rpx;
	}

	.user_name {
		font-size: 35rpx;
		color: #333333;
		font-weight: bold;
	}

	.user_mark {
		font-size: 20rpx;
		color: #666666;
		margin-top: 10rpx;
	}

	.right {
		position: absolute;
		right: 40rpx;
		bottom: 20rpx;
	}

	.user_time {
		font-size: 25rpx;
		font-weight: bold;
		color: #666666;
	}

	.user_num {
		background-color: red;
		border-radius: 30rpx;
		color: white;
		padding-left: 20rpx;
		padding-right: 20rpx;
		padding-top: 0rpx;
		padding-bottom: 0rpx;
	}
</style>
