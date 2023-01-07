<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
			// plus.screen.lockOrientation("portrait-primary")
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		},
		globalData:{
			tarbarKey:0
		}
	}
</script>
<style>
	/*每个页面公共css */
	@import'components/animate.min.css'
</style>
