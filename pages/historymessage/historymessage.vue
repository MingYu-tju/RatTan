<template>
	<view class="historyBox">
		<image src="../../static/historyBack.png"></image>
		<image src="../../static/Frame 16.png" class="temp"></image>
		<scroll-view class="innerbox" scroll-y="true" refresher-enabled="true" @refresherrefresh="refresh">
			<myhistory v-for="item in length"></myhistory>
		</scroll-view>
	</view>
</template>

<script>
	const BaseUrl = "http://101.201.68.134:8199"
	export default {
		data() {
			return {
				length: 0
			};
		},
		methods: {
			onload() {
				uni.showLoading({
					title: "加载中...",
					mask: true
				})
				uni.request({
					method: "POST",
					url: BaseUrl + "comment/history",
					success: (res) => {
						this.length = res.data.length
						uni.hideLoading()
					}
				})
			},
			refresh() {
				uni.redirectTo({
					url: "/pages/historymessage/historymessage"
				})
			}
		}
	}
</script>

<style lang="scss">
	.historyBox {
		width: 662rpx;
		height: 1300rpx;
		position: relative;
		top: 100rpx;
		left: 44rpx;
		display: flex;
		justify-content: center;
		align-items: center;

		image {
			width: 100%;
			height: 100%;
			position: absolute;
			z-index: -1;
		}

		.temp {
			width: 160rpx;
			height: 26rpx;
			position: absolute;
			z-index: 10;
			left: 16rpx;
			bottom: 10rpx;
		}

		.innerbox {
			width: 592rpx;
			height: 1150rpx;
			position: relative;

		}
	}
</style>
