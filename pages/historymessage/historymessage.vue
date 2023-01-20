<template>
		<view class="historyBox">
			<image src="../../static/historyBack.png"></image>
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
		.innerbox{
			width: 592rpx;
			height: 1150rpx;
			position: relative;
			
		}
	}

</style>
