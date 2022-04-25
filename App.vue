<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style lang="scss">
	/*每个页面公共css */
	@import '@/components/uni-scss/index.scss';
	/* #ifdef APP-NVUE */
	@import '@/static/customicons.css';
	// 设置整个项目的背景色
	page {
		background-color: #f5f5f5;
	}
	
	/* #endif */
	.b{
		font-size: 20px;
		font-weight: bold;
	}
	.s{
		color: #C0C0C0;
		font-weight: normal;
		font-size: 13px;
	}
</style>
