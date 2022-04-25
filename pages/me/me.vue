<template>
	<view>
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
		<!-- 个人主页 -->
		<view class="me">
			<view class="visitor" v-show="flag" @click="goLogin">
				<image class="avatar" src="../../static/icons/visitor.png" mode=""></image>
				<view class="name">
					<view class="b">点击登录</view>
					<view class="dec">
						<view>关注-</view>
						<view class="line"></view>
						<view>粉丝-</view>
					</view>
				</view>
			</view>
			<view class="user" v-show="!flag">
				<image class="avatar" src="https://yingke-pics.oss-cn-shenzhen.aliyuncs.com/user/01.jpg" mode=""></image>
				<view class="name">
					<view class="b">Lisa</view>
					<view class="s">账户名：admin001</view>
					<view class="dec">
						<view>关注7</view>
						<view class="line"></view>
						<view>粉丝0</view>
					</view>
				</view>
			</view>
			<view class="nav">
				<view class="nav_item" @click="goHistory()">
					<image src="../../static/icons/time-red.png"></image>
					<view>历史记录</view>
				</view>
				<view class="line"></view>
				<view class="nav_item" @click="goList()">
					<image src="../../static/icons/favorite.png"></image>
					<view>我的收藏</view>
				</view>
			</view>
			<view class="border"></view>
			
			<!-- 列表区域 -->
			<view class="bar">
				<view class="bar-item" :style="barflag?'font-weight: bold;':''" @click="chooseArticle()">发帖</view>
				<view class="bar-item" :style="!barflag?'font-weight: bold;':''" @click="chooseReview()">评论</view>
			</view>
			<view class="list" v-show="barflag" v-for="item in list" :key="item.id" @click="goDetail(item.id)">
				<view class="list-item">
					<view class="text">
						<view class="u_text">{{ item.title }}</view>
						<view class="l_text">{{ item.date }}</view>
					</view>
					<view class="img">
						<image :src="item.imgUrl"></image>
					</view>
				</view>
			</view>
			<view class="review" v-show="!barflag" v-for="(item,index) in review" :key="index">
				<view class="r-top">
					<view class="review-user">
						<image src="../../static/images/user/user1.jpg"></image>
						<view class="r-tit">
							<view class="b">{{ item.userName }}</view>
							<view class="r-tit-s">{{ item.date }} 评论帖子</view>
						</view>
						<uni-icons class="more" type="more-filled" size="20px" color="#C0C0C0"></uni-icons>
					</view>
				</view>
				<view class="r-review">
					<view>{{ item.content }}</view>
					<view class="r-bar" @click="goArticle(item.id)">
						<image src="../../static/images/banner2.webp" mode=""></image>
						<view class="r-tit">
							<view>{{ item.title }}</view>
							<view>{{ item.userName }}</view>
						</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				// flag: true,
				flag: false,
				barflag: true,
				list:[
					{
						l_id: 1,
						title: '四月新番导视四月新番导视',
						imgUrl: '../../static/images/banner2.webp',
						content: '四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视',
						date: '2022-4-5 08:00'
					},
					{
						l_id: 2,
						title: '四月新番导视四月新番导视',
						imgUrl: '../../static/images/banner2.webp',
						content: '四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视',
						date: '2022-4-5 08:00'
					},
					{
						l_id: 3,
						title: '四月新番导视四月新番导视',
						imgUrl: '../../static/images/banner2.webp',
						content: '四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视',
						date: '2022-4-5 08:00'
					},
					{
						l_id: 4,
						title: '四月新番导视四月新番导视',
						imgUrl: '../../static/images/banner2.webp',
						content: '四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视四月新番导视',
						date: '2022-4-5 08:00'
					},
				],
				review: [
					{
						r_id: 1,
						title: '四月新番导视四月新番导视',
						imgUrl: '../../static/images/banner2.webp',
						userName: 'Lisa',
						content: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠',
						date: '2022-04-18'
					},
					{
						r_id: 2,
						title: '四月新番导视四月新番导视',
						imgUrl: '../../static/images/banner2.webp',
						userName: 'Lisa',
						content: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠',
						date: '2022-04-18'
					},
					{
						r_id: 3,
						title: '四月新番导视四月新番导视',
						imgUrl: '../../static/images/banner2.webp',
						userName: 'Lisa',
						content: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠',
						date: '2022-04-18'
					},
					{
						r_id: 4,
						title: '四月新番导视四月新番导视',
						imgUrl: '../../static/images/banner2.webp',
						userName: 'Lisa',
						content: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠',
						date: '2022-04-18'
					}
				]
			}
		},
		methods: {
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
			goHistory() {
				uni.navigateTo({
					url: '../history/history'
				})
			},
			goList() {
				uni.navigateTo({
					url: '../mov-list/mov-list'
					//+id
				})
			},
			goDetail(id) {
				console.log(id)
				uni.navigateTo({
					url: '../com-detail/com-detail'
					//+id
				})
			},
			goArticle(id) {
				console.log(id)
				uni.navigateTo({
					url: '../com-detail/com-detail'
					//+id
				})
			},
			goLogin() {
				uni.navigateTo({
					url: '../login/login'
				})
			},
			chooseArticle() {
				this.barflag = true
			},
			chooseReview() {
				this.barflag = false
			}
		}
	}
</script>

<style lang="scss">
	.drawer{
		.close {
			padding: 10px;
		}
	}
	.me{
		.visitor{
			display: flex;
			margin: 10px 10px;
			padding-bottom: 10px;
			.avatar{
				width: 60px;
				height: 60px;
				border-radius: 50px;
			}
			.name{
				margin-top: 5px;
				margin-left: 10px;
				.dec{
					display: flex;
					margin-top: 8px;
					view{
						margin-right: 10px;
					}
				}
			}
		}
		.user{
			display: flex;
			margin: 10px 10px;
			padding-bottom: 10px;
			.avatar{
				width: 60px;
				height: 60px;
				border-radius: 50px;
			}
			.name{
				margin-left: 10px;
				.dec{
					display: flex;
					view{
						margin-right: 10px;
					}
				}
			}
		}
		.line{
			width: 2px;
			background: #eaeaea;
		}
		.border{
			border-bottom: 2px solid #eaeaea;
		}
		.nav{
			display: flex;
			border-radius: 20rpx;
			margin: 10px 5px;
			background: #fff;
				border: solid 1px #eaeaea;
				border-radius: 20rpx;
			.nav_item{
				width: 50%;
				text-align: center;
				font-size: 13px;
				padding-top: 5px;
				image{
					width: 30px;
					height: 30px;
				}
			}
		}
		.bar{
			width: 355px;
			height: 40px;
			margin: 10px 10px;
			display: flex;
			border-radius: 5px;
			font-size: 20px;
			.bar-item{
				margin-right: 10px;
			}
		}
		.list{
			width: 750rpx;
			height: 200rpx;
			display: flex;
			margin-top: 10px;
			padding-bottom: 10px;
			border-bottom: 1px solid #eaeaea;
			.list-item{
				width: 100%;
				background: #fcfcfc;
				border: 1px solid #eaeaea;
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
					display: inline-block;
					margin: 5px 5px;
					image{
						width: 120px;
						height: 80px;
						border-radius: 5px;
					}
				}
			}
			
		}
		.review{
			margin-left: 10px;
			margin-right: 10px;
			padding-bottom: 10px;
			border-bottom: 1px solid #eaeaea;
			.review-user{
				margin-top: 15px;
				image{
					width: 40px;
					height: 40px;
					border-radius: 50px;
					box-shadow: 5px 5px 10px #eaeaea;
				}
				.r-tit{
					margin-left: 10px;
					display: inline-block;
					.r-tit-s{
						font-size: 13px;
						color: #C0C0C0;
					}
				}
				.more{
					position: absolute;
					right: 10px;
					margin-top: 25px;
				}
			}
			.r-review{
				margin-top: 10px;
				.r-bar{
					width: 100%;
					height: 70px;
					margin-top: 5px;
					margin-right: 10px;
					background: #fcfcfc;
					border: 1px solid #eaeaea;
					display: flex;
					image{
						width: 90px;
						height: 60px;
					}
					.r-tit{
						margin: 10px 10px;
						
					}
				}
			}
		}
	}
</style>
