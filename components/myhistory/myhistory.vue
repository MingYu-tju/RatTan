<template>
	<view class="box">
		<image class="back" src="../../static/historyComponent.png"></image>
		<view class="userImg" @click="gotoDetail">
			<image :src="color"></image>
			<image :src="cloth"></image>
		</view>
		<view class="title" @click="gotoDetail">{{this.item.title}}</view>
		<view class="button" @click="deleteMessage">
			<image src="../../static/delete.png"></image>
		</view>
	</view>
</template>

<script>
	//const BaseUrl = "http://172.23.168.70:8080"
	const BaseUrl = "http://101.201.68.134:8199"
	export default {
		name: "myhistory",
		props: {
			item: {
				type: Object,
				default () {
					return {
						messageId: 0,
						title: "默认标题",
						colorId: 1,
						clothId: 1
					}
				}
			}
		},
		data() {
			return {
				color: "",
				cloth: ""
			};
		},
		methods: {
			deleteMessage() {
				uni.showModal({
					content: "确定删除？",
					success: (res) => {
						if (res.confirm) {
							uni.showLoading({
								title: "加载中...",
								mask: true
							})
							uni.request({
								method: "POST",
								url: BaseUrl + "/comment/history/delete",
								header: {
									'content-type': 'application/x-www-form-urlencoded'
								},
								data: {
									messageId: this.item.messageId
								},
								success: (res) => {
									uni.hideLoading()
									if (res.data.success) {
										uni.showToast({
											title: "删除成功！"
										})
										setTimeout(()=>uni.redirectTo({
											url: "/pages/historymessage/historymessage"
										}), 1000)
									} else {
										uni.showToast({
											title: "删除失败！"
										})
									}
								},
								fail: () => {}
							})
						}
					}
				})
			},
			gotoDetail() {
				uni.navigateTo({
					url: `/pages/details/details?cid=${this.item.messageId}`,
					animationType: 'zoom-fade-out',
					animationDuration: 600
				})
			}
		},
		created() {
			this.color = "../../static/color/a" + this.item.colorId + ".gif"
			this.cloth = "../../static/clothes/c" + this.item.clothId + ".png"
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
			font-family: Ipix;
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
