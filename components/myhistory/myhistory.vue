<template>
		<view class="box">
			<image class="back" src="../../static/historyComponent.png"></image>
			<view class="userImg">
				<image src="/static/testimage.png"></image>
			</view>
			<view class="title">{{this.title}}</view>
			<view class="button" @click="deleteMessage"><image src="../../static/delete.png"></image></view>
		</view>
</template>

<script>
	export default {
		name: "myhistory",
		data() {
			return {
				title: "测试标题测试标题测试标题测试标题"
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
		width: 592rpx;
		height: 152rpx;
		display: flex;
		align-items: center;
		position: relative;
		margin: 20rpx 0;
		.back {
			width: 100%;
			height: 100%;
			position: absolute;
			z-index: -1;
		}

		.userImg {
			width: 126rpx;
			height: 126rpx;
			position: absolute;
			left: 34rpx;
			image {
				width: 100%;
				height: 100%;
				border-radius: 50%;
			}
		}

		.title {
			width: 270rpx;
			font-weight: 400;
			color: rgba(0, 0, 0, 0.62);
			position: absolute;
			left: 176rpx;
		}

		.button {
			width: 64rpx;
			height: 64rpx;
			position: absolute;
			right: 30rpx;
			image{
				width: 100%;
				height: 100%;
			}
		}
	}
</style>
