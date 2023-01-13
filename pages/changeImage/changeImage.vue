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
				<view class="line"></view>
				<view class="color">
					<view>红</view>
					<view>灰</view>
					<view>白</view>
					<view>黑</view>
				</view>
				<view class="button">确定</view>
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
		width: 738rpx;
		height: 690rpx;
		background: linear-gradient(90deg, #D9D9D9 0%, #E5E5E5 25%, #F1F1F1 50%, #E7E7E7 75%, #D9D9D9 100%);
		border-radius: 60rpx;
		border: 8rpx solid #D1D1D1;

		.line {
			width: 540rpx;
			height: 0;
			position: absolute;
			top: 92rpx;
			margin: 0 105rpx;
			border: 6rpx solid #FFFFFF;
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
			left: 85rpx;
			width: 580rpx;
			height: 100rpx;
			background: linear-gradient(90deg, #169393 0%, #158B8B 0%, #19ADAD 28%, #1EBDBD 50%, #1AABAB 74%, #168888 100%);
			border-radius: 38rpx;
			border: 6rpx solid #1EBDBD;
			display: flex;
			justify-content: center;
			align-items: center;
			font-size: 46rpx;
			font-family: Inter-Medium, Inter;
			font-weight: 500;
			color: #1E2028;
		}
	}
</style>
