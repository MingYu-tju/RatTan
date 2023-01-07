<template>
	<view>
		<view class="animate__animated animate__fadeInDown">
			<view class="head">
				<view class="me">
					<image src="../../static/test.jpg"></image>
				</view>
				<view class="simple">
					<textarea placeholder="内容概览,15字以内" maxlength="15"></textarea>
				</view>
			</view>
			</view>
			<view class="animate__animated animate__fadeIn">
			<view class="medim">
				<view class="detail">
					<textarea maxlength="150" @input="descInput" v-model="desc" placeholder="详细内容"></textarea>
					<view class="num">{{desc.length}}/150</view>
				</view>
			</view>
			</view>
		
		<view class="animate__animated animate__fadeInUp">
			<button class="send" type="primary">发送</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				desc: ""
			}
		},
		methods: {
			descInput(e) {
				console.log(e.detail.value.length)
			}
		}
	}
</script>

<style lang="scss">
	.head {
		display: flex;
		padding: 60rpx 30rpx;
		justify-content: space-between;
		align-items: center;

		.me {
			width: 150rpx;
			height: 150rpx;
			margin-left: 30rpx;

			image {
				width: 100%;
				height: 100%;
				border-radius: 50%;
			}

		}

		.simple {
			width: 390rpx;
			height: 150rpx;
			font-size: 1.3em;
			border-radius: 30rpx;
			background-color: #55aaff;
			resize: none;
			padding: 20rpx;
			margin-right: 28rpx;
			textarea {
				width: 100%;
			}
		}
	}

	.medim {
		width: 750rpx;
		height: 900rpx;
		padding-top: 30rpx;
		display: flex;
		justify-content: center;
 
		.detail {
			width: 590rpx;
			height: 720rpx;
			background-color: #55aaff;
			resize: none;
			border-radius: 30rpx;
			padding: 20rpx;

			textarea {
				width: 100%;
				height: 97%;
			}

			.num {
				position: absolute;
				right: 80rpx;
				color: gray;
			}
		}
	}

	.send {
		width: 600rpx;
		margin-top: 100rpx;
	}
</style>
