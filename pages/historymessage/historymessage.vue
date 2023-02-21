<template>
		<view class="historyBox">
			<image src="../../static/historyBack.png"></image>
			<image src="../../static/Frame 16.png" class="temp"></image>
			<scroll-view class="innerbox" scroll-y="true" refresher-enabled="true">
				<myhistory v-for="item in 14"></myhistory>
			</scroll-view>
		</view>
</template>

<script>
	export default {
		data() {
			return {

			};
		}
	}
</script>

<style lang="scss">
	.historyBox{
		width: 662rpx;
		height:1300rpx;
		position: relative;
		top: 100rpx;
		left: 44rpx;
		display: flex;
		justify-content: center;
		align-items: center;
		image{
			width: 100%;
			height: 100%;
			position: absolute;
			z-index: -1;
		}
		.temp{
			width: 160rpx;
			height: 26rpx;
			position: absolute;
			z-index: 10;
			left: 16rpx;
			bottom: 10rpx;
		}
		.innerbox{
			width: 592rpx;
			height: 1150rpx;
			position: relative;
			
		}
	}

</style>
