<template>
	<view class="historyBox">
		<myhistory v-for="item in 10"></myhistory>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="scss">
	.historyBox{
		display: flex;
		flex-direction: column;
		align-items: center;
	}
</style>
