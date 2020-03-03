<template>
	<view class="content" >

		<view class="list_card" >
			<view class="list1">

				<view class="list1-left">
					<image class="img_avatar" :src="item.pic" mode="widthFix" lazy-load></image>
					{{item.name}}
				</view>


				<view class="list1-right" v-show="!isGuanZhu" @click="guanzhu()">
					<view class="iconfont icon-zengjia"></view>
					关注
				</view>

			</view>


			<view class="list2" @tap="gotodetail()">
				{{item.title}}
			</view>


			<view class="list3" @tap="gotodetail()">

				<image :src="item.titlePic" mode="widthFix" :lazy-load="true"></image>
				<template v-if="item.type == 'video'">
					<view class="iconfont icon-bofang"></view>
					<view>{{item.paly}}次播放 {{item.lang}}</view>
				</template>

			</view>

			<view class="list4">

				<view class="list4-left">
					<view class="list4-left-1 iconfont" :class="infonum.index==1?'active':'' " @click="doding()">
						<view class=" icon-icon_xiaolian-mian"> {{infonum.ding}} </view>
					</view>

					<view class="list4-left-2 iconfont" :class="infonum.index==2?'active_red':'' " @click="docai()">
						<view class="icon icon-kulian"> {{infonum.cai}} </view>
					</view>


				</view>

				<view class="list4-right">

					<view class="list4-left-1 iconfont">
						<view class=" icon-xiaoxi">{{item.ping}}</view>

					</view>

					<view class="list4-left-2 iconfont">
						<view class=" icon-zhuanfa">{{item.share}}</view>
					</view>


				</view>

			</view>
		</view>
	</view>
</template>

<script>
	export default {

		props: {
			item: Object,
			index: Number
		},

		data() {
			return {
				isGuanZhu: this.item.isGuanZhu,
				infonum: this.item.infonum
			}
		},
		methods: {

			guanzhu() {

				this.isGuanZhu = true;
				uni.showToast({ //弹框
					title: '关注成功',
					icon: 'success'
				})
			},
			doding() {
				//未顶--置黄 +1 （如果踩了 踩置默认 -1）
				//已经顶 -- 置默认 -1
				console.log("======this.info.index==" + this.infonum.index);
				if (this.infonum.index == 0) {
					this.infonum.ding++;
					this.infonum.index = 1;
				} else if (this.infonum.index == 1) {
					this.infonum.ding--;
					this.infonum.index = 0;
				} else if (this.infonum.index == 2) {
					this.infonum.cai--;
					this.infonum.ding++;
					this.infonum.index = 1;
				}
			},
			docai() {
				console.log("======this.info.index==" + this.infonum.index);
				if (this.infonum.index == 0) {
					this.infonum.cai++;
					this.infonum.index = 2;
				} else if (this.infonum.index == 2) {
					this.infonum.cai--;
					this.infonum.index = 0;
				} else if (this.infonum.index == 1) {
					this.infonum.ding--;
					this.infonum.cai++;
					this.infonum.index = 2;
				}
			},
			caoZuo(type) { //点击顶和踩的操作
				switch (type) {
					case 'ding':
						if (this.infonum.index == 1) { //只执行一次
							return false;
						}
						this.infonum.ding++;
						if (this.infonum.index == 2) { //只执行一次
							this.infonum.cai--;
						}
						this.infonum.index = 1;
						break;
					case 'cai':
						if (this.infonum.index == 2) { //只执行一次
							return false;
						}
						this.infonum.cai++;
						if (this.infonum.index == 1) { //只执行一次
							this.infonum.ding--;
						}
						this.infonum.index = 2;
						break;
					default:
						break;
				}
			},
			gotodetail(){
				uni.showToast({
					title: '进入详情页'
				});
			}
		}
	}
</script>

<style scoped>
	.content {
		padding: 20rpx;
	}

	.list_card {
		padding-bottom: 20rpx;
		border-bottom: 1rpx solid #EFEFEF;
	}

	.list1 {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
	}

	.list1-left {
		display: flex;
		flex-direction: row;
		align-items: center;
		font-size: 30rpx;
		color: #999999;
	}

	.img_avatar {
		width: 50rpx;
		height: 50rpx;
		border-radius: 50rpx;
		margin-right: 10rpx;
	}

	.list1-right {
		display: flex;
		flex-direction: row;
		height: 60rpx;
		align-items: center;
		background-color: #EEEEEE;
		padding: 0rpx 10rpx;
		font-weight: bold;
		border-radius: 5rpx;
	}

	.list2 {
		margin-top: 10rpx;
		font-size: 35rpx;
		color: #666666;
	}

	.list3 {
		position: relative;
		height: auto;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.list3>image {
		margin-top: 10rpx;
		width: 100%;
		height: auto;
		border-radius: 5rpx;
	}

	.list3>view:nth-child(2) {
		position: absolute;
		color: #FFFFFF;
		font-size: 80rpx;
	}

	.list3>view:nth-child(3) {
		position: absolute;
		width: auto;
		padding: 0 15rpx;
		background: rgba(0, 0, 0, .5);
		border-radius: 20rpx;
		bottom: 10rpx;
		right: 10rpx;
		color: #FFFFFF;
	}


	.list4 {
		display: flex;
		flex-direction: row;
		align-items: center;
		margin-top: 10rpx;
		justify-content: space-between;
	}

	.list4-left {
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: center;
	}

	.list4-right {
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: center;
	}

	.list4-left-1 {
		margin-right: 20rpx;
		font-size: 10rpx;
	}

	.iconfont {
		color: #999999;
		font-size: 40rpx;
		margin-top: 10rpx;
	}

	.active {
		color: #FFB400;
	}

	.active_red {
		color: red;
	}
</style>
