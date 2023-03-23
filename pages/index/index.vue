<template>
	<view class="ground">
			<image class="back" src="/static/background1.png"></image>
			<view class="hist">
				<view class="history" @click="gotoHistoryPage" hover-class="hoverButton" hover-stay-time="100"
					hover-start-time="0">
					<image src="../../static/history.png"></image>
				</view>
			</view>

			<view class="tubebox">
				<view class="tube tube1">
					<showMessage v-if="show1"></showMessage>
				</view>
				<view class="tube tube2">
					<showMessage v-if="show2" pos="right"></showMessage>
				</view>
				<view class="tube tube3">
					<showMessage v-if="show3"></showMessage>
				</view>
				<view class="tube tube4">
					<showMessage v-if="show4" pos="right"></showMessage>
				</view>
				<view class="tube tube5">
					<showMessage v-if="show5"></showMessage>
				</view>
				<view class="tube tube6">
					<showMessage v-if="show6"></showMessage>
				</view>
				<view class="tube tube7">
					<showMessage v-if="show7" pos="right"></showMessage>
				</view>
			</view>
			<view class="tail">
				<view class="custom" @click="gotoChangeImgPage" hover-class="hoverButton" hover-stay-time="100"
					hover-start-time="0">				
					<image :src="color" v-if="showImg"></image>
					<image :src="cloth" v-if="showImg"></image>
					<view v-if="!showImg">未登录</view>				
				</view>
				<view class="addButton" hover-class="hoverButton" hover-stay-time="100" hover-start-time="0">
					<image src="../../static/send.png" @click="gotoAddMessagePage"></image>
				</view>
			</view>
	</view>
</template>

<script>
	//const BaseUrl ="http://172.23.168.70:8080"
	const BaseUrl = "http://101.201.68.134:8199"
	export default {
		data() {
			return {
				show1: 0,
				show2: 0,
				show3: 0,
				show4: 0,
				show5: 0,
				show6: 0,
				show7: 0,
				showImg: false,
				color: "",
				cloth: ""
			}
		},
		methods: {
			gotoHistoryPage() {		//历史记录按钮
				if (getApp().globalData.login) 		//检查登陆状态，未登录跳转login页面
					uni.navigateTo({
						url: "../historymessage/historymessage",
						animationType: 'slide-in-top',			//动画
						animationDuration: 600
					})
				else {
					uni.switchTab({
						url: "/pages/login/login"
					})
				}
			},
			gotoAddMessagePage() {		//发言按钮
				if (getApp().globalData.login)		//检查登陆状态
					uni.navigateTo({
						url: "/pages/addmessage/addmessage",
						animationType: 'zoom-fade-out',
						animationDuration: 400
					})
				else {
					uni.switchTab({
						url: "/pages/login/login",
					})
				}
			},
			gotoChangeImgPage() {		//换装按钮
				if (getApp().globalData.login)		//检查登陆状态
					uni.navigateTo({
						url: "/pages/changeImage/changeImage",
						animationType: 'slide-in-bottom',
						animationDuration: 600
					})
				else {
					uni.switchTab({
						url: "/pages/login/login"
					})
				}
			},
			tube1() { 	//生成showMessage组件并展示15秒，错开生成时间看起来有随机出现的效果，js单线程，不知道怎么实现真随机出现
				this.show1 = 1
				setTimeout(e => this.show1 = 0, 15000)
			},
			tube2() {
				setTimeout(e => {
					this.show2 = 1
					setTimeout(e => this.show2 = 0, 15000)
				}, 5000)
			},
			tube3() {
				setTimeout(e => {
					this.show3 = 1
					setTimeout(e => this.show3 = 0, 15000)
				}, 8000)
			},
			tube4() {
				setTimeout(e => {
					this.show4 = 1
					setTimeout(e => this.show4 = 0, 15000)
				}, 13000)
			},
			tube5() {
				setTimeout(e => {
					this.show5 = 1
					setTimeout(e => this.show5 = 0, 15000)
				}, 17000)
			},
			tube6() {
				setTimeout(e => {
					this.show6 = 1
					setTimeout(e => this.show6 = 0, 15000)
				}, 19000)
			},
			tube7() {
				setTimeout(e => {
					this.show7 = 1
					setTimeout(e => this.show7 = 0, 15000)
				}, 22000)
			}
		},
		onLoad() {
			this.tube1() //进入页面先生成一次
			this.tube2()
			this.tube3()
			this.tube4()
			this.tube5()
			this.tube6()
			this.tube7()
			setInterval(this.tube1, 30000)
			setInterval(this.tube2, 25000)
			setInterval(this.tube3, 25000)
			setInterval(this.tube4, 25000)
			setInterval(this.tube5, 25000)
			setInterval(this.tube6, 25000)
			setInterval(this.tube7, 25000)
		},
		onShow() {
			if (getApp().globalData.login)
				this.showImg = true
			else {
				this.showImg = false
			}
			this.color = getApp().globalData.userColor
			this.cloth = getApp().globalData.userCloth
		}
	}
</script>

<style lang="scss">
	.ground {
		width: 750rpx;
		height: 1395rpx;
			.back {
				position: absolute;
				width: 100%;
				height: 100%;
				top: 0;
			}
	}

	.hist {
		width: 750rpx;
		height: 140rpx;
		position: fixed;
		top: var(--window-top);
		display: flex;
		justify-content: center;
		align-items: center;
		z-index: 3;
		.history {
			width: 100rpx;
			height: 100rpx;
			position: absolute;
			right: 30rpx;

			image {
				width: 100%;
				height: 100%;
			}
		}
	}

	.tubebox {
		width: 100%;
		height: 100%;
		position: absolute;

		.tube {
			width: 140rpx;
			height: 140rpx;
			position: absolute;
			border-radius: 50%;
		}

		.tube1 {
			top: 375rpx;
			left: 24rpx;
		}

		.tube2 {
			top: 380rpx;
			right: 18rpx;
		}

		.tube3 {
			left: 236rpx;
			top: 495rpx;
		}

		.tube4 {
			top: 617rpx;
			right: 18rpx;
		}

		.tube5 {
			left: 90rpx;
			top: 731rpx;
		}

		.tube6 {
			left: 310rpx;
			bottom: 420rpx;
		}

		.tube7 {
			right: 90rpx;
			bottom: 540rpx;
		}
	}

	.tail {
		width: 750rpx;
		height: 300rpx;
		position: fixed;
		bottom: var(--window-bottom);
		display: flex;
		justify-content: center;
		bottom: 30rpx;

		.custom {
			width: 250rpx;
			height: 250rpx;
			position: absolute;
			left: 100rpx;
			top: 0;
			border: 3px solid #BDC6C3;
			background-color: #e2ece9;
			border-radius: 60rpx;

			image {
				width: 100%;
				height: 100%;
				position: absolute;
			}

			view {
				width: 100%;
				height: 100%;
				display: flex;
				justify-content: center;
				align-items: center;
				font-size: 80rpx;
				font-family: Ipix;
				font-weight: 500;
			}
		}

		.addButton {
			width: 160rpx;
			height: 160rpx;
			position: absolute;
			right: 100rpx;
			top: 50rpx;

			image {
				width: 100%;
				height: 100%;
			}
		}
	}

	.hoverButton {
		opacity: 0.9;
		transform: scale(0.95, 0.95);
	}
</style>
