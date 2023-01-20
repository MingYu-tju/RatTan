<template>
	<view>
		<view class="head">
			<view class="imag">
				<image src="../../static/testimage.png"></image>
			</view>
			<view class="switch">
				<view class="text">
					<text class="choose">Choose</text>
					<text class="favor">your favorite color</text>
				</view>
				<view class="switchBox">
					<view class="switchButton">
						<view class="left">
							<image src="../../static/left.png"></image>
						</view>
						<view class="right">
							<image src="../../static/right.png"></image>
						</view>
					</view>
					<view class="title">切换</view>
				</view>
			</view>
		</view>
		<view class="tail animate__animated animate__slideInUp animate__faster">
			<image class="back" src="../../static/change.png"></image>
			<view class="color">
				<view>红</view>
				<view>灰</view>
				<view>白</view>
				<view>黑</view>
			</view>
			<view class="button">
				<image src="../../static/Frame 14@2x.png"></image>
			</view>
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
	.head {
		width: 750rpx;
		height: 800rpx;

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
			}
		}

		.switch {
			width: 750rpx;
			height: 200rpx;
			position: absolute;
			top: 600rpx;
			display: flex;
			align-items: center;

			.text {
				height: 200rpx;
				flex: 4;
				display: flex;
				flex-direction: column;

				.choose {
					position: absolute;
					top: 30rpx;
					left: 50rpx;
					font-family: Jost-Medium, Jost;
					font-size: 50rpx;
					font-weight: 500;
					background: linear-gradient(92deg, #012777 0%, #19439B 24%, #305DBD 48%, #385FAF 58%, #1A439A 76%, #012777 100%, #012777 100%);
					-webkit-background-clip: text;
					color: transparent;
				}

				.favor {
					position: absolute;
					bottom: 50rpx;
					left: 50rpx;
					font-family: Jost-Medium;
					font-size: 40rpx;
					font-weight: 500;
					color: #000000;
				}
			}

			.switchBox {
				height: 200rpx;
				flex: 3;
				display: flex;
				flex-direction: column;

				.switchButton {
					width: 100%;
					height: 60%;
					display: flex;
					justify-content: center;
					align-items: center;

					.left {
						width: 70rpx;
						height: 70rpx;
						margin: 0 30rpx;

						image {
							width: 100%;
							height: 100%;
						}
					}

					.right {
						width: 70rpx;
						height: 70rpx;
						margin: 0 30rpx;

						image {
							width: 100%;
							height: 100%;
						}
					}
				}

				.title {
					width: 100%;
					height: 40%;
					text-align: center;
					font-size: 40rpx;
					font-weight: 500;
				}
			}
		}
	}

	.tail {
		width: 750rpx;
		height: 703rpx;

		.back {
			width: 100%;
			height: 100%;
			z-index: -1;
			position: absolute;
		}

		.color {
			position: absolute;
			width: 700rpx;
			height: 180rpx;
			top: 220rpx;
			margin: 0 25rpx;
			display: flex;
			justify-content: space-around;

			view {
				width: 150rpx;
				height: 150rpx;
				border-radius: 50%;
				background-color: #FFFFFF;
				font-size: 80rpx;
				font-family: Jost-Black;
				color: #D1D1D1;
				font-weight: 700;
				display: flex;
				justify-content: center;
				align-items: center;
			}
		}

		.button {
			position: absolute;
			bottom: 140rpx;
			left: 185rpx;
			width: 380rpx;
			height: 120rpx;

			image {
				width: 100%;
				height: 100%;
			}
		}
	}
</style>
