<template>
	<view>
		<!-- 顶部按钮区域 -->
		<view class="d-top">
			<view class="close" @click="close">
				<uni-icons type="closeempty" size="30px"></uni-icons>
			</view>
			<view class="scan">
				<uni-icons type="scan" size="30px" @click="scan"></uni-icons>
			</view>
		</view>
		<!-- 用户信息区域 -->
		<view class="user">
			<image class="avatar" src="../../static/images/user/user1.jpg"></image>
			<view class="name">
				<view class="b">Lisa</view>
				<view class="s">账号名：admin001</view>
				<view class="dec">
					<view>关注7</view>
					<view class="line"></view>
					<view>粉丝0</view>
				</view>
			</view>
		</view>
		<!-- 功能列表区域 -->
		<view class="func">
			<view class="func-item" @click="golist">
				<image src="../../static/icons/file-common.png"></image>
				<view>我的收藏</view>
			</view>
			<view class="func-item" @click="goHistory">
				<image src="../../static/icons/time.png"></image>
				<view>浏览历史</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:"drawer-content-item",
		data() {
			return {
				
			};
		},
		methods: {
			golist() {
				uni.navigateTo({
					url: '../mov-list/mov-list'
				})
			},
			close() {
				this.$emit('closeDrawer')
			},
			scan() {
				this.$emit('scan')
			},
			goHistory() {
				uni.navigateTo({
					url: '../history/history'
				})
			}
		}
	}
</script>

<style lang="scss">
	.d-top{
		padding: 20px 10px 10px 10px;
		display: flex;
		text-align: center;
		.close{
			width: 40px;
			height: 40px;
			line-height: 40px;
			position: absolute;
			left: 10px;
		}
		.scan{
			width: 40px;
			height: 40px;
			position: absolute;
			right: 10px;
			float: right;
			line-height: 40px;
		}
	}
	.user{
		display: flex;
		margin: 50px 10px 10px 10px;
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
	.func{
		margin-left: 10px;
		.func-item{
			width: 112px;
			display: flex;
			margin-top: 20px;
			line-height: 30px;
			font-size: 18px;
			image{
				width: 30px;
				height: 30px;
			}
			view{
				margin-left: 10px;
			}
		}
	}
</style>
