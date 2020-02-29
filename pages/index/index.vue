<template>
<!-- 	<view class="content">
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view>
	</view> -->
	
	<view>
		
	<!-- 	<view :class="{'box':isActivity}">
			<view class="box-item">{{title}}</view>
			<view class="box-item">测试2</view>
			<view class="box-item">测试3</view>
		</view> -->
		
		<view :class="[age > 10?'box':'']" v-show="(age>20 && age< 29)">
			<view class="box-item">{{title}}</view>
			<view class="box-item">{{age>30?'中年人':'少年'}}</view>
			<view class="box-item">测试3</view>
		</view>
		
			
		<button type="default" @tap="onclick('哈哈哈')">点击修改</button>
		<button type="default" @tap="editStyle()">点击修改样式</button>
		<button type="default" @tap="addAge()">点击增加年龄</button>
		
		<view>{{myconvert}}</view>
		
	</view>



		
		
</template>

<script>
	export default {
		// data() {
		// 	return {
		// 		title: 'HelloIndex'
		// 	}
		// },
		
		data() {
			return {
				classname: 'box',
				title: 'hellowda',
				isActivity: true,
				age: 18,
				isshow: false,
				weight : 2000
			}
		},
		onLoad() {

		},
		computed: {
			myconvert:function() {
				if(this.weight > 1000){
					return this.weight/1000 + "kg";
				}else{
					return this.weight +"g";
				}
			}
		},
		methods: {
			
			onclick:function(name){
				this.title = name;
			},
			editStyle:function(){
				if(this.classname == "box2"){
					this.classname = "box";
				}else{
					this.classname = "box2";
				}
				
			},
			addAge:function(){
				this.age++;
			}

		}
	}
</script>

<style>
	
	.box {
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: center;
		width: 100%;
		height: 500upx;
		background-color: #007AFF;
		border:1upx soild #ff00ff;
	}
	.box2 {
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: center;
		width: 100%;
		height: 500upx;
		background-color: #55aa7f;
		border:1upx soild #ff00ff;
	}
	.box-item{
		display: flex;
		align-items: center;
		justify-content: center;
		flex: 1;
		height: 100%;
		border:1upx solid #09BB07 ;
	}
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
</style>
