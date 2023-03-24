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
						<input type="text" class="userName" placeholder="请输入用户名" placeholder-class="plc"
							v-model="userName">
					</view>
					<view class="input-text">
						<view class="title">密码</view>
						<input class="password" placeholder="请输入密码" placeholder-class="plc" :password="visible"
							v-model="userPassword" @input="handleinput" maxlength="15" />
						<view class="eyes" hover-class="hoverButton" hover-stay-time="100" hover-start-time="0">
							<image src="../../static/eye2.png" @click="eye" v-if="bool"></image>
							<image src="../../static/eye1.png" @click="eye" v-if="!bool"></image>
						</view>
					</view>
					<view class="login" @click="login" hover-class="hoverButton" hover-stay-time="100"
						hover-start-time="0">
						<image src="../../static/loginButton.png"></image>
					</view>
					<view class="signUp">还没有账户?<span @click="gotoRegisterPage" hover-class="hoverButton"
							hover-stay-time="100" hover-start-time="0">立即注册</span></view>
				</view>
			</view>

			<view class="animate__animated animate__slideInUp animate__fast" v-if="showX">
				<view class="form">
					<view class="input-text">
						<view class="title">用户名</view>
						<input type="text" class="userName" placeholder="请输入用户名" placeholder-class="plc"
							v-model="userName">
					</view>
					<view class="input-text">
						<view class="title">密码</view>
						<input class="password" placeholder="请输入密码" placeholder-class="plc" :password="visible"
							v-model="userPassword" @input="handleinput" maxlength="15" />
						<view class="eyes" hover-class="hoverButton" hover-stay-time="100" hover-start-time="0">
							<image src="../../static/eye2.png" @click="eye" v-if="bool"></image>
							<image src="../../static/eye1.png" @click="eye" v-if="!bool"></image>
						</view>
					</view>
					<view class="input-text">
						<view class="title">确认密码</view>
						<input class="password" placeholder="请再次输入密码" placeholder-class="plc" :password="visible"
							v-model="userPasswordX" @input="handleinputX" maxlength="15" />
						<view class="eyes" hover-class="hoverButton" hover-stay-time="100" hover-start-time="0">
							<image src="../../static/eye2.png" @click="eye" v-if="bool"></image>
							<image src="../../static/eye1.png" @click="eye" v-if="!bool"></image>
						</view>
					</view>
					<view v-if="!correct" class="correct">两次输入的密码不匹配！</view>
					<view class="register" @click="register" hover-class="hoverButton" hover-stay-time="100"
						hover-start-time="0">
						<image src="../../static/register.png"></image>
					</view>
				</view>
			</view>

		</view>

		<view class="loginSuccess" v-if="showS">
			<image src="../../static/loginSuccessBack.png" class="loginSuccessBack"></image>
			<view class="ydl">{{userName}}，已登录！</view>
			<view :class="activeClass" @click="cheat" :key="Key">
				<image :src="color"></image>
				<image :src="cloth"></image>
			</view>
			<view class="tcdl" @click="signOut" hover-class="hoverButton" hover-stay-time="100" hover-start-time="0">
				<image src="../../static/tcdlButton.png"></image>
				<view>退出登录</view>
			</view>
		</view>
	</view>
</template>

<script>
	//const BaseUrl = "http://172.23.168.70:8080"
	const BaseUrl = "http://101.201.68.134:8199"
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
				userName: "",
				correct: true,
				userId: "userName",
				color: "",
				cloth: "",
				smallCheat: [
					'bounce',
					'flash',
					'pulse',
					'rubberBand',
					'shakeX',
					'shakeY',
					'headShake',
					'swing',
					'tada',
					'wobble',
					'jello'
				],
				activeClass: "userImg"
			};
		},
		onHide() { 		//更新key值重置动画
			this.Key = Math.random()
			this.show = false
			this.showX = false
		},
		onShow() {
			if (!getApp().globalData.login)
				this.show = true
			this.color = getApp().globalData.userColor
			this.cloth = getApp().globalData.userCloth
		},
		methods: {
			login() {
				uni.showLoading({			//loading弹窗
					title: "登陆中...",		
					mask: true
				})
				uni.request({		
					method: "POST",	
					url: BaseUrl + "/user/login",
					header: {
						'content-type': 'application/x-www-form-urlencoded'
					},
					data: {								//请求方式POST,参数为用户输入的账号密码
						userName: this.userName,
						userPassword: this.userPassword
					},
					success: res => {
						if (res.data.success == 'true') {	//如果账号密码正确
							getApp().globalData.colorId = res.data.colorId
							getApp().globalData.clothId = res.data.clothId
							getApp().globalData.userName = res.data.userName		
							getApp().globalData.userCloth = "../../static/clothes/c" + res.data.clothId +
								".png"
							getApp().globalData.userColor = "../../static/color/a" + res.data.colorId + ".gif"
							getApp().globalData.login = true			//修改登录状态为true、修改鼠鼠全局的形象
							this.color = getApp().globalData.userColor
							this.cloth = getApp().globalData.userCloth
							this.show = false 		//展示已登录页面
							this.showX = false
							this.showS = true
							uni.hideLoading()
						} else {
							uni.hideLoading()
							uni.showToast({
								title: "用户名或密码错误！",
								icon: 'none'
							})
						}
					},
					fail: () => {
						uni.hideLoading()
						uni.showToast({
							title: "请求失败！",
							icon: 'error'
						})
					}
				})
			},
			gotoRegisterPage() {
				this.showX = true
				this.show = false
				this.userName = ""
				this.userPassword = ""
				this.userPasswordX = ""
			},
			eye() { //密码是否可见
				this.bool = !this.bool
				this.visible = !this.visible
			},
			handleinput(e) { //限制密码输入格式
				const inputRule = /[\W]/g
				this.$nextTick(() => {
					this.userPassword = e.detail.value.replace(inputRule, '')
				})
			},
			handleinputX(e) { //限制密码输入格式
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
				if (this.userPassword == this.userPasswordX&&this.userName!="") {
					uni.showLoading({
						title: "加载中...",
						mask: true
					})
					uni.request({
						method: "POST",
						url: BaseUrl + "/user/register",
						header: {
							'content-type': 'application/x-www-form-urlencoded'
						},
						data: {
							userName: this.userName,
							userPassword: this.userPassword
						},
						success: res => {
							if (res.data.success == 'true') {
								uni.hideLoading()
								uni.showToast({
									title: "注册成功！"
								})
								this.showX = false
								this.show = true
							} else {
								uni.showToast({
									title: "该用户名已被注册！",
									icon: 'none'
								})
							}
						},
						fail: () => {
							uni.hideLoading()
							uni.showToast({
								title: "请求失败！",
								icon: 'error'
							})
						}
					})
				}
				else{
					uni.showToast({
						title:"请检查用户名或密码输入",
						icon:'none'
					})
				}
			},
			signOut() {
				uni.showModal({
					content: "确认退出？",
					success: (res) => {
						if (res.confirm) {
							getApp().globalData.login = 0
							this.showS = false
							this.show = true
							this.userName = ""
							this.userPassword = ""
							this.userPasswordX = ""
						}
					}
				})
			},
			cheat() {
				this.activeClass = "userImg animate__animated animate__" + this.smallCheat[Math.floor(Math
					.random() * 11)]
				this.Key = Math.random()
			}
		},
	}
</script>
<style lang="scss">
	.body {
		width: 750rpx;
		height: 1398rpx;
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
		position: absolute;
		left: 200rpx;
		bottom: 450rpx;

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

	.loginSuccess {
		width: 750rpx;
		height: 1395rpx;

		.loginSuccessBack {
			width: 750rpx;
			height: 900rpx;
			position: absolute;
		}

		.userImg {
			width: 700rpx;
			height: 700rpx;
			position: relative;
			left: 50rpx;
			top: 100rpx;

			image {
				width: 100%;
				height: 100%;
				position: absolute;
			}
		}

		.ydl {
			font-family: Ipix;
			font-size: 50rpx;
			color: #AB5F7B;
			position: relative;
			text-align: center;
			top: 100rpx;
		}

		.tcdl {
			width: 550rpx;
			height: 110rpx;
			position: absolute;
			left: 100rpx;
			bottom: 200rpx;

			image {
				position: absolute;
				width: 100%;
				height: 100%;
			}

			view {
				z-index: 2;
				position: absolute;
				width: 100%;
				height: 100%;
				font-size: 50rpx;
				font-weight: 500;
				color: #AB5F7B;
				display: flex;
				justify-content: center;
				align-items: center;
			}
		}
	}

	.hoverButton {
		opacity: 0.95;
		transform: scale(0.95, 0.95);
	}
</style>
