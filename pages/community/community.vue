<template>
	<view class="com">
		<!-- #ifdef APP-PLUS -->
		<view style="margin-top: 30px;"></view>
		<!-- #endif -->
		
		<!-- 搜索栏区域 -->
		<search-item @showDrawer="showDrawer('showLeft')"></search-item>
		<!-- 侧拉栏区域 -->
		<view class="drawer">
			<!-- 侧拉栏内容 -->
			<uni-drawer mask ref="showLeft" mode="left" :width="250" @change="change($event,'showLeft')">
				<drawer-content-item @closeDrawer="closeDrawer('showLeft')" @scan='scan()'></drawer-content-item>
			</uni-drawer>
		</view>
		
		<!-- 列表区域 -->
		<view class="list" v-for="item in list" :key="item.id" @click="goDetail(item.id)">
			<view class="text">
				<view class="u_text">{{ item.title }}</view>
				<view class="l_text">{{ item.date }}</view>
			</view>
			<view class="img">
				<image :src="item.imgUrl"></image>
			</view>
		</view>
		<uni-fab ref="fab" :pattern="pattern" :horizontal="horizontal" :vertical="vertical"
			 @fabClick="fabClick" />
			
		<!-- 底部 -->
		<view class="bottom">前面的区域以后再来探索吧</view>
	</view>
</template>

<script>
	import searchItem from '../../components/search-item/search-item.vue';
	import fabItem from '../../components/uni-fab/uni-fab.vue'
	export default {
		data() {
			return {
				horizontal: 'right',
				vertical: 'bottom',
				pattern: {
					color: '#7A7E83',
					backgroundColor: '#fff',
					buttonColor: '#d81e06',
					iconColor: '#fff'
				},
				list:[
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
					},
					{
						id: 5,
						title: '四月新番导视四月新番导视四月新番导视',
						imgUrl: '../../static/images/banner2.webp',
						content: '四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视',
						date: '2022-4-5 08:00'
					},
					{
						id: 6,
						title: '四月新番导视四月新番导视四月新番导视',
						imgUrl: '../../static/images/banner2.webp',
						content: '四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视',
						date: '2022-4-5 08:00'
					},
					{
						id: 7,
						title: '四月新番导视四月新番导视四月新番导视',
						imgUrl: '../../static/images/banner2.webp',
						content: '四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视',
						date: '2022-4-5 08:00'
					},
					{
						id: 8,
						title: '四月新番导视四月新番导视四月新番导视',
						imgUrl: '../../static/images/banner2.webp',
						content: '四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视',
						date: '2022-4-5 08:00'
					},
					{
						id: 9,
						title: '四月新番导视四月新番导视四月新番导视',
						imgUrl: '../../static/images/banner2.webp',
						content: '四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视',
						date: '2022-4-5 08:00'
					},
					{
						id: 10,
						title: '四月新番导视四月新番导视四月新番导视',
						imgUrl: '../../static/images/banner2.webp',
						content: '四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视',
						date: '2022-4-5 08:00'
					},
					{
						id: 11,
						title: '四月新番导视四月新番导视四月新番导视',
						imgUrl: '../../static/images/banner2.webp',
						content: '四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视',
						date: '2022-4-5 08:00'
					},
					{
						id: 12,
						title: '四月新番导视四月新番导视四月新番导视',
						imgUrl: '../../static/images/banner2.webp',
						content: '四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视',
						date: '2022-4-5 08:00'
					},
					{
						id: 13,
						title: '四月新番导视四月新番导视四月新番导视',
						imgUrl: '../../static/images/banner2.webp',
						content: '四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视',
						date: '2022-4-5 08:00'
					}
				]
			}
		},
		components: {
			'search-item': searchItem
		},
		methods: {
			goDetail(id) {
				console.log(id)
				uni.navigateTo({
					url: '../com-detail/com-detail',
					//+id
				})
			},
			// 打开窗口
			showDrawer(e) {
				// console.log('打开抽屉')
				this.$refs[e].open();
			},
			// 关闭窗口
			closeDrawer(e) {
				this.$refs[e].close();
			},
			// 抽屉状态发生变化触发
			change(e, type) {
				// console.log((type === 'showLeft' ? '左窗口' : '右窗口') + (e ? '打开' : '关闭'));
				this[type] = e
			},
			fabClick() {
				uni.navigateTo({
					url: '../post/post'
				})
			}
		}
	}
</script>

<style lang="scss">
	.com{
		.drawer{
			.close {
				padding: 10px;
			}
		}
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
		
		.bottom{
			height: 50px;
			margin-top: 20px;
			text-align: center;
		}
	}
</style>
