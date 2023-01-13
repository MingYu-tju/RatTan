<template>
	<view>
		<view class="back"></view>
		<view class="historyBox">
			<view class="box">
			</view>
		</view>
		<view class="innerbox">
			<myhistory v-for="item in 10"></myhistory>
		</view>
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
	.back {
		position: fixed;
		top: 100rpx;
		left: 60rpx;
		width: 630rpx;
		height: 1188rpx;
		background: #D9D9D9;
		border-radius: 60rpx;
		transform: rotate(-4deg);
	}

	.historyBox {
		width: 630rpx;
		height: 1180rpx;
		position: fixed;
		top: 100rpx;
		left: 60rpx;
		background: linear-gradient(90deg, #EAEAEA 0%, #FFFFFF 43%, #FFFFFF 60%, #E8E8E8 100%);
		border-radius: 60rpx;
		border: 6rpx solid #FFFFFF;

		.box {
			width: 590rpx;
			height: 1100rpx;
			border-radius: 40rpx;
			position: fixed;
			top: 140rpx;
			left: 80rpx;
			border: 6rpx dashed #9747FF;

		}
	}

	.innerbox {
		width: 550rpx;
		height: 1060rpx;
		position: absolute;
		top: 170rpx;
		left: 100rpx;
		display: flex;
		flex-direction: column;
		align-items: center;
		overflow: auto;
	}
</style>
