<template>
	<view>
		
		<block v-for="(item,index) in list" :key="key">
			<indexListCard :item='item'></indexListCard>
		</block>
		
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

				list: [{
					pic: '../../static/demo/userpic/12.jpg',
					name: '昵称',
					isGuanZhu: false,
					title: '我是标题',
					titlePic: '../../static/demo/datapic/11.jpg',
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
				 	titlePic: '../../static/demo/datapic/11.jpg',
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
				 	titlePic: '../../static/demo/datapic/11.jpg',
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
				 	titlePic: '../../static/demo/datapic/11.jpg',
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

			}
		},
		methods: {

		}
	}
</script>

<style>

</style>
