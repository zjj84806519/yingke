<template>
	<view class="search">
		<button class="drawer-button" plain="true" type="default" @click="draw()">
			<uni-icons type="list" size="30px"></uni-icons>
		</button>
		<view class="search-bar">
			<uni-search-bar @confirm="search" :focus="false" v-model="searchValue" @blur="blur" @focus="focus" @input="input"
				@cancel="cancel" @clear="clear" :radius="20" clearButton="auto" cancelButton="none" placeholder="搜索">
			</uni-search-bar>
			<!-- <view class="search-result">
				<text class="search-result-text">当前输入为：{{ searchValue }}</text>
			</view> -->
		</view>
		<view class="icon">
			<uni-icons type="email" size="30px"></uni-icons>
		</view>
	</view>
</template>

<script>
	export default {
		name:"search-item",
		data() {
			return {
				searchValue: ''
			};
		},
		methods: {
			draw(){
				// console.log('点击按钮')
				this.$emit('showDrawer')
			},
			search(res) {
				uni.showToast({
					title: '搜索：' + res.value,
					icon: 'none'
				})
			},
			input(res) {
				console.log('----input:', res)
			},
			clear(res) {
				uni.showToast({
					title: 'clear事件，清除值为：' + res.value,
					icon: 'none'
				})
			},
			blur(res) {
				uni.showToast({
					title: 'blur事件，输入值为：' + res.value,
					icon: 'none'
				})
			},
			focus(e) {
				uni.showToast({
					title: 'focus事件，输出值为：' + e.value,
					icon: 'none'
				})
			},
			cancel(res) {
				uni.showToast({
					title: '点击取消，输入值为：' + res.value,
					icon: 'none'
				})
			}
		},
		onBackPress() {
			// #ifdef APP-PLUS
			plus.key.hideSoftKeybord();
			// #endif
		}
	}
</script>

<style lang="scss">
	.search{
		width: 100%;
		height: 50px;
		display: flex;
		border-bottom: 1px solid #eaeaea;
		.drawer-button{
			width: 40px;
			height: 40px;
			margin-top: 4px;
			line-height: 40px;
			border: 1px solid #fff;
		}
		.search-bar{
			width: 280px;
		}
		.icon{
			margin: 15px auto;
		}
	}
</style>
