<template>
	<view>
		<view class="box">
			<view class="userImg">
				<image src="../../static/testimage.png"></image>
			</view>
			<view class="title">{{this.title}}</view>
			<view class="button" @click="deleteMessage"><text>删除</text></view>
		</view>
	</view>
</template>

<script>
	export default {
		name: "myhistory",
		data() {
			return {
				title: "这是测试标题这是测试标题测试标"
			};
		},
		methods: {
			deleteMessage() {

			}
		}
	}
</script>

<style lang="scss">
	.box {
		width: 540rpx;
		height: 140rpx;
		margin: 40rpx 0;
		background: linear-gradient(180deg, #969290 0%, #D1D1D1 25%, #D1D1D1 74%, #94908E 100%);
		display: flex;
		justify-content: space-around;
		align-items: center;
		border-radius: 40rpx;

		.userImg {
			width: 124rpx;
			height: 124rpx;

			image {
				width: 100%;
				height: 100%;
				border-radius: 50%;
			}
		}

		.title {
			width: 270rpx;
			font-family: Jost-Regular, Jost;
			font-weight: 400;
			color: rgba(0, 0, 0, 0.62);
		}

		.button {
			width: 76rpx;
			height: 48rpx;
			font-size: 30rpx;
			font-family: Jost-Regular, Jost;
			font-weight: 400;
			color: #000000;
			line-height: 28rpx;
			background: linear-gradient(90deg, #E2E207 0%, #FFFF71 30%, #FFFF71 71%, #E2E207 100%);
			box-shadow: 8rpx 0 8rpx 0 rgba(0, 0, 0, 0.2);
			border-radius: 20rpx;
			border: 4rpx solid #E3E300;
			display: flex;
			justify-content: center;
			align-items: center;
		}
	}
</style>
