<template>
	<view class="history">
		<view class="list" v-for="item in list" :key="item.id" @click="goDetail">
			<view class="text">
				<view class="u_text">{{ item.title }}</view>
				<view class="l_text">{{ item.date }}</view>
			</view>
			<view class="img">
				<image :src="item.imgUrl"></image>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list: [
					{
						id: 1,
						title: '四月新番导视四月新番导视四月新番导视',
						imgUrl: '../../static/images/banner2.webp',
						content: '四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视',
						date: '2022-4-5 08:00'
					},
					{
						id: 2,
						title: '四月新番导视四月新番导视四月新番导视',
						imgUrl: '../../static/images/banner2.webp',
						content: '四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视',
						date: '2022-4-5 08:00'
					},
					{
						id: 3,
						title: '四月新番导视四月新番导视四月新番导视',
						imgUrl: '../../static/images/banner2.webp',
						content: '四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视',
						date: '2022-4-5 08:00'
					},
					{
						id: 4,
						title: '四月新番导视四月新番导视四月新番导视',
						imgUrl: '../../static/images/banner2.webp',
						content: '四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视',
						date: '2022-4-5 08:00'
					}
				]
			}
		},
		methods: {
			goDetail() {
				uni.navigateTo({
					url: '../com-detail/com-detail'
				})
			}
		}
	}
</script>

<style lang="scss">
	.list{
		width: 750rpx;
		height: 200rpx;
		display: flex;
		margin-top: 5px;
		border-bottom: 1px solid #eaeaea;
		.text{
			width: 480rpx;
			float: left;
			.u_text{
				margin: 10px 5px 10px;
			}
			.l_text{
				margin-left: 5px;
			}
		}
		.img{
			width: 120rpx;
			float: right;
			margin: 5px 5px;
			image{
				width: 120px;
				height: 80px;
				border-radius: 5px;
			}
		}
	}
</style>
