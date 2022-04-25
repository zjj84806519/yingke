<template>
	<view class="rank">
		<view class="rank-item" v-for="(item,index) in rank" :key="item.id">
			<view class="pics">
				<view>
					<view class="flag">
						<text class="no" :style="index>8?'fontsize:14px':'margin-left:5px'">{{ index+1 }}</text>
						<image class="f-icon" v-show="index===0" src="../../static/icons/NO1.png"></image>
					</view>
					<image class="f-icon" v-show="index===1" src="../../static/icons/NO2.png"></image>
					<image class="f-icon" v-show="index===2" src="../../static/icons/NO3.png"></image>
					<image class="f-icon" v-show="index>2" src="../../static/icons/NO.png"></image>
					<image class="cover" :src="item.coverUrl" @click="goDetail(item.id)"></image>
				</view>
				<swiper class="swiper" indicator-dots>
					<swiper-item v-for="(item,index) in item.imgUrl" :key="index" @click="goDetail(item.id)">
						<view class="swiper-item">
							<image :src="item" ></image>
						</view>
					</swiper-item>
				</swiper>
			</view>
			<view class="text">
				<view class="t-tit">
					<view class="like">
						<uni-icons :type="flag[index]?'heart-filled':'heart'" size="30px" color="#ff9500" @click="collect(index)"></uni-icons>
						<view style="color: #ff9500;">想看</view>
					</view>
					</view>
				<view class="b">{{ item.title }}</view>
				<view class="t-score">
					<uni-rate :readonly="true" :value="item.grade" size="13px"/>
					<view class="t-score-n" style="color: #ff9500;">{{ item.grade }}</view>
				</view>
				<view class="s">{{ item.info }}</view>
				<view>{{ item.hot }}</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				flag: [],
				rank: [
					{
						id: 1,
						title: '新蝙蝠侠(2022)',
						coverUrl: '../../static/images/mov/cover/m1.jpg',
						imgUrl: [
							'../../static/images/mov/pic/4128335310.jpg',
							'../../static/images/mov/pic/4128337297.jpg',
							'../../static/images/mov/pic/4128345978.jpg',
							'../../static/images/mov/pic/4128348689.jpg'
						],
						grade: 4.5,
						info: '2022/美国/动作/sss/sss',
						hot: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠'
					},
					{
						id: 2,
						title: '月球陨落(2022)',
						coverUrl: '../../static/images/mov/cover/m2.jpg',
						imgUrl: [
							'../../static/images/mov/pic/4128335310.jpg',
							'../../static/images/mov/pic/4128337297.jpg',
							'../../static/images/mov/pic/4128345978.jpg',
							'../../static/images/mov/pic/4128348689.jpg'
						],
						grade: 2.5,
						info: '2022/美国/动作/sss/sss',
						hot: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠'
					},
					{
						id: 3,
						title: '月球陨落(2022)',
						coverUrl: '../../static/images/mov/cover/m2.jpg',
						imgUrl: [
							'../../static/images/mov/pic/4128335310.jpg',
							'../../static/images/mov/pic/4128337297.jpg',
							'../../static/images/mov/pic/4128345978.jpg',
							'../../static/images/mov/pic/4128348689.jpg'
						],
						grade: 2.5,
						info: '2022/美国/动作/sss/sss',
						hot: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠'
					},
					{
						id: 4,
						title: '新蝙蝠侠(2022)',
						coverUrl: '../../static/images/mov/cover/m1.jpg',
						imgUrl: [
							'../../static/images/mov/pic/4128335310.jpg',
							'../../static/images/mov/pic/4128337297.jpg',
							'../../static/images/mov/pic/4128345978.jpg',
							'../../static/images/mov/pic/4128348689.jpg'
						],
						grade: 4.5,
						info: '2022/美国/动作/sss/sss',
						hot: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠'
					},
					{
						id: 5,
						title: '月球陨落(2022)',
						coverUrl: '../../static/images/mov/cover/m2.jpg',
						imgUrl: [
							'../../static/images/mov/pic/4128335310.jpg',
							'../../static/images/mov/pic/4128337297.jpg',
							'../../static/images/mov/pic/4128345978.jpg',
							'../../static/images/mov/pic/4128348689.jpg'
						],
						grade: 2.5,
						info: '2022/美国/动作/sss/sss',
						hot: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠'
					},
					{
						id: 6,
						title: '月球陨落(2022)',
						coverUrl: '../../static/images/mov/cover/m2.jpg',
						imgUrl: [
							'../../static/images/mov/pic/4128335310.jpg',
							'../../static/images/mov/pic/4128337297.jpg',
							'../../static/images/mov/pic/4128345978.jpg',
							'../../static/images/mov/pic/4128348689.jpg'
						],
						grade: 2.5,
						info: '2022/美国/动作/sss/sss',
						hot: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠'
					},
					{
						id: 7,
						title: '新蝙蝠侠(2022)',
						coverUrl: '../../static/images/mov/cover/m1.jpg',
						imgUrl: [
							'../../static/images/mov/pic/4128335310.jpg',
							'../../static/images/mov/pic/4128337297.jpg',
							'../../static/images/mov/pic/4128345978.jpg',
							'../../static/images/mov/pic/4128348689.jpg'
						],
						grade: 4.5,
						info: '2022/美国/动作/sss/sss',
						hot: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠'
					},
					{
						id: 8,
						title: '月球陨落(2022)',
						coverUrl: '../../static/images/mov/cover/m2.jpg',
						imgUrl: [
							'../../static/images/mov/pic/4128335310.jpg',
							'../../static/images/mov/pic/4128337297.jpg',
							'../../static/images/mov/pic/4128345978.jpg',
							'../../static/images/mov/pic/4128348689.jpg'
						],
						grade: 2.5,
						info: '2022/美国/动作/sss/sss',
						hot: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠'
					},
					{
						id: 9,
						title: '月球陨落(2022)',
						coverUrl: '../../static/images/mov/cover/m2.jpg',
						imgUrl: [
							'../../static/images/mov/pic/4128335310.jpg',
							'../../static/images/mov/pic/4128337297.jpg',
							'../../static/images/mov/pic/4128345978.jpg',
							'../../static/images/mov/pic/4128348689.jpg'
						],
						grade: 2.5,
						info: '2022/美国/动作/sss/sss',
						hot: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠'
					},
					{
						id: 10,
						title: '新蝙蝠侠(2022)',
						coverUrl: '../../static/images/mov/cover/m1.jpg',
						imgUrl: [
							'../../static/images/mov/pic/4128335310.jpg',
							'../../static/images/mov/pic/4128337297.jpg',
							'../../static/images/mov/pic/4128345978.jpg',
							'../../static/images/mov/pic/4128348689.jpg'
						],
						grade: 4.5,
						info: '2022/美国/动作/sss/sss',
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
	.rank{
		margin-left: 10px;
		.rank-item{
			padding-bottom: 10px;
			border-bottom: 1px solid #eaeaea;
			.pics{
				display: flex;
				margin-top: 10px;
				.flag{
					.no{
						position: absolute;
						z-index: 999;
						font-size: 18px;
						color: #fff;
					}
				}
				.f-icon{
					width: 30px;
					height: 30px;
					position: absolute;
					z-index: 998;
					margin-left: -4px;
					margin-top: -2px;
				}
				.cover{
					width: 110px;
					height: 160px;
					border-radius: 10px;
				}
				.swiper{
					width: 65%;
					height: 160px;
					margin-left: 15px;
					image{
						width: 235px;
						height: 160px;
						border-radius: 10px;
					}
				}
			}
			.text{
				margin-top: 10px;
				.t-tit{
					.like{
						margin-right: 10px;
						float: right;
						text-align: center;
					}
				}
				.t-score{
					display: inline-flex;
					.t-score-n{
						position: absolute;
						left: 75px;
						margin-top: -5px;
						font-size: 15px;
					}
				}
			}
		}
	}
</style>
