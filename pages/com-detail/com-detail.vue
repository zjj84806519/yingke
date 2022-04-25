<template>
	<view class="detail">
		<view v-for="item in article">
			<image class="banner" :src="item.imgUrl"></image>
			<view class="title">
				{{ item.title }}
			</view>
			<view class="text">
				<view class="user">
					<image :src="item.avatarUrl"></image>
					<view class="u-tit">
						<view class="b">{{ item.userName }}</view>
						<view class="u-tit-s">{{ item.date }}</view>
					</view>
				</view>
				<view class="content">
					<rich-text :nodes="item.content"></rich-text>
				</view>
				<view class="like" @click="like">
					<uni-icons :type="flag?'hand-up-filled':'hand-up'" size="25px" :color="flag?'#ff9500':''"></uni-icons>
					<view>{{ item.like }}</view>
				</view>
			</view>
		</view>	
		
		<view class="line"></view>
		<view class="review">
			<view class="r-top">
				<view class="b">全部评论</view>
			<view class="write" @click="goWrite">
				<uni-icons type="compose" size="30px"></uni-icons>
				<view>发评论</view>
			</view>
			</view>
			
			<review-item :review="reivew" :rev_like="rev_like"></review-item>
		</view>
		<view class="bottom">已加载全部评论</view>
	</view>
</template>

<script>
	import reviewItem from '../../components/review-item/review-item.vue'
	export default {
		data() {
			return {
				flag: 0,
				rev_like: [],
				article: [
					{
						id: 1,
						userName: 'Lisa',
						title: '蝙蝠侠',
						imgUrl: '../../static/images/banner3.webp',
						avatarUrl: '../../static/images/user/user1.jpg',
						content: '<p>我觉得扩展社交范围有一个很重要的因素，就是对负面评价的反应和情绪波动。</p><p>如果一个人在一个友善的环境中可以做到顺畅社交，但是换到一个严苛的环境中，马上被pua到自闭，就不算拥有稳定的社交能力。社牛都是完全不在意其他人的负面评价的，不论环境如何，就是自信，自己爽才是真的爽。</p><p>我真的很容易怀疑自己，别人攻击我，我会觉得，我是不是真的有这个毛病？我是不是改正一下比较好？但是有时候，别人说的，并不是事实。</p><p>所以，有辩证思维很重要，辩证思维是克服情绪化的有力武器；另外，最好深入地了解自己（通过观察自己的情绪，习惯，尤其是一些下意识下来），知道自己是什么样的性格，别人攻击反应，我才不是这样的。</p><p>所以，有辩证你的时候，你才能马上反应，我才。</p>',
						date: '3月9日',
						like: 999
					}
				],
				reivew: [
					{
						id: 1,
						userName: 'Lisa',
						avatarUrl: '../../static/images/user/user1.jpg',
						content: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠',
						date: '3月9日',
						like: 999
					},
					{
						id: 2,
						userName: 'Lisa',
						avatarUrl: '../../static/images/user/user1.jpg',
						content: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠',
						date: '3月9日',
						like: 999
					},
					{
						id: 3,
						userName: 'Lisa',
						avatarUrl: '../../static/images/user/user1.jpg',
						content: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠',
						date: '3月9日',
						like: 999
					},
					{
						id: 4,
						userName: 'Lisa',
						avatarUrl: '../../static/images/user/user1.jpg',
						content: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠',
						date: '3月9日',
						like: 999
					},
					{
						id: 5,
						userName: 'Lisa',
						avatarUrl: '../../static/images/user/user1.jpg',
						content: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠',
						date: '3月9日',
						like: 999
					},
					{
						id: 6,
						userName: 'Lisa',
						avatarUrl: '../../static/images/user/user1.jpg',
						content: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠',
						date: '3月9日',
						like: 999
					},
					{
						id: 7,
						userName: 'Lisa',
						avatarUrl: '../../static/images/user/user1.jpg',
						content: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠',
						date: '3月9日',
						like: 999
					},
					{
						id: 8,
						userName: 'Lisa',
						avatarUrl: '../../static/images/user/user1.jpg',
						content: '蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠蝙蝠侠',
						date: '3月9日',
						like: 999
					}
				]
			}
		},
		components: {
			'review-item': reviewItem
		},
		onLoad() {
			
		},
		methods: {
			like() {
				if(this.flag){
					this.article[0].like--
				}
				else
					this.article[0].like++
				this.flag = !this.flag
			},
			goWrite() {
				uni.navigateTo({
					url: '../write/write'
				})
			}
		}
	}
</script>

<style lang="scss">
	.detail{
		.banner{
			width: 100%;
		}
		.title{
			margin-left: 10px;
			font-size: 25px;
			font-weight: bold;
		}
		.text{
			margin: 10px 10px;
			background: #fcfcfc;
			border-radius: 10px;
			border: 1px solid #eaeaea;
			box-shadow: 5px 5px 10px #eaeaea;
			padding: 10px 10px;
			.user{
				margin-top: 15px;
				display: flex;
				image{
					width: 40px;
					height: 40px;
					border-radius: 50px;
					box-shadow: 5px 5px 10px #eaeaea;
				}
				.u-tit{
					margin-left: 10px;
					.u-tit-s{
						font-size: 13px;
						color: #C0C0C0;
					}
				}
			}
			.content{
				margin-top: 10px;
			}
			.like{
				display: flex;
			}
		}
		.line{
			height: 5px;
			background: #eaeaea;
		}
		.review{
			margin: 10px 10px;
			.r-top{
				display: flex;
				.write{
					position: absolute;
					right: 15px;
					display: inline-flex;
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
