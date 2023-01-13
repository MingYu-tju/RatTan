<template>
	<view :class="activeclass" @click="gotoDetails">
		<view class="showBox">
			<view class="showTitle">{{item.title}}</view>
			<view class="userimg">
				<image :src="item.picsrc"></image>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: "showMessage",
		props: {
			item: {
				type: Object,
				default () {
					return {
						Id: null,
						title: "这是标题这是标题这是标题",
						picsrc: "../../static/test.jpg"
						//../../static/test.jpg
					}
				}

			}
		},
		data() {
			return {
				activeclass: "animate__animated animate__zoomIn"
			};
		},
		created() {
			setTimeout(e => {
				this.activeclass = "animate__animated animate__zoomOut"
			}, 14200)
		},
		methods: {
			gotoDetails() {
				if (getApp().globalData.login)
					uni.navigateTo({
						url: `/pages/details/details?cid=${this.item.Id}`
					})
				else {
					uni.switchTab({
						url:"/pages/login/login"
					})
				}
				}
			}
		}
</script>

<style lang="scss">
	.showBox {
		width: 140rpx;
		height: 140rpx;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.showTitle {
		width: 300rpx;
		position: absolute;
		bottom: 160rpx;
		white-space: nowrap;
		overflow: hidden;
		text-overflow: ellipsis;
	}

	.userimg {
		width: 100%;
		height: 100%;
		border-radius: 50%;
		position: relative;

		image {
			width: 100%;
			height: 100%;
			border-radius: 50%;
			position: absolute;
		}
	}
</style>
