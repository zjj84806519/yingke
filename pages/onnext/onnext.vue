<template>
	<view class="onnext">
		<view class="onnext-item" v-for="(item,index) in find" :key="item.id">
			<view class="time">{{ item.date }} 中国大陆上映</view>
			<swiper class="swiper" indicator-dots>
				<swiper-item v-for="(item,index) in item.imgUrl" :key="index" @click="goDetail(item.id)">
					<view class="swiper-item">
						<image :src="item" mode="aspectFill"></image>
					</view>
				</swiper-item>
			</swiper>
			<view class="text">
				<view class="text-top">
					<image class="cover" :src="item.coverUrl" mode="aspectFill" @click="goDetail(item.id)"></image>
					<view class="t-tit">
						<view class="like">
							<uni-icons :type="flag[index]?'heart-filled':'heart'" size="30px" color="#ff9500" @click="collect(index)"></uni-icons>
							<view style="color: #ff9500;">想看</view>
						</view>
					</view>
					<view class="t-text">
						<view class="b">{{ item.title }}</view>
						<view>尚未上映</view>
						<view>{{ item.info }}</view>
					</view>
				</view>
				<view class="brief">{{ item.brief }}</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				flag: [],
				find: [
					{
						id: 1,
						title: '新蝙蝠侠(2022)',
						date: '6月2日',
						coverUrl: '../../static/images/mov/cover/m1.webp',
						imgUrl: [
							'../../static/images/mov/pic/4128335310.webp',
							'../../static/images/mov/pic/4128337297.webp',
							'../../static/images/mov/pic/4128345978.webp',
							'../../static/images/mov/pic/4128348689.webp'
						],
						grade: 4.5,
						info: '2022/美国/动作/sss/sss',
						brief: '布鲁斯·韦恩（罗伯特·帕丁森 饰）化身蝙蝠侠于哥谭市行侠仗义两年后，罪犯皆闻风丧胆，他也因此深入接触到哥谭市的阴暗面。他潜行于哥谭市腐败的政要名流关系网中，身边仅有的几个值得信赖的盟友——管家阿尔弗雷德·潘尼沃斯（安迪·瑟金斯 饰）与詹姆斯·戈登警长（杰弗里·怀特 饰）。这位独行的“义警侠探”在哥谭市民心中已成为“复仇”二字最当仁不让的代名词。',
						hot: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠'
					},
					{
						id: 2,
						title: '月球陨落(2022)',
						date: '6月2日',
						coverUrl: '../../static/images/mov/cover/m2.webp',
						imgUrl: [
							'../../static/images/mov/pic/4128335310.webp',
							'../../static/images/mov/pic/4128337297.webp',
							'../../static/images/mov/pic/4128345978.webp',
							'../../static/images/mov/pic/4128348689.webp'
						],
						grade: 2.5,
						info: '2022/美国/动作/sss/sss',
						brief: '布鲁斯·韦恩（罗伯特·帕丁森 饰）化身蝙蝠侠于哥谭市行侠仗义两年后，罪犯皆闻风丧胆，他也因此深入接触到哥谭市的阴暗面。他潜行于哥谭市腐败的政要名流关系网中，身边仅有的几个值得信赖的盟友——管家阿尔弗雷德·潘尼沃斯（安迪·瑟金斯 饰）与詹姆斯·戈登警长（杰弗里·怀特 饰）。这位独行的“义警侠探”在哥谭市民心中已成为“复仇”二字最当仁不让的代名词。',
						hot: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠'
					},
					{
						id: 3,
						title: '新蝙蝠侠(2022)',
						date: '6月2日',
						coverUrl: '../../static/images/mov/cover/m1.webp',
						imgUrl: [
							'../../static/images/mov/pic/4128335310.webp',
							'../../static/images/mov/pic/4128337297.webp',
							'../../static/images/mov/pic/4128345978.webp',
							'../../static/images/mov/pic/4128348689.webp'
						],
						grade: 4.5,
						info: '2022/美国/动作/sss/sss',
						brief: '布鲁斯·韦恩（罗伯特·帕丁森 饰）化身蝙蝠侠于哥谭市行侠仗义两年后，罪犯皆闻风丧胆，他也因此深入接触到哥谭市的阴暗面。他潜行于哥谭市腐败的政要名流关系网中，身边仅有的几个值得信赖的盟友——管家阿尔弗雷德·潘尼沃斯（安迪·瑟金斯 饰）与詹姆斯·戈登警长（杰弗里·怀特 饰）。这位独行的“义警侠探”在哥谭市民心中已成为“复仇”二字最当仁不让的代名词。',
						hot: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠'
					},
					{
						id: 4,
						title: '月球陨落(2022)',
						date: '6月2日',
						coverUrl: '../../static/images/mov/cover/m2.webp',
						imgUrl: [
							'../../static/images/mov/pic/4128335310.webp',
							'../../static/images/mov/pic/4128337297.webp',
							'../../static/images/mov/pic/4128345978.webp',
							'../../static/images/mov/pic/4128348689.webp'
						],
						grade: 2.5,
						info: '2022/美国/动作/sss/sss',
						brief: '布鲁斯·韦恩（罗伯特·帕丁森 饰）化身蝙蝠侠于哥谭市行侠仗义两年后，罪犯皆闻风丧胆，他也因此深入接触到哥谭市的阴暗面。他潜行于哥谭市腐败的政要名流关系网中，身边仅有的几个值得信赖的盟友——管家阿尔弗雷德·潘尼沃斯（安迪·瑟金斯 饰）与詹姆斯·戈登警长（杰弗里·怀特 饰）。这位独行的“义警侠探”在哥谭市民心中已成为“复仇”二字最当仁不让的代名词。',
						hot: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠'
					}
				]
			}
		},
		methods: {
			goDetail(id){
				uni.navigateTo({
					url: '../mov-detail/mov-detail',
					//+id
				})
			},
			collect(index) {
				if(this.flag[index]){
					this.flag[index] = 0
					//收藏表中删除该项
				}
				else{
					this.flag[index] = 1
					//收藏表中增加该项
				}
				// console.log(this.flag)
				this.$forceUpdate()
				//将对应id的影片加入收藏数组
			}
		}
	}
</script>

<style lang="scss">
	.onnext{
		margin: 10px 10px;
		.onnext-item{
			padding-bottom: 10px;
			border-bottom: 1px solid #eaeaea;
			.time{
				margin: 10px 10px;
			}
			.swiper{
				width: 355px;
				height: 230px;
				border-radius: 10px;
				image{
					width: 355px;
					height: 230px;
					border-radius: 10px;
				}
			}
			.text{
				margin-top: 10px;
				.text-top{
					display: flex;
					line-height: 25px;
					.cover{
						width: 90px;
						height: 130px;
						border-radius: 10px;
					}
					.t-tit{
						margin-top: 5px;
						margin-right: 10px;
						.like{
							position: absolute;
							right: 10px;
							text-align: center;
						}
					}
				}
				.brief{
					margin-top: 10px;
				}
			}
		}
		
	}
</style>
