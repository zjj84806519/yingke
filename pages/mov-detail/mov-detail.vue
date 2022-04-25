<template>
	<view class="detail">
		<!-- #ifdef APP-PLUS -->
		<view style="margin-top: 30px;"></view>
		<!-- #endif -->
		
		<view class="top" v-for="item in movie">
			<image :src="item.imgUrl"></image>
			<view class="tit">
				<view>
					<text>{{ item.title }}</text><br>
					<text>{{ item.eng_title }}</text><br>
					<text class="s">{{ item.label }}</text>
				</view>
				<view class="tit-score">
					<uni-rate :readonly="true" :value="item.grade*0.5" size="20px"/>
					<view class="c">{{ item.grade }}</view>
				</view>
				<view class="bot">
					<view class="collect">
						<uni-icons :type="flag?'star-filled':'star'" size="25px" color="#ffca3e" @click="collect(item.id)"></uni-icons>
						<view><text v-show="flag">已</text>收藏</view>
					</view>
					<view class="collect" @click="goAppraise(item.id)">
						<uni-icons type="hand-up" size="25px" color="#ffca3e"></uni-icons>
						<view>评价</view>
					</view>
				</view>
			</view>
			<view class="b">简介</view>
			<view class="intro">
				<rich-text :nodes="item.info"></rich-text>
			</view>
		</view>
		
		
		
		<view class="stuff">
			<view class="stuff-top">
				<view class="b">演职员</view>
				<view>
					全部<uni-icons type="right"></uni-icons>
				</view>
			</view>
			
			<scroll-list-item :array="stuff"></scroll-list-item>
		</view>
		
		<view class="pics">
			<view class="b">剧照</view>
			<scroll-view class="scroll-list" scroll-x >
				<view class="scroll-item" v-for="(item,index) in pics" :key="index">
					<view class="sroll-item-pics">
						<image :src="item" mode="aspectFill"></image>
					</view>
				</view>
			</scroll-view>
		</view>
		
		<view class="review">
			<view class="b">影评</view>
			<review-item :review="review" :rev_like="rev_like"></review-item>
		</view>
		
		<view class="bottom">已加载全部评论</view>
	</view>
</template>

<script>
	import scrollListItem from '../../components/scroll-list-item/scroll-list-item.vue';
	import reviewItem from '../../components/review-item/review-item.vue'
	export default {
		data() {
			return {
				flag: 0,
				rev_like: [],
				stuff: [
					{
						second: '马特·里夫斯',
						imgUrl: '../../static/images/stuff/Matt Reeves.jpg',
						third: '导演'
					},
					{
						second: '罗伯特·帕丁森',
						imgUrl: '../../static/images/stuff/Robert Pattinson.jpg',
						third: '饰 Bruce Wayne/Batman'
					},
					{
						second: '保罗·达诺',
						imgUrl: '../../static/images/stuff/Paul Dano.jpg',
						third: '饰 Edward Nashton/The Riddler'
					},
					{
						second: '佐伊·克罗维兹',
						imgUrl: '../../static/images/stuff/Zoë Kravitz.jpg',
						third: '饰 Selina Kyle  Catwoman'
					},
					{
						second: '杰弗里·怀特',
						imgUrl: '../../static/images/stuff/Jeffrey Wright.jpg',
						third: '饰 Commissioner Gordon'
					}
				],
				movie: [
					{
						id: 1,
						title: '新蝙蝠侠',
						eng_title: 'The Batman(2022)',
						imgUrl: 'https://yingke-pics.oss-cn-shenzhen.aliyuncs.com/movie/%E6%96%B0%E8%9D%99%E8%9D%A0%E4%BE%A0The%20Batman/cover.jpg',
						label: '美国/动作/2022-04-03/170分钟',
						grade: 7.6,
						info: '<p>阿甘（汤姆·汉克斯 饰）于二战结束后不久出生在美国南方阿拉巴马州一个闭塞的小镇，他先天弱智，智商只有75，然而他的妈妈是一个性格坚强的女性，她常常鼓励阿甘“傻人有傻福”，要他自强不息。</p><p>阿甘像普通孩子一样上学，并且认识了一生的朋友和至爱珍妮（罗宾·莱特·潘 饰），在珍妮 和妈妈的爱护下，阿甘凭着上帝赐予的“飞毛腿”开始了一生不停的奔跑。</p><p>阿甘成为橄榄球巨星、越战英雄、乒乓球外交使者、亿万富翁，但是，他始终忘不了珍妮，几次匆匆的相聚和离别，更是加深了阿甘的思念。</p><p>有一天，阿甘收到珍妮的信，他们终于又要见面……</p>'
					}
				],
				pics: [
					'../../static/images/mov/pic/4128335310.webp',
					'../../static/images/mov/pic/4128337297.webp',
					'../../static/images/mov/pic/4128339161.webp',
					'../../static/images/mov/pic/4128343275.webp',
					'../../static/images/mov/pic/4128345978.webp',
					'../../static/images/mov/pic/4128348689.webp'
				],
				review: [
					{
						id: 1,
						userName: 'Lisa',
						avatarUrl: '../../static/images/user/user1.jpg',
						content: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠',
						grade: 8.5,
						date: '3月9日',
						like: 999
					},
					{
						id: 2,
						userName: 'Lisa',
						avatarUrl: '../../static/images/user/user1.jpg',
						content: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠',
						grade: 8.5,
						date: '3月9日',
						like: 999
					},
					{
						id: 3,
						userName: 'Lisa',
						avatarUrl: '../../static/images/user/user1.jpg',
						content: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠',
						grade: 8.5,
						date: '3月9日',
						like: 999
					},
					{
						id: 4,
						userName: 'Lisa',
						avatarUrl: '../../static/images/user/user1.jpg',
						content: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠',
						grade: 8.5,
						date: '3月9日',
						like: 999
					}
				]
			}
		},
		components: {
			'scroll-list-item': scrollListItem,
			'review-item': reviewItem
		},
		methods: {
			collect(id) {
				this.flag = !this.flag
				//this.flag = id
				//:type="flag==item.id?true:false"
				//将对应id的影片加入收藏表
			},
			goAppraise(id) {
				uni.navigateTo({
					url: '../appraise/appraise'
				})
			}
		}
	}
</script>

<style lang="scss">
	.detail{
		.c{
			// #ifdef APP-PLUS
			margin-top: -6px;
			// #endif
			font-size: 20px;
			color: #ffca3e;
		}
		.top{
			margin-top: 10px;
			margin-left: 10px;
			padding-bottom: 10px;
			border-bottom: solid 1px #eaeaea;
			image{
				width: 95px;
				height: 140px;
				border-radius: 10px;
				box-shadow: 5px 5px 10px #bababa;
			}
			.tit{
				width: 250px;
				margin-left: 10px;
				margin-top: 5px;
				font-size: 22px;
				font-weight: bold;
				display: inline-block;
				text:nth-child(3){
					font-size: 15px;
				}
				.tit-score{
					display: flex;
				}
				.s{
					color: #C0C0C0;
					font-weight: normal;
					font-size: 13px;
				}
				.bot{
					display: flex;
					.collect{
						width: 120px;
						margin-left: 10px;
						text-align: center;
						border: 1px solid #eaeaea;
						border-radius: 5px;
						box-shadow: 5px 3px 10px #f3f3f3;
						font-size: 18px;
					}
				}
			}
		}
		.intro{
			margin: 10px 5px;
		}
		.stuff{
			.stuff-top{
				display: flex;
				view:first-child{
					margin-left: 10px;
				}
				view:last-child{
					position: absolute;
					right: 5px;
					margin-top: 5px;
					font-size: 15px;
				}
			}
			
		}
		
		.pics{
			margin-top: 10px;
			.b{
				margin-left: 10px;
			}
			.scroll-list{
				width: 100%;
				margin-top: 20px;
				white-space: nowrap;
				.scroll-item{
					display: inline-block;
					margin-right: 5px;
					.sroll-item-pics{
						width: 250px;
						height: 150px;
						overflow: hidden;
						image{
							width: 100%;
							height: 100%;
							object-fit: cover;
						}
					}
				}
			}
		}
		
		.review{
			margin-top: 10px;
			margin-left: 10px;
			.re-tit{
				font-size: 20px;
				font-weight: bold;
			}
		}
		.bottom{
			height: 50px;
			margin-top: 20px;
			text-align: center;
		}
	}
</style>
