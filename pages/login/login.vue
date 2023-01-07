<template>
	<view class="body">
		<text class="animate__animated animate__slideInRight" :key="show">您好，
			请登陆后查看完整内容</text>
		<view class="log">
			<view class="animate__animated animate__slideInUp" :key="show">
				<view class="form">
					<view>用户名</view>
					<view class="input-text">
						<input type="text" class="userName" placeholder="用户名">
					</view>
					<view>密码</view>
					<view class="input-text">
						<input type="text" class="password" placeholder="密码" />
					</view>
					<button class="login">登录</button>
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
			show:0
			};
		},
		onTabItemTap(){
			this.show=Math.random()
		}
	}
</script>

<style lang="scss">
	.body {
		width: 750rpx;
		height: 1300rpx;
		background-color: #55aaff;
	}

	text {
		position: absolute;
		font-size: 50rpx;
		top: 150rpx;
	}

	.log {
		width: 750rpx;
		height: 1000rpx;
		position: absolute;
		bottom: 0;
	}

	.form {
		width: 750rpx;
		height: 1000rpx;
		background-color: white;
		border-top-left-radius: 60rpx;
		border-top-right-radius: 60rpx;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.input-text {
		background-color: white;
		border-radius: 5rpx;
		border-bottom: 3rpx solid gray;
	}
	.signUp{
		span{
			color: blue;
			border-bottom: 5rpx solid blue;
		}
	}
</style>
