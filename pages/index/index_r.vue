<template>
	<view>

		<view class="uni-tab-bar">

			<!-- 顶部tabbar 横向滚动scrollview -->
			<scroll-view class='uni-swiper-tab' scroll-x>
				<block v-for="(tabitem,index) in tabBars" :key="tabitem.id">
					<view class="swiper-tab-list" :class="{'active':tabDefIndex==index}" @tap="tabtap(index)">
						{{tabitem.name}}
						<view class="swipe-tab-line"></view>
					</view>
				</block>
			</scroll-view>

			<!-- swiper类似Android的viewpager或者轮播图 -->
			<swiper :indicator-dots="false" :autoplay="false" :duration="500" :style="{height:swiperHeight+'px'}"
			 :current="tabDefIndex" @change="tabChange">
			 
				<swiper-item v-for="(items,index) in newslist" :key="index">
					<scroll-view scroll-y class="list">
						<block v-for="(item,index1) in items.list" :key="index1">
							<indexListCard :item='item' :index="index1"></indexListCard>
						</block>
					</scroll-view>
				</swiper-item>
				
			</swiper>
		</view>


	</view>

</template>

<script>
	import indexListCard from '../../components/index/index-list-card.vue';
	export default {
		components: {
			indexListCard
		},
		data() {
			return {
				swiperHeight: 500,
				tabDefIndex: 1,
				tabBars: [{
						name: "关注",
						id: "guanzhu"
					},
					{
						name: "推荐",
						id: "tuijian"
					},
					{
						name: "体育",
						id: "tiyu"
					},
					{
						name: "热点",
						id: "redian"
					},
					{
						name: "财经",
						id: "caijing"
					},
					{
						name: "娱乐",
						id: "yule"
					}
				],

				newslist: [

					{
						list: [{
								pic: '../../static/demo/userpic/12.jpg',
								name: '昵称',
								isGuanZhu: false,
								title: '我是标题',
								titlePic: '../../static/demo/datapic/1.jpg',
								type: 'img', //img图文 video视屏
								paly: '20w',
								lang: '02:17',
								infonum: {
									index: 0, //0 为没有操作 1为顶加1 2为踩一下
									ding: 10,
									cai: 10
								},
								ping: 34,
								share: 17
							},
							{
								pic: '../../static/demo/userpic/12.jpg',
								name: '昵称',
								isGuanZhu: false,
								title: '我是标题222',
								titlePic: '../../static/demo/datapic/1.jpg',
								type: 'video', //img图文 video视屏
								paly: '20w',
								lang: '02:17',
								infonum: {
									index: 1, //0 为没有操作 1为顶加1 2为踩一下
									ding: 10,
									cai: 10
								},
								ping: 34,
								share: 17

							}, {
								pic: '../../static/demo/userpic/12.jpg',
								name: '昵称',
								isGuanZhu: false,
								title: '我是标题222',
								titlePic: '../../static/demo/datapic/1.jpg',
								type: 'img', //img图文 video视屏
								paly: '20w',
								lang: '02:17',
								infonum: {
									index: 2, //0 为没有操作 1为顶加1 2为踩一下
									ding: 10,
									cai: 10
								},
								ping: 34,
								share: 17

							}, {
								pic: '../../static/demo/userpic/12.jpg',
								name: '昵称',
								isGuanZhu: false,
								title: '我是标题222',
								titlePic: '../../static/demo/datapic/1.jpg',
								type: 'img', //img图文 video视屏
								paly: '20w',
								lang: '02:17',
								infonum: {
									index: 0, //0 为没有操作 1为顶加1 2为踩一下
									ding: 10,
									cai: 10
								},
								ping: 34,
								share: 17

							}
						]
					}, {
						list: [{
							pic: '../../static/demo/userpic/12.jpg',
							name: '昵称',
							isGuanZhu: false,
							title: '我是标题222',
							titlePic: '../../static/demo/datapic/1.jpg',
							type: 'img', //img图文 video视屏
							paly: '20w',
							lang: '02:17',
							infonum: {
								index: 0, //0 为没有操作 1为顶加1 2为踩一下
								ding: 10,
								cai: 10
							},
							ping: 34,
							share: 17

						}]
					}, {
						list: []
					}, {
						list: []
					}, {
						list: []
					}, {
						list: []
					}
				],
			}
		},

		onLoad() {
			//根据屏幕高度和tab的高度 给scrollview动态赋值高度
			uni.getSystemInfo({
				success: (res) => {
					let heigth = res.windowHeight - uni.upx2px(100); //屏幕高度-tab的高度
					console.log(heigth);
					this.swiperHeight = heigth
				}
			})
		},
		methods: {
			//tab点击事件
			tabtap(index) {
				this.tabDefIndex = index;
			},
			//swipe滑动事件
			tabChange(e) {
				this.tabDefIndex = e.detail.current
			}
		}
	}
</script>

<style>
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

	.uni-swiper-tab {
		border-bottom: 1rpx solid #EEEEEE;
	}
</style>
