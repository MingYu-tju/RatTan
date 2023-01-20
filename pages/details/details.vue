<template>
	<view>
		<view class="box">
			<z-swiper class="all" v-model="list" :options="options">
				<z-swiper-item v-for="(item,index) in list" :key="index">
					<view class="detailBox">
						<view class="detail">{{item}}</view>
					</view>
					<view class="buble">
						<image src="../../static/buble.png"></image>
					</view>
					<view class="img">
						<image src="../../static/testimage.png"></image>
					</view>
				</z-swiper-item>
			</z-swiper>
			<view class="button" @click="reSend">
				<image src="../../static/normal.png"></image><text>回复</text>
			</view>
		</view>
	</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				uId: null,
				num: 0,
				options: {
					initialSlide: 0,
					effect: 'creative',
					creativeEffect: {
						prev: {
							shadow: true,
							translate: ['-70%', '-20%', -1000],
						},
						next: {
							translate: ['100%', 80, 1000]
						}
					}
				},
				list: [
					`留言5`,
					`留言4`,
					`留言3`,
					`留言2`,
					`留言1`,
					`此页为消息详细内容，后续右滑为此消息的留言，回复可为该条消息留言`
				]
			};
		},
		onLoad(e) {
			this.uId = e.cid
			this.options.initialSlide = this.list.length
		},
		methods: {
			reSend() {
				console.log("27364")
			}
		}
	}
</script>

<style lang="scss">
	.buble {
		width: 152rpx;
		height: 75rpx;
		position: fixed;
		left: 300rpx;
		top: 660.5rpx;

		image {
			width: 100%;
			height: 100%;
		}
	}

	.box {
		width: 750rpx;
		height: 1500rpx;
		background: #e4e4e4;
		position: relative;

		.all {
			width: 750rpx;
			height: 1500rpx;
			position: relative;
			initialSlide: 4;

			.detailBox {
				width: 618rpx;
				height: 516rpx;
				position: absolute;
				top: 140rpx;
				left: 66rpx;
				background: #FFFFFF;
				border: 8rpx solid #F5F5F5;
				border-radius: 40rpx;
				display: flex;
				justify-content: center;
				align-items: center;

				.detail {
					width: 570rpx;
					height: 400rpx;
					font-family: Ipix;
					font-size: 35rpx;
				}
			}

			.img {
				width: 460rpx;
				height: 520rpx;
				position: absolute;
				left: 65rpx;
				bottom: 200rpx;

				image {
					width: 100%;
					height: 100%;
				}
			}
		}

		.button {
			z-index: 2;
			position: absolute;
			right: 80rpx;
			bottom: 80rpx;
			width: 184rpx;
			height: 96rpx;
			font-size: 38rpx;
			font-family: Ipix;
			font-weight: 500;
			color: #000000;
			line-height: 28rpx;
			display: flex;
			justify-content: center;
			align-items: center;

			image {
				width: 100%;
				height: 100%;
				position: absolute;
				z-index: -1;
			}
		}
	}
</style>
