<template>
	<view class="home">
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
		
		<!-- 轮播图区域 -->
		<view class="banner">
			<swiper indicator-dots autoplay :interval="3000" :duration="1000">
				<swiper-item v-for="item in swipers" :key="item.id" @click="goDetail(item.id)">
					<view class="swiper-item">
						<image :src="item.imgUrl" mode="aspectFill"></image>
					</view>
				</swiper-item>
			</swiper>
		</view>
		
		<!-- 导航区域 -->
		<view class="nav">
			<view class="nav_item" v-for="(item,index) in nav" :key="index" @click="goNavs(item)">
				<uni-icons class="icon" :type="item.type" size="70rpx"></uni-icons>
				<view>{{item.title}}</view>
			</view>
		</view>
		
		<!-- 推荐区域 -->
		<view class="recom">
			<view class="u_list">
				<view :class="recomflag?'b':''" @click="chooseRecom">影院热映</view>
				<view class="line"></view>
				<view :class="!recomflag?'b':''" @click="chooseHot">热门推荐</view>
				<view>
					全部<uni-icons type="right"></uni-icons>
				</view>
			</view>
			<scroll-list-item v-show="recomflag" class="recom-item" :array="recoms" @scrollItemClick="goDetail($options)"></scroll-list-item>
			<scroll-list-item v-show="!recomflag" class="recom-item" :array="hot" @scrollItemClick="goDetail($options)"></scroll-list-item>
			<!-- <scroll-view class="scroll-list" scroll-x="true" >
				<view class="scroll-item" v-for="(item,index) in recoms" :key="index" @click="goDetail">
					<image :src="item.imgUrl" ></image>
					<view>{{ item.title }}</view>
					<view class="grade">{{ item.grade }}</view>
				</view>
			</scroll-view> -->
		</view>
		
		<!-- 找电影区域 -->
		<view class="find">
			<view class="b">找电影</view>
			<view class="find-item" v-for="(item,index) in find" :key="item.id">
				<view class="f-pics">
					<image class="cover" :src="item.coverUrl" mode="aspectFill" @click="goDetail(item.id)"></image>
					<swiper class="f-swiper" indicator-dots>
						<swiper-item v-for="(item,index) in item.imgUrl" :key="index" @click="goDetail(item.id)">
							<view class="swiper-item">
								<image :src="item" mode="aspectFill"></image>
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
		<!-- 底部区域 -->
		<view class="bottom">前面的区域以后再来探索吧</view>
	</view>
</template>

<script>
	import searchItem from '../../components/search-item/search-item.vue';
	import scrollListItem from '../../components/scroll-list-item/scroll-list-item.vue';
	import uniSection from '../../components/uni-section/uni-section.vue';
	import drawerContentItem from '../../components/drawer-content-item/drawer-content-item.vue';
	export default {
		data() {
			return {
				showLeft: false,
				flag: [],
				recomflag: true,
				title: '首页',
				swipers: [
					{
						id: 1,
						imgUrl:"../../static/images/banner1.webp",
						grade: 4.9	
					},
					{
						id: 2,
						imgUrl:"../../static/images/banner2.webp",
						grade: 4.9	
					},
					{
						id: 3,
						imgUrl:"../../static/images/banner3.webp",
						grade: 4.9	
					},
				],
				nav: [
					{
						id: 0,
						type: 'search',
						title: '找电影',
						path: ''
					},
					{
						id: 1,
						type: 'medal',
						title: '排行榜',
						path: '../mov-list/mov-list'
					},
					{
						id: 2,
						type: 'calendar',
						title: '即将上映',
						path: '../onnext/onnext'
					},
					{
						id: 3,
						type: 'list',
						title: '片单',
						path: '../mov-list/mov-list'
					}
				],
				recoms: [
					{
						id:'001',
						second: '新蝙蝠侠',
						imgUrl: '../../static/images/mov/cover/m1.webp',
						third: 4.5
					},
					{
						id: '002',
						second: '月球陨落',
						imgUrl: '../../static/images/mov/cover/m2.webp',
						third: 2.5
					},
					{
						id: '003',
						second: '青春变形记',
						imgUrl: '../../static/images/mov/cover/m3.webp',
						third: 4.2
					},
					{
						id: '004',
						second: '狙击手',
						imgUrl: '../../static/images/mov/cover/m4.webp',
						third: 3.5
					},
					{
						id: 5,
						second: '新蝙蝠侠',
						imgUrl: '../../static/images/mov/cover/m1.webp',
						third: 4.5
					},
					{
						id: 6,
						second: '月球陨落',
						imgUrl: '../../static/images/mov/cover/m2.webp',
						third: 2.5
					},
					{
						id: 7,
						second: '青春变形记',
						imgUrl: '../../static/images/mov/cover/m3.webp',
						third: 4.2
					}
				],
				hot: [
					{
						id: '001',
						second: '新蝙蝠侠',
						imgUrl: '../../static/images/mov/cover/m1.webp',
						third: 4.5
					},
					{
						id: '002',
						second: '月球陨落',
						imgUrl: '../../static/images/mov/cover/m2.webp',
						third: 2.5
					},
					{
						id: '003',
						second: '青春变形记',
						imgUrl: '../../static/images/mov/cover/m3.webp',
						third: 4.2
					}
				],
				find: [
					{
						id: '001',
						title: '新蝙蝠侠(2022)',
						coverUrl: '../../static/images/mov/cover/m1.webp',
						imgUrl: [
							'../../static/images/mov/pic/4128335310.webp',
							'../../static/images/mov/pic/4128337297.webp',
							'../../static/images/mov/pic/4128345978.webp',
							'../../static/images/mov/pic/4128348689.webp'
						],
						grade: 4.5,
						info: '2022/美国/动作/sss/sss',
						hot: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠'
					},
					{
						id: '002',
						title: '月球陨落(2022)',
						coverUrl: '../../static/images/mov/cover/m2.webp',
						imgUrl: [
							'../../static/images/mov/pic/4128335310.webp',
							'../../static/images/mov/pic/4128337297.webp',
							'../../static/images/mov/pic/4128345978.webp',
							'../../static/images/mov/pic/4128348689.webp'
						],
						grade: 2.5,
						info: '2022/美国/动作/sss/sss',
						hot: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠'
					},
					{
						id: 3,
						title: '月球陨落(2022)',
						coverUrl: '../../static/images/mov/cover/m2.webp',
						imgUrl: [
							'../../static/images/mov/pic/4128335310.webp',
							'../../static/images/mov/pic/4128337297.webp',
							'../../static/images/mov/pic/4128345978.webp',
							'../../static/images/mov/pic/4128348689.webp'
						],
						grade: 2.5,
						info: '2022/美国/动作/sss/sss',
						hot: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠'
					}
				]
			}
		},
		onLoad() {
			
		},
		components: {
			'search-item': searchItem,
			'scroll-list-item': scrollListItem,
			'drawer-content-item': drawerContentItem
		},
		methods: {
			goDetail(id){
				console.log(id)
				uni.navigateTo({
					url: '../mov-detail/mov-detail',
					//+id
				})
			},
			goNavs(item) {
				switch(item.id){
					case 0:
						uni.createSelectorQuery().select('.find').boundingClientRect(data=>{//目标位置的节点，类class或者id
							console.log("目标view的top\left\right\bottom分别是多少",data.top,data.left,data.right,data.bottom)
							uni.pageScrollTo({
								duration: 100,//过渡时间
								scrollTop: data.top//到达目标class的top值
							})
						}).exec();
						break
					case 1:
						uni.navigateTo({
							url: '../rank/rank'
						})
						break
					case 2:
						uni.navigateTo({
							url: '../onnext/onnext'
						})
					case 3:
						console.log(item.id)
					default:
						break
				}
				
			},
			scan() {
				uni.scanCode({
					success: function (res) {
						console.log('条码类型：' + res.scanType);
						console.log('条码内容：' + res.result);
					}
				});
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
			},
			chooseRecom() {
				this.recomflag = true
			},
			chooseHot() {
				this.recomflag = false
			}
		}
	}
</script>

<style lang="scss">
	.home{
		.drawer{
			
		}
		.banner{
			swiper{
				width: 750rpx;
				height: 400rpx;
				text-align: center;
				image{
					width: 750rpx;
				}
			}
		}
		
		.nav{
			display: flex;
			margin-top: 20px;
			.nav_item{
				width: 75px;
				margin: 5px auto;
				text-align: center;
				background: #fff;
				font-size: 13px;
				border: solid 1px #eaeaea;
				border-radius: 20rpx;
				box-shadow: 5px 5px 10px #eaeaea;
				padding-top: 5px;
			}
		}
		.recom{
			margin-top: 30px;
			.u_list{
				display: flex;
				font-size: 20px;
				view{
					margin-left: 10px;
				}
				view:last-child{
					position: absolute;
					right: 5px;
					margin-top: 5px;
					font-size: 15px;
				}
				.line{
					border-left: 1px solid #808080;
				}
			}
			.recom-item{
				margin-top: 10px;
			}
			
			.scroll-list{
				width: 100%;
				margin-top: 20px;
				overflow: hidden;
				white-space: nowrap;
				.scroll-item{
					display: inline-block;
					margin-left: 10px;
					image{
						width: 95px;
						height: 140px;
						border-radius: 10px;
					}
					.grade{
						color: #ff9500;
					}
				}
				// overflow-x: hidden;
			}
		}
		.find{
			margin-top: 10px;
			margin-left: 10px;
			.find-item{
				padding-bottom: 10px;
				border-bottom: 1px solid #eaeaea;
				.f-pics{
					display: flex;
					margin-top: 10px;
					.cover{
						width: 110px;
						height: 160px;
						border-radius: 10px;
					}
					.f-swiper{
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
		.bottom{
			height: 50px;
			margin-top: 20px;
			text-align: center;
		}
	}
</style>
