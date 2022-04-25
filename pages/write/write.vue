<template>
	<view class="write">
		<uni-easyinput v-model="content" type="textarea" placeholder="请输入评论内容(最多100个字)" :inputBorder="true"
		:clearable="false" maxlength="100" trim="both" autoHeight></uni-easyinput>
		<button class="post" type="default" @click="post">发布</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				content: '',
				time: ''
			}
		},
		methods: {
			post() {
				if(this.content=='')
					uni.showToast({
						icon: 'error',
						title: '内容不能为空'
					})
				else{
						this.time = this.dateFormat(Date.now())
						console.log(this.content, this.time)
					}
			},
			dateFormat(time) {
				let date = new Date(time);
				let year = date.getFullYear();
				let month = date.getMonth() + 1 < 10 ? '0' + (date.getMonth() + 1) : date.getMonth() + 1;
				let day = date.getDate() < 10 ? '0' + date.getDate() : date.getDate();
				let hours = date.getHours() < 10 ? '0' + date.getHours() : date.getHours();
				let minutes = date.getMinutes() < 10 ? '0' + date.getMinutes() : date.getMinutes();
				let seconds = date.getSeconds() < 10 ? '0' + date.getSeconds() : date.getSeconds();
			   
				// return year + "-" + month + "-" + day + " " + hours + ":" + minutes + ":" + seconds;
				return month + '月' + day + '日'
			}
		}
	}
</script>

<style lang="scss">
	.write{
		margin: 10px 10px;
		.post{
			width: 75%;
			margin-top: 10px;
			background: #d81e06;
			color: #fff;
		}
	}
</style>
