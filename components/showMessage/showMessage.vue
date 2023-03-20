<template>
	<view :class="activeclass" @click="gotoDetailsPage">
		<view class="showBox">
			<view :style="showTitle" hover-class="hoverButton" hover-stay-time="100" hover-start-time="0">
				<image :src="activeBubble" class="bubble"></image>
				<view class="title">{{title}}</view>
			</view>
			<view class="userimg" hover-class="hoverButton" hover-stay-time="100" hover-start-time="0">
				<image :src="color"></image>
				<image :src="cloth"></image>
			</view>
		</view>
	</view>
</template>

<script>
	const BaseUrl ="http://101.201.68.134:8199"
	export default {
		name: "showMessage",
		props: {
			pos: {
				type: String,
			}
		},
		data() {
			return {
				activeclass: "animate__animated animate__bounceIn",
				title: "测试标题测试标题测试标题测试标题",
				color: "../../static/color/a2.png",
				cloth: "../../static/clothes/c2.png",
				messageId: "",
				activeBubble: "../../static/tBubble1.png",
				showTitle: {
					'width': '280rpx',
					'height': '130rpx',
					'position': 'absolute',
					'bottom': '160rpx',
					'left': '0',
					'overflow': 'hidden',
					'text-overflow': 'ellipsis',
					'font-family': 'Ipix',
					'font-size': '28rpx'
				}
			};
		},
		created() {
			if (this.pos == "right") { //防止标题框超出屏幕
				this.showTitle.left = "-160rpx"
				this.activeBubble = "../../static/tBubble2.png"
			}
			uni.request({ //接口未完成
				method: "POST",
				url: BaseUrl+"/comment/all",
				success: res => {
					
					
					//接口可调用时删去注释
					this.color = "../../static/color/a" + res.data.clothId + ".png"
				    this.cloth = "../../static/clothes/c" + res.data.colorId + ".png"
					this.title = res.data.title
					
					
					this.messageId = res.data.messageId
					setTimeout(e => {
						this.activeclass = "animate__animated animate__bounceOut"
					}, 14200)
				},
				fail: () => {
				}
			})
		},

		methods: {
			gotoDetailsPage() {
				if (getApp().globalData.login)
					uni.navigateTo({
						url: `/pages/details/details?cid=${this.messageId}`,
						animationType: 'zoom-fade-out',
						animationDuration: 600
					})
				else {
					uni.switchTab({
						url: "/pages/login/login"
					})
				}
			}
		}
	}
</script>

<style lang="scss">
	.showBox {
		width: 140rpx;
		height: 140rpx;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.userimg {
		width: 100%;
		height: 100%;
		border-radius: 50%;
		position: relative;

		image {
			width: 100%;
			height: 100%;
			position: absolute;
		}
	}

	.bubble {
		width: 100%;
		height: 100%;
		position: absolute;
		z-index: -1;
	}

	.title {
		width: 80%;
		position: absolute;
		top: 20rpx;
		left: 25rpx;
	}

	.hoverButton {
		opacity: 0.9;
		transform: scale(0.95, 0.95);
	}
</style>
