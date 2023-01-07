<template>
	<view>
		<view class="box">
			<view class="userImg">
				<image src="../../static/test.jpg"></image>
			</view>
			<view class="title">{{this.title}}</view>
			<view class="button" @click="deleteMessage">删除</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: "myhistory",
		data() {
			return {
				title:"这是测试标题这是测试标题测试标"
			};
		},
		methods:{
			deleteMessage(){
				
			}
		}
	}
</script>

<style lang="scss">
	.box {
		width: 670rpx;
		height: 200rpx;
		margin: 20rpx 0;
		background-color: #efefef;
		display: flex;
		justify-content: space-around;
		align-items: center;
		border-radius: 20rpx;
		
		.userImg{
			width: 130rpx;
			height: 130rpx;
			image{
				width: 100%;
				height: 100%;
				border-radius: 50%;
			}
		}
		
		.title {
			width:300rpx;
			border-bottom: 1px solid #dddddd;
		}


		.button {
			width: 50rpx;
			align-items: center;
			font-size: 25rpx;
		}
	}
</style>
