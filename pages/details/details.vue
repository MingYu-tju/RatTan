<template>
	<view>
		<view class="box">
			<image src="../../static/detailBack.png" class="back"></image>
			<image src="../../static/water.gif" class="water"></image>
			<image src="../../static/marshroom2.gif" class="marshroom2"></image>
			<z-swiper class="all" v-model="list" :options="options" @slideChange="onChange">
				<image src="../../static/marshroom1.gif" class="marshroom1"></image>
				<z-swiper-item v-for="(item,index) in list" :key="index">
					<view v-if="show==index||show==(index+1)||show==(index-1)">
						<view class="detailBox">
							<image src="../../static/buble.png" class="buble"></image>
							<view class="detail">{{item.Message}}</view>
						</view>

						<view class="img">
							<image :src="item.color"></image>
							<image :src="item.cloth"></image>
						</view>
					</view>
				</z-swiper-item>
			</z-swiper>
			<view class="button" @click="reSend" hover-class="hoverButton" hover-stay-time="100" hover-start-time="0">
				<image src="../../static/normal.png"></image><text>说点什么...</text>
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
				show: 0,
				options: {
					initialSlide: 0,
					effect: 'creative',
					creativeEffect: {
						prev: {
							shadow: true,
							translate: ['-100%', '-20%', -1600],
						},
						next: {
							translate: ['100%', 80, 1000]
						}
					}
				},
				list: [{
						Message: `留言5`,
						color: "../../static/color/black.png",
						cloth: "../../static/clothes/c7.png"
					},
					{
						Message: `留言4`,
						color: "../../static/color/grey.png",
						cloth: "../../static/clothes/c6.png"
					},
					{
						Message: `留言3`,
						color: "../../static/color/white.png",
						cloth: "../../static/clothes/c5.png"
					},
					{
						Message: `留言2`,
						color: "../../static/color/red.png",
						cloth: "../../static/clothes/c4.png"
					},
					{
						Message: `留言1`,
						color: "../../static/color/white.png",
						cloth: "../../static/clothes/c3.png"
					},
					{
						Message: `此页为消息详细内容，后续右滑为此消息的留言，回复可为该条消息留言`,
						color: "../../static/color/grey.png",
						cloth: "../../static/clothes/c1.png"
					}
				]
			};
		},
		onLoad(e) {
			this.uId = e.cid
			this.options.initialSlide = this.list.length
			this.show = this.list.length
		},
		methods: {
			reSend() {

			},
			onChange(swiper, index) {
				this.show = index
			}
		}
	}
</script>

<style lang="scss">
	.back {
		z-index: 0;
		width: 750rpx;
		height: 1500rpx;
		position: fixed;
	}

	.water {
		width: 750rpx;
		height: 1500rpx;
		z-index: 0;
		position: fixed;
	}

	.marshroom1 {
		width: 750rpx;
		height: 1500rpx;
		position: absolute;
		z-index: 3;
	}


	.marshroom2 {
		width: 750rpx;
		height: 1500rpx;
		z-index: 0;
		position: fixed;
		right: 0;
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

			.detailBox {
				width: 618rpx;
				height: 620rpx;
				position: absolute;
				top: 140rpx;
				left: 66rpx;
				display: flex;
				justify-content: center;

				.detail {
					width: 570rpx;
					height: 400rpx;
					font-family: Ipix;
					font-size: 35rpx;
					position: relative;
					top: 50rpx;
				}

				.buble {
					width: 100%;
					height: 100%;
					position: absolute;
					z-index: -1;
				}
			}

			.img {
				width: 460rpx;
				height: 520rpx;
				position: absolute;
				left: 160rpx;
				bottom: 200rpx;

				image {
					width: 100%;
					height: 100%;
					position: absolute;
				}
			}
		}

		.button {
			z-index: 2;
			position: absolute;
			right: 80rpx;
			bottom: 80rpx;
			width: 400rpx;
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

	.hoverButton {
		opacity: 0.9;
		transform: scale(0.95, 0.95);
	}
</style>
