<template>
	<view class="login">
		<view class="input">
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
			<button type="default" plain hover-class="btn1" @click="goRegister">注册</button>
			<button type="default" hover-class="btn2">登录</button>
		</view>
	</view>
</template>

<script>
	import unieasyinputItem from '../../components/uni-easyinput/uni-easyinput.vue'
	export default {
		data() {
			return {
				userName: '',
				password: ''
			}
		},
		components: {
			'uni-easyinput': unieasyinputItem
		},
		methods: {
			goRegister() {
				uni.navigateTo({
					url: '../register/register'
				})
			}
		}
	}
</script>

<style lang="scss">
	.login{
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
			button:first-child{
				width: 45%;
				color: #d81e06;
				border: 1px solid #d81e06;
			}
			button:last-child{
				width: 45%;
				background-color: #d81e06;
				color: #fff;
			}
			.btn1{
				color: #710e03;
				border: 1px solid #710e03;
			}
			.btn2{
				background-color: #710e03;
			}
		}
	}
</style>
