<template>
	<view>

		<view class="uni-tab-bar" animated fadeInLeft>

			<indexTabbar :tabBars="tabBars" :tabDefIndex="tabDefIndex" @tabtap="tabtap"></indexTabbar>


			<!-- swiper类似Android的viewpager或者轮播图 -->
			<swiper :indicator-dots="false" :autoplay="false" :duration="500" :style="{height:swiperHeight+'px'}" :current="tabDefIndex"
			 @change="tabChange">


				<swiper-item v-for="(items,index) in newslist" :key="index">
					<template v-if="items.list.length > 0">
					 <scroll-view scroll-y class="list" @scrolltolower="loadmore(index)">
						<!-- 图文列表 -->
						<block v-for="(item,index1) in items.list" :key="index1">
							<indexListCard :item='item' :index="index1"></indexListCard>
						</block>
						<!-- 上拉加载 -->

						<loadMore :loadtext="items.loadtext"></loadMore>
						</scroll-view>
					</template>

					<template v-else>
						<noThing></noThing>
					</template>



				</swiper-item>

			</swiper>
		</view>


	</view>

</template>

<script>
	import indexListCard from '../../components/index/index-list-card.vue';
	import indexTabbar from '../../components/index/index_tabbar.vue';
	import loadMore from '../../components/common/loadmore.vue';
	import noThing from '../../components/common/nothing_view.vue'
	export default {
		components: {
			indexListCard,
			indexTabbar,
			loadMore,
			noThing
		},
		data() {
			return {

				swiperHeight: 500,
				tabDefIndex: 0,
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
						loadtext: "上拉加载更多...",
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
						loadtext: "上拉加载更多...",
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
						loadtext: "上拉加载更多...",
						list: []
					}, {
						loadtext: "上拉加载更多...",
						list: []
					}, {
						loadtext: "上拉加载更多...",
						list: []
					}, {
						loadtext: "上拉加载更多...",
						list: []
					}
				],
				loadmoreNum: 520, //临时变量
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
			loadmore(index) {
				if (this.newslist[index].loadtext != "上拉加载更多...")
					return;
				this.newslist[index].loadtext == "加载中...";
				setTimeout(() => {
					let obj = {

						pic: '../../static/demo/userpic/12.jpg',
						name: '昵称666',
						isGuanZhu: false,
						title: '我是标题666',
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

					obj.title = "我是标题666" + (this.loadmoreNum++);
					//追加数据
					this.newslist[index].list.push(obj);
				}, 1000);

			},
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

</style>
