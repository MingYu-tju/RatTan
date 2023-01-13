<template>
	<view class="body">
		<view class="animate__animated animate__slideInRight animate__fast" :key="Key" v-if="show">
			<text>您好,
				请登陆后查看完整内容</text>
		</view>
		<view class="log">
			<view class="animate__animated animate__slideInUp animate__fast" :key="Key" v-if="show">
				<view class="form">

					<view class="input-text">
						<view class="title">用户名</view>
						<input type="text" class="userName" placeholder="请输入用户名" placeholder-class="plc">
					</view>

					<view class="input-text">
						<view class="title">密码</view>
						<input class="password" placeholder="请输入密码" placeholder-class="plc" :password="visible" v-model="userPassword"
						 @input="handleinput" maxlength="15"/>
						<view class="eyes">
							<image src="../../static/eye2.png" @click="eye" v-if="bool"></image>
							<image src="../../static/eye1.png" @click="eye" v-if="!bool"></image>
						</view>
					</view>
					<button class="login" @click="login">登录</button>
					<view class="signUp">还没有账户?<span>立即注册</span></view>
				</view>
			</view>
		</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				Key: 0,
				show: true,
				bool: true,
				visible: true,
				userPassword:""
			};
		},
		onHide() { //更新key值达到重置动画的效果
			this.Key = Math.random()
			this.show = false
		},
		onShow() {
			this.show = true
		},
		methods: {
			login() {
				getApp().globalData.login = true
				uni.navigateTo({
					url: "/pages/loginSuccess/loginSuccess"
				})
			},
			eye() {
				this.bool = !this.bool
				this.visible = !this.visible
			},
			handleinput(e){
				const inputRule=/[\W]/g
				this.$nextTick(()=>{
					this.userPassword=e.detail.value.replace(inputRule,'')
				})
			}
		}
	}
</script>
<style lang="scss">
	.body {
		width: 750rpx;
		height: 1395rpx;
		background: linear-gradient(90deg, #128F8F 0%, #1FB0B0 47%, #13ACAC 63%, #169393 100%);
	}

	text {
		position: absolute;
		left: 64rpx;
		font-size: 50rpx;
		top: 130rpx;
		font-family: Jost-Black,jost;
		font-size: 50rpx;
		font-weight: 800;
		color: #FFFFFF;
		line-height: 75rpx;
	}

	.log {
		width: 750rpx;
		height: 1000rpx;
		position: absolute;
		bottom: 0;
	}

	.form {
		width: 737rpx;
		height: 990rpx;
		background-color: white;
		border-top-left-radius: 60rpx;
		border-top-right-radius: 60rpx;
		display: flex;
		flex-direction: column;
		border: 8rpx solid #D9D9D9;
		border-bottom: none;
	}

	.input-text {
		width: 626rpx;
		height: 100rpx;
		margin: 60rpx auto;
		background-color: #FFFFFF;

		.title {
			font-size: 35rpx;
			font-weight: 600;
		}

		input {
			margin-top: 50rpx;
			border-bottom: 6rpx solid #F5F5F5;
			height: 80rpx;

			.plc {
				font-size: 36rpx;
				font-family: Jost-Regular, Jost;
				font-weight: 400;
				color: #D9D9D9;
			}
		}
	}

	.eyes {
		width: 50rpx;
		height: 50rpx;
		position: relative;
		bottom: 60rpx;
		left: 570rpx;

		image {
			width: 100%;
			height: 100%;
		}
	}

	.login {
		position: relative;
		top: 300rpx;
		width: 604rpx;
		height: 122rpx;
		background: linear-gradient(180deg, #969290 0%, #D1D1D1 34%, #D1D1D1 71%, #B2AFAB 100%);
		border-radius: 38rpx;
		opacity: 1;
		border: 6rpx solid #F3EFEF;
		padding-top: 15rpx;
		font-size: 62rpx;
		font-family: Jost-Light, Jost;
		font-weight: 600;
		color: #000000;
		line-height: 72rpx;
	}

	.signUp {
		margin: 0 auto;
		bottom: 50rpx;

		span {
			color: blue;
			border-bottom: 5rpx solid blue;
		}
	}
</style>
