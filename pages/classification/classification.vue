<template>
	<view class="class">
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
		
		<!-- 分类栏区域 -->
		<view class="tit">分类</view>
		<view class="row">
			<view class="list" v-for="item in genre1" :key="item.id" @click="goList(item.id)">
				<view class="list-item">
					<image :src="item.icon"></image><br>
					<text>{{ item.title }}</text>
				</view>
			</view>
		</view>
		<view class="row">
			<view class="list" v-for="item in genre2" :key="item.id" @click="goList(item.id)">
				<view class="list-item">
					<image :src="item.icon"></image><br>
					<text>{{ item.title }}</text>
				</view>
			</view>
		</view>
		<view class="row">
			<view class="list" v-for="item in genre3" :key="item.id" @click="goList(item.id)">
				<view class="list-item">
					<image :src="item.icon"></image><br>
					<text>{{ item.title }}</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import searchItem from '../../components/search-item/search-item.vue'
	export default {
		data() {
			return {
				genre1: [
					{
						id: 1,
						icon: '../../static/icons/classify/action.png',
						title: '动作'
					},
					{
						id: 2,
						icon: '../../static/icons/classify/comedy.png',
						title: '喜剧'
					},
					{
						id: 3,
						icon: '../../static/icons/classify/romantic.png',
						title: '爱情'
					},
					{
						id: 4,
						icon: '../../static/icons/classify/sci-fi.png',
						title: '科幻'
					}
				],
				genre2: [
					{
						id: 5,
						icon: '../../static/icons/classify/cartoon.png',
						title: '动画'
					},
					{
						id: 6,
						icon: '../../static/icons/classify/adventure.png',
						title: '冒险'
					},
					{
						id: 7,
						icon: '../../static/icons/classify/fantasy.png',
						title: '奇幻'
					},
					{
						id: 8,
						icon: '../../static/icons/classify/war.png',
						title: '战争'
					}
				],
				genre3: [
					{
						id: 9,
						icon: '../../static/icons/classify/horror.png',
						title: '恐怖'
					},
					{
						id: 10,
						icon: '../../static/icons/classify/thriller.png',
						title: '惊悚'
					},
					{
						id: 11,
						icon: '../../static/icons/classify/series.png',
						title: '电视剧'
					},
					{
						id: 12,
						icon: '../../static/icons/classify/documentary.png',
						title: '纪录片'
					}
				]
			}
		},
		components: {
			'search-item': searchItem,
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
			goList(id) {
				console.log(id)
				uni.navigateTo({
					url: '../mov-list/mov-list',
					//+id
				})
			}
		}
	}
</script>

<style lang="scss">
	.class{
		.drawer{
			.close {
				padding: 10px;
			}
		}
		.tit{
			margin-top: 10px;
			margin-left: 10px;
			font-size: 22px;
			font-weight: bold;
		}
		.row{
			display: flex;
			margin-top: 20px;
			.list{
				margin: 0 auto;
				white-space: normal;
				.list-item{
					width: 70px;
					height: 70px;
					padding-top: 5px;
					text-align: center;
					background: #fff;
					border-radius: 10px;
					box-shadow: 5px 5px 10px #eaeaea;
					image{
						width: 40px;
						height: 40px;
					}
				}
				
			}
		}
	}
	
	
</style>
