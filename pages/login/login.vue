<template>
	<view class="body">
		<view class="animate__animated animate__slideInRight animate__fast" :key="Key" v-if="show">
			<text>您好,
				请登陆后查看完整内容</text>
		</view>
		<view class="animate__animated animate__slideInRight animate__fast" v-if="showX">
			<text>您好,
				注册后可登录！</text>
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
						<input class="password" placeholder="请输入密码" placeholder-class="plc" :password="visible"
							v-model="userPassword" @input="handleinput" maxlength="15" />
						<view class="eyes">
							<image src="../../static/eye2.png" @click="eye" v-if="bool"></image>
							<image src="../../static/eye1.png" @click="eye" v-if="!bool"></image>
						</view>
					</view>
					<view class="login" @click="login">
						<image src="../../static/loginButton.png"></image>
					</view>
					<view class="signUp">还没有账户?<span @click="gotoRegister">立即注册</span></view>
				</view>
			</view>

			<view class="animate__animated animate__slideInUp animate__fast" v-if="showX">
				<view class="form">
					<view class="input-text">
						<view class="title">用户名</view>
						<input type="text" class="userName" placeholder="请输入用户名" placeholder-class="plc">
					</view>
					<view class="input-text">
						<view class="title">密码</view>
						<input class="password" placeholder="请输入密码" placeholder-class="plc" :password="visible"
							v-model="userPassword" @input="handleinput" maxlength="15" />
						<view class="eyes">
							<image src="../../static/eye2.png" @click="eye" v-if="bool"></image>
							<image src="../../static/eye1.png" @click="eye" v-if="!bool"></image>
						</view>
					</view>
					<view class="input-text">
						<view class="title">确认密码</view>
						<input class="password" placeholder="请再次输入密码" placeholder-class="plc" :password="visible"
							v-model="userPasswordX" @input="handleinputX" maxlength="15" />
						<view class="eyes">
							<image src="../../static/eye2.png" @click="eye" v-if="bool"></image>
							<image src="../../static/eye1.png" @click="eye" v-if="!bool"></image>
						</view>
					</view>
					<view v-if="!correct" class="correct">两次输入的密码不匹配！</view>
					<view class="register" @click="register">
						<image src="../../static/register.png"></image>
					</view>
				</view>
			</view>

		</view>

		<view class="loginSuccess" v-if="showS">已登录！</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				Key: 0,
				show: true,
				showX: false,
				showS: false,
				bool: true,
				visible: true,
				userPassword: "",
				userPasswordX: "",
				correct: true
			};
		},
		onHide() { //更新key值达到重置动画的效果
			this.Key = Math.random()
			this.show = false
			this.showX = false
		},
		onShow() {
			if (!getApp().globalData.login)
				this.show = true
		},
		methods: {
			login() {
				getApp().globalData.login = true
				uni.showLoading({
					mask: true
				})
				setTimeout(() => {
					uni.hideLoading()
					setTimeout(() => uni.switchTab({
						url: "/pages/index/index"
					}), 1000)

					this.show = false //展示已登录页面
					this.showX = false
					this.showS = true
				}, 1000)

			},
			gotoRegister() {
				this.showX = true
				this.show = false
			},
			eye() {
				this.bool = !this.bool
				this.visible = !this.visible
			},
			handleinput(e) { //限制密码输入格式
				const inputRule = /[\W]/g
				this.$nextTick(() => {
					this.userPassword = e.detail.value.replace(inputRule, '')
				})
			},
			handleinputX(e) {
				const inputRule = /[\W]/g
				this.$nextTick(() => {
					this.userPasswordX = e.detail.value.replace(inputRule, '')
				})
				if (this.userPasswordX != this.userPassword && this.userPasswordX != "")
					this.correct = false
				else {
					this.correct = true
				}
			},
			register() {

			}
		}
	}
</script>
<style lang="scss">
	.body {
		width: 750rpx;
		height: 1395rpx;
		background: linear-gradient(90deg, #AB5F7B 0%, #BA7C8C 47%, #BA7C8C 63%, #AB5F7B 100%);
	}

	text {
		position: absolute;
		left: 64rpx;
		font-size: 50rpx;
		top: 130rpx;
		font-family: Jost-Black, jost;
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
		width: 560rpx;
		height: 120rpx;
		top: 250rpx;
		left: 88rpx;

		image {
			width: 100%;
			height: 100%;
		}
	}

	.register {
		position: relative;
		width: 560rpx;
		height: 120rpx;
		top: 150rpx;
		left: 88rpx;

		image {
			width: 100%;
			height: 100%;
		}
	}

	.signUp {
		margin: 0 auto;
		bottom: 50rpx;

		span {
			color: blue;
			border-bottom: 5rpx solid blue;
		}
	}

	.correct {
		color: red;
		position: absolute;
		bottom: 275rpx;
		left: 70rpx;
	}
</style>
