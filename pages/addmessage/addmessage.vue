<template>
	<view class="background">
		<view class="head animate__animated animate__fadeInDown animate__faster">
			<view class="me">
				<image src="../../static/testimage.png"></image>
			</view>
			<view class="simple">
				<textarea placeholder="内容概览,15字以内" maxlength="15"></textarea>
			</view>
		</view>
		<view class="medim animate__animated animate__slideInRight animate__faster">
			<view class="detail">
				<textarea maxlength="150" @input="descInput" v-model="desc" placeholder="详细内容"></textarea>
				<view class="num">{{desc.length}}/150</view>
			</view>
		</view>
		<button class="send animate__animated animate__fadeInUp animate__faster">发送</button>
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
	.background {
		height: 1500rpx;
		// background: #D9D9D9;
	}

	.head {
		display: flex;
		position: relative;
		top: 68rpx;
		padding: 60rpx 30rpx;
		justify-content: space-between;
		align-items: center;

		.me {
			width: 224rpx;
			height: 224rpx;
			margin-left: 30rpx;

			opacity: 1;

			image {
				width: 100%;
				height: 100%;
				border-radius: 29px 29px 29px 29px;
			}

		}

		.simple {
			width: 280rpx;
			height: 120rpx;
			font-size: 1.3em;
			resize: none;
			padding: 20rpx;
			padding-top: 50rpx;
			margin-right: 28rpx;
			background: linear-gradient(88deg, #DDDCDC 0%, #E1E1E1 10%, #EAEAEA 48%, #EBE5E5 93%, #E2DFDF 100%);
			border-radius: 19px 19px 19px 19px;
			opacity: 1;
			border: 4px solid #FFFFFF;

			textarea {
				width: 100%;
			}
		}
	}

	.medim {
		width: 750rpx;
		height: 498rpx;
		padding-top: 30rpx;
		display: flex;
		justify-content: center;
		position: relative;
		top: 126rpx;

		.detail {
			width: 642rpx;
			height: 498rpx;
			resize: none;
			padding: 20rpx;
			background: linear-gradient(90deg, #F1F100 0%, #DFDF00 0%, #F9F93C 6%, #FFFF49 50%, #F9F938 94%, #E4E401 100%);
			border-radius: 29px 29px 29px 29px;
			opacity: 1;
			border: 4px solid #DEDE00;

			textarea {
				width: 100%;
				height: 97%;
			}

			.num {
				position: relative;
				right: 80rpx;
				color: gray;
				bottom: 20rpx;
				left: 550rpx;
			}
		}
	}

	.send {
		width: 492rpx;
		position: relative;
		top: 350rpx;
		background: linear-gradient(90deg, #169393 0%, #158B8B 0%, #19ADAD 28%, #1EBDBD 50%, #1AABAB 74%, #168888 100%);
		border-radius: 19px 19px 19px 19px;
		opacity: 1;
		border: 3px solid #1EBDBD;
	}
</style>
