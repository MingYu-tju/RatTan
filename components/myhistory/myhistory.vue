<template>
	<view class="box" @click="gotoDetail">
		<image class="back" src="../../static/historyComponent.png"></image>
		<view class="userImg">
			<image :src="color"></image>
			<image :src="cloth"></image>
		</view>
		<view class="title">{{this.title}}</view>
		<view class="button" @click="deleteMessage">
			<image src="../../static/delete.png"></image>
		</view>
	</view>
</template>

<script>
	const BaseUrl = "http://101.201.68.134:8199"
	export default {
		name: "myhistory",
		data() {
			return {
				messageId: 0,
				title: "测试标题测试标题测试标题测试标题",
				color: "",
				cloth: ""
			};
		},
		methods: { //接口未完成
			deleteMessage() {
				uni.showLoading({
					title: "加载中...",
					mask: true
				})
				uni.request({
					method: "POST",
					url: BaseUrl + "/comment/history/del",
					data: {
						messageId: this.messageId
					},
					success: (res) => {
						uni.hideLoading()
						if (res.data.success) {
							uni.showToast({
								title: "删除成功！"
							})
						} else {
							uni.showToast({
								title: "删除失败！"
							})
						}
					},
					fail: () => {}
				})
			},
			gotoDetail() {
				uni.navigateTo({
					url: `/pages/details/details?cid=${this.messageId}`,
					animationType: 'zoom-fade-out',
					animationDuration: 600
				})
			}
		},
		created() { //接口未完成
			uni.request({
				method: "POST",
				url: BaseUrl + "comment/history",
				data: {
					userName: getApp().globalData.userName
				},
				success: (res) => {
					this.messageId = res.data.massageId
					rhis.title = res.data.title
					this.color = "../../static/color.a" + res.data.colorId + ".png"
					this.cloth = "../../static/clothed.c" + res.data.clothId + ".png"
				}
			})
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
				position: absolute;
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

			image {
				width: 100%;
				height: 100%;
			}
		}
	}
</style>
