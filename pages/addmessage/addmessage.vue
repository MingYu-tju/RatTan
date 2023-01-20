<template>
	<view class="body">
		<image class="back" src="../../static/addMessage.png"></image>
		<view :style="titleStyle">{{title}}</view>
		<view class="head">
			<view  :class="activeclass1">
				<image src="../../static/765675.png" class="jia"></image>
				<image src="../../static/testimage.png"></image>
			</view>
			<view :class="activeclass2">
				<image src="../../static/Frame 17@2x.png"></image>
				<view class="simple">
					<input placeholder="Title" maxlength="16" @input="backText"></input>
				</view>
				<view class="detail">
					<textarea maxlength="150"  v-model="desc" placeholder="详细内容"></textarea>
					<view class="num">{{desc.length}}/150</view>
				</view>
			</view>
		</view>

		<view class="send animate__animated animate__fadeIn" @click="send"><image src="../../static/sendMessage.png"></image></view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				desc: "",
				activeclass1: "",
				activeclass2:"",
				title:"福报",
				titleStyle:{
					'width': '600rpx',
					'position': 'absolute',
					'z-index': '-1',
					'font-size': '260rpx',
					'font-family': 'Ipix',
					'white-space': 'pre-wrap',
					'top': '200rpx',
					'left':'110rpx',
					'color':'green'
				}
			}
		},
		methods: {
			backText(e) {
				this.titleStyle['font-size']="75rpx"
				this.titleStyle['top']="300rpx"
				this.title=e.detail.value
			},
			send() {
				uni.showModal({
					success: (res) => {
						if (res.confirm) {
							this.activeclass1 = "me animate__animated animate__bounceOutUp animate__fast"//动画部分，别在意
							setTimeout(()=>this.activeclass2 = "message animate__animated animate__fadeOutUp animate__faster",400)
							setTimeout(()=>uni.switchTab({
								url:"/pages/index/index"
							}),700)
						}
					},
					content: "确定发送？"
				})
			}
		},
		onLoad() {
			this.activeclass1 = "me animate__animated animate__bounceInDown animate__fast"//动画部分，别在意
			this.activeclass2 = "message animate__animated animate__fadeInDown animate__faster"
		}
	}
</script>

<style lang="scss">
	.body {
		.back {
			position: absolute;
			width: 750rpx;
			height: 1503rpx;
			z-index: -2;
		}

	}

	.head {
		display: flex;
		flex-direction: column;
		align-items: center;
		position: relative;
		.me {
			width: 250rpx;
			height: 360rpx;
			position: relative;

			image {
				width: 230rpx;
				height: 230rpx;
				position: absolute;
				bottom: 0;
				left: 8rpx;
			}

			.jia {
				width: 100%;
				height: 100%;
			}
		}

		.message {
			position: relative;
			top: 110rpx;
			
			image{
				z-index: -1;
				position: absolute;
				width: 100%;
				height: 100%;
			}
			.simple {
				width: 625rpx;
				height: 80rpx;
				margin-top: 50rpx;
				display: flex;
				justify-content: center;
				align-items: center;
				
				input {
					width: 565rpx;
					height: 60rpx;
					font-size: 35rpx;
					font-weight: 600rpx;
					font-family: Ipix;
					align-items: center;
					border-bottom: 6rpx solid #e2e2e2;
				}
			}

			.detail {
				width: 625rpx;
				height: 600rpx;
				display: flex;
				justify-content: center;
				align-items: center;
				
				textarea {
			
					width: 565rpx;
					height: 540rpx;
					font-family: Ipix;
				}

				.num {
					position: absolute;
					bottom: 0;
					right: 20rpx;
				}
			}

		}
	}

	.send {
		width: 380rpx;
		height: 118rpx;
		position: absolute;
		left: 185rpx;
		bottom: 140rpx;
		image{
			width: 100%;
			height: 100%;
		}
	}
</style>
