<template>
	<view class="ground">

		<view class="hist">
			<view class="history" @click="gotoHistoryPage">
				<image src="../../static/history.png"></image>
			</view>
		</view>

		<view class="tubebox">
			<view class="tubebox1">
				<view class="tube">
					<showMessage v-if="show1" :item="item1"></showMessage>
				</view>
				<view class="tube">
					<showMessage v-if="0"></showMessage>
				</view>
				<view class="tube">
					<showMessage v-if="0"></showMessage>
				</view>
				<view class="tube">
					<showMessage v-if="0"></showMessage>
				</view>
				<view class="tube">
					<showMessage v-if="show2" :item="item2"></showMessage>
				</view>
			</view>

			<view class="tubebox2">
				<view class="tube">
					<showMessage v-if="0"></showMessage>
				</view>
				<view class="tube">
					<showMessage v-if="0"></showMessage>
				</view>
				<view class="tube">
					<showMessage v-if="show3" :item="item3"></showMessage>
				</view>
				<view class="tube">
					<showMessage v-if="0"></showMessage>
				</view>
				<view class="tube">
					<showMessage v-if="0"></showMessage>
				</view>
				<view class="tube">
					<showMessage v-if="0"></showMessage>
				</view>
			</view>
			<view class="tubebox1">
				<view class="tube">
					<showMessage v-if="0"></showMessage>
				</view>
				<view class="tube">
					<showMessage v-if="0"></showMessage>
				</view>
				<view class="tube">
					<showMessage v-if="0"></showMessage>
				</view>
				<view class="tube">
					<showMessage v-if="0"></showMessage>
				</view>
				<view class="tube">
					<showMessage v-if="show4" :item="item4"></showMessage>
				</view>
			</view>
			<view class="tubebox2">
				<view class="tube">
					<showMessage v-if="0"></showMessage>
				</view>
				<view class="tube">
					<showMessage v-if="show5" :item="item5"></showMessage>
				</view>
				<view class="tube">
					<showMessage v-if="0"></showMessage>
				</view>
				<view class="tube">
					<showMessage v-if="0"></showMessage>
				</view>
				<view class="tube">
					<showMessage v-if="0"></showMessage>
				</view>
				<view class="tube">
					<showMessage v-if="0"></showMessage>
				</view>
			</view>
			<view class="tubebox1">
				<view class="tube">
					<showMessage v-if="0"></showMessage>
				</view>
				<view class="tube">
					<showMessage v-if="0"></showMessage>
				</view>
				<view class="tube">
					<showMessage v-if="show6" :item="item6"></showMessage>
				</view>
				<view class="tube">
					<showMessage v-if="0"></showMessage>
				</view>
				<view class="tube">
					<showMessage v-if="show7" :item="item7"></showMessage>
				</view>
			</view>
		</view>

		<view class="tail">
			<view class="custom" @click="changeImg">
				<image src="../../static/testimage.png"></image>
			</view>
		</view>
	</view>

</template>

<script>
	export default {
		data() {
			return {
				item1: {},
				item2: {},
				item3: {},
				item4: {},
				item5: {},
				item6: {},
				item7: {},
				show1: 0,
				show2: 0,
				show3: 0,
				show4: 0,
				show5: 0,
				show6: 0,
				show7: 0,
			}
		},
		methods: {
			gotoHistoryPage() {
				if (getApp().globalData.login)
					uni.navigateTo({
						url: "../historymessage/historymessage"
					})
				else {
					uni.switchTab({
						url: "/pages/login/login"
					})
				}
			},
			addMessage() {
				if (getApp().globalData.login)
					uni.navigateTo({
						url: "/pages/addmessage/addmessage"
					})
				else {
					uni.switchTab({
						url: "/pages/login/login"
					})
				}
			},
			changeImg() {
				if (getApp().globalData.login)
					uni.navigateTo({
						url: "/pages/changeImage/changeImage"
					})
				else {
					uni.switchTab({
						url: "/pages/login/login"
					})
				}
			},
			getTitle1() {
				uni.request({
					method: 'GET',
					url: "https://jsonplaceholder.typicode.com/photos/" + Math.floor(Math.random() * 90 + 1),
					success: res => {
						this.item1 = {
							Id: res.data.id,
							title: res.data.title,
							picsrc: res.data.thumbnailUrl
						}
						this.show1 = 1
						setTimeout(e => {
							this.show1 = 0
						}, 15000)
					}
				})
			},
			getTitle2() {
				uni.request({
					method: 'GET',
					url: "https://jsonplaceholder.typicode.com/photos/" + Math.floor(Math.random() * 90 + 1),
					success: res => {
						setTimeout(e => {
							this.item2 = {
								Id: res.data.id,
								title: res.data.title,
								picsrc: res.data.thumbnailUrl
							}
							this.show2 = 1
							setTimeout(e => this.show2 = 0, 15000)
						}, 5000)

					}
				})

			},

			getTitle3() {
				uni.request({
					method: 'GET',
					url: "https://jsonplaceholder.typicode.com/photos/" + Math.floor(Math.random() * 90 + 1),
					success: res => {
						setTimeout(e => {
							this.item3 = {
								Id: res.data.id,
								title: res.data.title,
								picsrc: res.data.thumbnailUrl
							}
							this.show3 = 1
							setTimeout(e => this.show3 = 0, 15000)
						}, 8000)

					}
				})
			},
			getTitle4() {
				uni.request({
					method: 'GET',
					url: "https://jsonplaceholder.typicode.com/photos/" + Math.floor(Math.random() * 90 + 1),
					success: res => {
						setTimeout(e => {
							this.item4 = {
								Id: res.data.id,
								title: res.data.title,
								picsrc: res.data.thumbnailUrl
							}
							this.show4 = 1
							setTimeout(e => this.show4 = 0, 15000)
						}, 13000)

					}
				})
			},
			getTitle5() {
				uni.request({
					method: 'GET',
					url: "https://jsonplaceholder.typicode.com/photos/" + Math.floor(Math.random() * 90 + 1),
					success: res => {
						setTimeout(e => {
							this.item5 = {
								Id: res.data.id,
								title: res.data.title,
								picsrc: res.data.thumbnailUrl
							}
							this.show5 = 1
							setTimeout(e => this.show5 = 0, 15000)
						}, 17000)

					}
				})
			},
			getTitle6() {
				uni.request({
					method: 'GET',
					url: "https://jsonplaceholder.typicode.com/photos/" + Math.floor(Math.random() * 90 + 1),
					success: res => {
						setTimeout(e => {
							this.item6 = {
								Id: res.data.id,
								title: res.data.title,
								picsrc: res.data.thumbnailUrl
							}
							this.show6 = 1
							setTimeout(e => this.show6 = 0, 15000)
						}, 19000)

					}
				})
			},
			getTitle7() {
				uni.request({
					method: 'GET',
					url: "https://jsonplaceholder.typicode.com/photos/" + Math.floor(Math.random() * 90 + 1),
					success: res => {
						setTimeout(e => {
							this.item7 = {
								Id: res.data.id,
								title: res.data.title,
								picsrc: res.data.thumbnailUrl
							}
							this.show7 = 1
							setTimeout(e => this.show7 = 0, 15000)
						}, 22000)

					}
				})
			}
		},
		onLoad() {
			this.getTitle1()
			this.getTitle2()
			this.getTitle3()
			this.getTitle4()
			this.getTitle5()
			this.getTitle6()
			this.getTitle7()
			setInterval(this.getTitle1, 30000)
			setInterval(this.getTitle2, 25000)
			setInterval(this.getTitle3, 25000)
			setInterval(this.getTitle4, 25000)
			setInterval(this.getTitle5, 25000)
			setInterval(this.getTitle6, 25000)
			setInterval(this.getTitle7, 25000)
		}
	}
</script>

<style lang="scss">
	.hist {
		width: 750rpx;
		height: 140rpx;
		position: fixed;
		top: var(--window-top);
		display: flex;
		justify-content: center;
		align-items: center;

		.history {
			width: 80rpx;
			height: 80rpx;
			position: absolute;
			right: 30rpx;

			image {
				width: 100%;
				height: 100%;
			}
		}
	}

	.tubebox {
		width: 750rpx;
		height: 680rpx;
		margin-top: 300rpx;
		display: flex;
		flex-direction: column;
		bounce: none;

		.tubebox1 {
			flex: 1;
			display: flex;
			justify-content: center;

			.tube {
				width: 140rpx;
				height: 140rpx;
				position: relative;
				border: 1rpx solid black;
				background-color: #dadada;
				border-radius: 50%;
			}

		}

		.tubebox2 {
			flex: 1;
			display: flex;
			justify-content: center;

			.tube {
				width: 140rpx;
				height: 140rpx;
				min-width: 140rpx;
				position: relative;
				border: 1rpx solid black;
				border-radius: 50%;
			}
		}
	}

	.tail {
		width: 750rpx;
		position: fixed;
		bottom: var(--window-bottom);
		display: flex;
		justify-content: center;
		bottom: 90rpx;

		.custom {
			width: 200rpx;
			height: 200rpx;
			padding: 20rpx 0;

			image {
				width: 100%;
				height: 100%;
				border-radius: 60rpx;
				border: 3px solid #BDC6C3;
			}
		}
	}

	.say {
		width: 200rpx;
		line-height: 1.5em;
		position: absolute;
		right: 50rpx;
		bottom: 64rpx;
		text-align: center;
		border-radius: 15rpx;
	}
</style>
