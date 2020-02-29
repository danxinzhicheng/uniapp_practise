<template>
	<!-- 	<view class="content">
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view>
	</view> -->

	<!--循环一维数组 和对象-->


	<view>
		<view class="font">{{list1[0]}}</view>
		<view class="font">{{list1[1]}}</view>
		<view class="font">{{list1[2]}}</view>
		<view class="font">{{list1[3]}}</view>

		<view class="font" v-for="(val,index) in list1" :key="i"> {{val}} - {{index}}</view>
		
		<view class="font" v-for="(val,index) in list2" :key="i">
			==============
			{{val.locate}}
			
			<view class="font"   v-for="(val2,index2) in val.list" :key="index2"> {{val2}} - {{index2}} </view>
			
			==============
		</view>
		
		<view class="font" v-for="(value,key) in listobj" :key="key">
			
			{{value}}
			++++
			{{key}}
		
		</view>
		
		<view class="button" @tap="taptest()">点击事件</view>
	</view>


</template>

<script>
	export default {
		data() {
			return {
				title: 'HelloMy',
				list1: ["暗球", "羽毛球", "篮球", "网球"],
				list2: [{
						"locate": "jaingsu",
						"list": ["暗球", "羽毛球", "篮球", "网球"]
					},
					{
						"locate": "shandong",
						"list": ["暗球2", "羽毛球2", "篮球2", "网球2"]
					},

				],
				listobj: {
					name1: "zhangsan",
					name2: "lisi",
					name3: "wangwu"
				}


			}
		},
		onLoad() {

		},
		methods: {
			taptest(){
				console.log("点击了");
			}

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

	.font {
		font-size: 40rpx;
	}
	.button {
		background-color: #09BB07;
		color: #FFFFFF;
		height: 80rpx;
		width: 80%;
		display: flex;
		justify-content: center;
		align-items: center;
		margin: auto;
		border-radius: 30rpx;
		border: 1rpx solid #007AFF;
		
	}
</style>
