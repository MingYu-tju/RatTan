<template>
	<view>
		<view>id为{{this.uId}}的发言详情页</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				uId:null
			};
		},
		onLoad(e){
			this.uId=e.cid
		}
	}
</script>

<style lang="scss">

</style>
