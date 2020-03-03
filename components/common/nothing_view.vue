<template>
	<view class="nothing">
		<image src="../../static/logo.png" lazy-load mode="widthFix"></image>
	</view>
</template>

<script>
</script>

<style scoped>
	.nothing{
		display: flex;
		justify-content: center;
		align-items: center;
		position: absolute;
		top: 0;
		bottom: 0;
		left: 0;
		right: 0;
	}
	.nothing image{
		width: 50%;
	}
</style>
