<template>
	<view class="register">
		<view class="input">
			<view class="name">
				<view>昵称</view>
				<uni-easyinput v-model="name" maxlength="11" confirmType="下一步" focus placeholder="请输入昵称"></uni-easyinput>
				<!-- errormessage -->
			</view>
			<view class="userName">
				<view>账号</view>
				<uni-easyinput v-model="userName" maxlength="11" confirmType="下一步" focus placeholder="请输入账户名"></uni-easyinput>
				<!-- errormessage -->
			</view>
			<view class="password">
				<view>密码</view>
				<uni-easyinput type="password" v-model="password" maxlength="11" placeholder="请输入密码"></uni-easyinput>
			</view>
		</view>
		<view class="button">
			<button type="default" hover-class="btn2" @click="register(name,userName,password)">注册</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				name: '',
				userName: '',
				password: ''
			}
		},
		methods: {
			register(name,userName,password) {
				console.log(name,userName,password)
				uni.showToast({
					title: '注册成功'
				})
			}
		}
	}
</script>

<style lang="scss">
	.register{
		margin: 10px 10px;
		font-size: 15px;
		.input{
			.userName{
				
			}
			.password{
				
			}
		}
		.button{
			margin-top: 20px;
			display: flex;
			button{
				width: 95%;
				background-color: #d81e06;
				color: #fff;
			}
			.btn2{
				background-color: #710e03;
			}
		}
	}
</style>
