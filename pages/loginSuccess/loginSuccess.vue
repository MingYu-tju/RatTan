<template>
	<view>
		<view @click="gotoIndex">登陆成功！点击返回首页</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		},
		methods:{
			gotoIndex(){
				uni.reLaunch({
					url:"/pages/index/index"
				})
			}
		}
	}
</script>

<style lang="scss">

</style>
