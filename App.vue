<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
			uni.onTabBarMidButtonTap(() => {
				if (this.globalData.login)
					uni.navigateTo({
						url: "/pages/addmessage/addmessage"
					})
				else {
					uni.switchTab({
						url: "/pages/login/login"
					})
				}
			})

		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		},
		globalData: {
			login: false,
			userColor:"../../static/color/grey.png",
			colorId:2,
			userCloth:"../../static/clothes/c1.png",
			clothId:1
		}
	}
</script>
<style>
	/*每个页面公共css */
	@import'components/animate.min.css';
	@import'components/magic.css';

	@font-face {
		font-family: 'Jost-Medium';
		src: url("~@/font/Jost-Medium.ttf");
	}

	@font-face {
		font-family: 'JostBlack';
		src: url("~@/font/Jost-Black.ttf");
	}

	@font-face {
		font-family: 'ChillBit';
		src: url("~@/font/ChillBitmap.ttf");
	}

	@font-face {
		font-family: 'Ipix';
		src: url("~@/font/Ipix.ttf");
	}
</style>
