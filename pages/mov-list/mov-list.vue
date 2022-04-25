<template>
	<view class="list">
		<view class="list-item" v-for="(item,index) in list" :key="index" @click="goDetail(item.id)">
			<image :src="item.imgUrl" mode="aspectFill"></image>
			<view>{{ item.second }}</view>
			<view class="third">
				<uni-rate style="margin-top: 3px;" :value="item.third*0.5" size="10px"></uni-rate>
				<view>{{ item.third }}</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				// 数据库传递
				list: [
					{
						id: 1,
						second: '新蝙蝠侠',
						imgUrl: '../../static/images/mov/cover/m1.webp',
						third: 7.6
					},
					{
						id: 2,
						second: '月球陨落',
						imgUrl: '../../static/images/mov/cover/m2.webp',
						third: 5.2
					},
					{
						id: 3,
						second: '青春变形记',
						imgUrl: '../../static/images/mov/cover/m3.webp',
						third: 8.2
					},
					{
						id: 4,
						second: '狙击手',
						imgUrl: '../../static/images/mov/cover/m4.webp',
						third: 7.7
					},
					{
						id: 1,
						second: '新蝙蝠侠',
						imgUrl: '../../static/images/mov/cover/m1.webp',
						third: 7.6
					},
					{
						id: 2,
						second: '月球陨落',
						imgUrl: '../../static/images/mov/cover/m2.webp',
						third: 5.2
					},
					{
						id: 3,
						second: '青春变形记',
						imgUrl: '../../static/images/mov/cover/m3.webp',
						third: 8.2
					},
					{
						id: 4,
						second: '狙击手',
						imgUrl: '../../static/images/mov/cover/m4.webp',
						third: 7.7
					},
					{
						id: 1,
						second: '新蝙蝠侠',
						imgUrl: '../../static/images/mov/cover/m1.webp',
						third: 7.6
					},
					{
						id: 2,
						second: '月球陨落',
						imgUrl: '../../static/images/mov/cover/m2.webp',
						third: 5.2
					},
					{
						id: 3,
						second: '青春变形记',
						imgUrl: '../../static/images/mov/cover/m3.webp',
						third: 8.2
					},
					{
						id: 4,
						second: '狙击手',
						imgUrl: '../../static/images/mov/cover/m4.webp',
						third: 7.7
					}
				],
				movies: []
			}
		},
		methods: {
			goDetail(id){
				console.log(id)
				uni.navigateTo({
					url: '../mov-detail/mov-detail'
					//+id
				})
			},
		}
	}
</script>

<style lang="scss">
	.list{
		margin-top: 10px;
		margin-left: 5px;
		.list-item{
			display: inline-block;
			margin-bottom: 10px;
			margin-left: 10px;
			image{
				width: 80px;
				height: 125px;
				border-radius: 10px;
			}
			.third{
				display: flex;
				color: #ffca3e;
			}
		}
		
	}
</style>
