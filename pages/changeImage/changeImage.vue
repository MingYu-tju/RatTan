<template>
	<view>
		<view class="head">
			<view class="text1">倾情呈现！定制你的鼠鼠!</view>
			<view class="text2">Behold! Your OWN Rat!</view>
			<view class="imag">
				<image :src="color" class="animate__animated animate__fadeIn" :key="test1"></image>
				<image :src="cloth" class="animate__animated animate__fadeIn" :key="test2"></image>
			</view>
			<view class="switch">
				<view class="color">
					<view @click="changeColor('red',1)" class="c1" hover-class="hoverButton" hover-stay-time="200" hover-start-time="0">
						<image v-if="selectedColor==1" src="../../static/left.png"></image>
					</view>
					<view @click="changeColor('grey',2)" class="c2" hover-class="hoverButton" hover-stay-time="200" hover-start-time="0">
						<image v-if="selectedColor==2" src="../../static/left.png"></image>
					</view>
					<view @click="changeColor('white',3)" class="c3" hover-class="hoverButton" hover-stay-time="200" hover-start-time="0">
						<image v-if="selectedColor==3" src="../../static/left.png"></image>
					</view>
					<view @click="changeColor('black',4)" class="c4" hover-class="hoverButton" hover-stay-time="200" hover-start-time="0">
						<image v-if="selectedColor==4" src="../../static/left.png"></image>
					</view>
				</view>
			</view>
		</view>
		<view class="tail animate__animated animate__slideInUp animate__faster">
			<image class="back" src="../../static/change.png"></image>
			<view class="text3">customize it</view>
			<view class="selectCloth">
				<view @click="changeCloth(1)" hover-class="hoverButton" hover-stay-time="200" hover-start-time="0">
					<view v-if="selectedCloth==1" class="selected"></view>
					<view class="clothName">草莓蛋糕</view>
				</view>
				<view @click="changeCloth(2)" hover-class="hoverButton" hover-stay-time="200" hover-start-time="0">
					<view v-if="selectedCloth==2" class="selected"></view>
					<view class="clothName">沙滩游鼠</view>
				</view>
				<view @click="changeCloth(3)" hover-class="hoverButton" hover-stay-time="200" hover-start-time="0">
					<view v-if="selectedCloth==3" class="selected"></view>
					<view class="clothName">古希腊鼠</view>
				</view>
				<view @click="changeCloth(4)" hover-class="hoverButton" hover-stay-time="200" hover-start-time="0">
					<view v-if="selectedCloth==4" class="selected"></view>
					<view class="clothName">西域舞鼠</view>
				</view>
				<view @click="changeCloth(5)" hover-class="hoverButton" hover-stay-time="200" hover-start-time="0">
					<view v-if="selectedCloth==5" class="selected"></view>
					<view class="clothName">小叮当鼠</view>
				</view>
				<view @click="changeCloth(6)" hover-class="hoverButton" hover-stay-time="200" hover-start-time="0">
					<view v-if="selectedCloth==6" class="selected"></view>
					<view class="clothName">梅里达鼠</view>
				</view>
				<view @click="changeCloth(7)" hover-class="hoverButton" hover-stay-time="200" hover-start-time="0">
					<view v-if="selectedCloth==7" class="selected"></view>
					<view class="clothName">鼠利波特</view>
				</view>
				<view @click="changeCloth(8)" hover-class="hoverButton" hover-stay-time="200" hover-start-time="0">
					<view v-if="selectedCloth==8" class="selected"></view>
					<view class="clothName">三明治鼠</view>
				</view>
				<view @click="changeCloth(9)" hover-class="hoverButton" hover-stay-time="200" hover-start-time="0">
					<view v-if="selectedCloth==9" class="selected"></view>
					<view class="clothName">西兰花鼠</view>
				</view>
				<view @click="changeCloth(10)" hover-class="hoverButton" hover-stay-time="200" hover-start-time="0">
					<view v-if="selectedCloth==10" class="selected"></view>
					<view class="clothName">上班鼠鼠</view>
				</view>
				<view @click="changeCloth(11)" hover-class="hoverButton" hover-stay-time="200" hover-start-time="0">
					<view v-if="selectedCloth==11" class="selected"></view>
					<view class="clothName">云宝黛鼠</view>
				</view>
				<view @click="changeCloth(12)" hover-class="hoverButton" hover-stay-time="200" hover-start-time="0">
					<view v-if="selectedCloth==12" class="selected"></view>
					<view class="clothName">曼联鼠鼠</view>
				</view>
				<view @click="changeCloth(13)" hover-class="hoverButton" hover-stay-time="200" hover-start-time="0">
					<view v-if="selectedCloth==13" class="selected"></view>
					<view class="clothName">夏威夷鼠</view>
				</view>
				<view @click="changeCloth(14)" hover-class="hoverButton" hover-stay-time="200" hover-start-time="0">
					<view v-if="selectedCloth==14" class="selected"></view>
					<view class="clothName">摇滚鼠鼠</view>
				</view>
				<view @click="changeCloth(15)" hover-class="hoverButton" hover-stay-time="200" hover-start-time="0">
					<view v-if="selectedCloth==15" class="selected"></view>
					<view class="clothName">鼠气东来</view>
				</view>
				<view @click="changeCloth(16)" hover-class="hoverButton" hover-stay-time="200" hover-start-time="0">
					<view v-if="selectedCloth==16" class="selected"></view>
					<view class="clothName">黄金鼠条</view>
				</view>
				<view @click="changeCloth(17)" hover-class="hoverButton" hover-stay-time="200" hover-start-time="0">
					<view v-if="selectedCloth==17" class="selected"></view>
					<view class="clothName">绿帽小子</view>
				</view>
				<view @click="changeCloth(18)" hover-class="hoverButton" hover-stay-time="200" hover-start-time="0">
					<view v-if="selectedCloth==18" class="selected"></view>
					<view class="clothName">斯坦麻鼠</view>
				</view>
				<view @click="changeCloth(19)" hover-class="hoverButton" hover-stay-time="200" hover-start-time="0">
					<view v-if="selectedCloth==19" class="selected"></view>
					<view class="clothName">初音未来</view>
				</view>
				<view @click="changeCloth(20)" hover-class="hoverButton" hover-stay-time="200" hover-start-time="0">
					<view v-if="selectedCloth==20" class="selected"></view>
					<view class="clothName">V 我50</view>
				</view>

			</view>
			<view class="button" @click="submit" hover-class="hoverButton" hover-stay-time="100" hover-start-time="0">
				<image src="../../static/Frame 14@2x.png"></image>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				color: "",
				cloth: "",
				selectedColor: 0,
				selectedCloth: 0,
				test1: null,
				test2: null,
				activeClass: "animate__animated animate__flipInY animate__faster"
			};
		},
		methods: {
			changeColor(e, a) {
				//getApp().globalData.userColor = "../../static/color/" + e + ".png"
				if (this.selectedColor != a) {
					this.color = "../../static/color/" + e + ".png"
					this.selectedColor = a
					this.test1 = Math.random()
				}
			},
			changeCloth(e) {
				if (this.selectedCloth != e) {
					this.cloth = "../../static/clothes/c" + e + ".png"
					this.selectedCloth = e
					this.test2 = Math.random()
				}
			},
			submit() { //请求部分
				getApp().globalData.userColor = this.color
				getApp().globalData.userCloth = this.cloth
				getApp().globalData.colorId = this.selectedColor
				getApp().globalData.clothId = this.selectedCloth
				uni.switchTab({
					url: "/pages/index/index"
				})
			}
		},
		onLoad() {
			this.selectedColor = getApp().globalData.colorId
			this.selectedCloth = getApp().globalData.clothId
			this.color = getApp().globalData.userColor
			this.cloth = getApp().globalData.userCloth
		}
	}
</script>

<style lang="scss">
	.head {
		width: 750rpx;
		height: 800rpx;

		.text1 {
			text-align: center;
			font-size: 45rpx;
		}

		.text2 {
			text-align: center;
			color: #B2ABA5;
			font-size: 45rpx;
		}

		.imag {
			width: 750rpx;
			height: 480rpx;
			position: absolute;
			top: 120rpx;
			display: flex;
			justify-content: center;

			image {
				width: 480rpx;
				height: 480rpx;
				position: absolute;
			}

		}

		.switch {
			width: 750rpx;
			height: 200rpx;
			position: absolute;
			top: 600rpx;

			.color {
				position: absolute;
				width: 700rpx;
				height: 180rpx;
				margin: 0 25rpx;
				display: flex;
				justify-content: space-around;

				view {
					width: 150rpx;
					height: 150rpx;
					border-radius: 50%;
					background-color: #FFFFFF;
					display: flex;
					justify-content: center;
					align-items: center;
					border: 12rpx solid gainsboro;

					image {
						width: 100rpx;
						height: 100rpx;
						border-radius: 50%;
						position: absolute;
						z-index: 0;
					}
				}

				.c1 {
					background-color: #B6442A;
				}

				.c2 {
					background-color: #FCC898;
				}

				.c4 {
					background-color: #4B4B4B;
				}
			}
		}
	}

	.tail {
		width: 750rpx;
		height: 703rpx;
		display: flex;
		justify-content: center;

		.text3 {
			font-size: 40rpx;
			color: #7B555D;
			position: absolute;
			left: 80rpx;
			top: 18rpx;
		}

		.back {
			width: 100%;
			height: 100%;
			z-index: -1;
			position: absolute;
		}

		.selectCloth {
			width: 670rpx;
			height: 370rpx;
			position: absolute;
			top: 130rpx;
			display: flex;
			flex-wrap: wrap;
			overflow: auto;

			view {
				width: 150rpx;
				height: 150rpx;
				background-color: #FFFFFF;
				border-radius: 50%;
				margin: 10rpx;
				position: relative;
				display: flex;
				justify-content: center;
				align-items: center;

				.clothName {
					width: 70%;
					height: 70%;
					color: #B1ACA9;
					font-size: 38rpx;
					font-weight: 500;
					text-align: center;
				}

				.selected {
					width: 100%;
					height: 100%;
					border: 10rpx solid #094827;
					position: absolute;
					z-index: -1;
				}
			}
		}

		.button {
			position: absolute;
			bottom: 80rpx;
			left: 185rpx;
			width: 380rpx;
			height: 120rpx;

			image {
				width: 100%;
				height: 100%;
			}
		}

		.hoverButton {
			transform: scale(0.95, 0.95);
		}
	}
</style>
