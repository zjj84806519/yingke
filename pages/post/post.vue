<template>
	<view>
		<view class="input">
			<uni-easyinput v-model="title" type="text" :inputBorder="false" placeholder="请输入贴子标题(5-31个字)" 
			placeholderStyle="font-size:15px;font-weight:bold" :clearable="false" style="border-bottom: 1px solid #eaeaea;"
			maxlength="31" trim="both"></uni-easyinput>
			<uni-easyinput v-model="content" type="textarea" placeholder="请输入贴子内容(最多255个字)" :inputBorder="false" 
			:clearable="false" maxlength="255" trim="both"></uni-easyinput>
		</view>
		<view class="pics">
			<view class="imgArr" v-for="(item,index) in imgArr">
				<view class="imgArritem">
					<uni-icons class="close" type="close" size="25px" color="#242424" style="opacity: 0.5;" 
					@click="splice(index)"></uni-icons>
					<image :src="item" @click="previewImg(index)"></image>
				</view>
			</view>
			<view class="add" hover-class="added" v-show="imgArr.length!=1" @click="chooseImg(imgArr)">
				<uni-icons type="plusempty" size="40px"></uni-icons>
			</view>
		</view>
		<button class="post" hover-class="posted" type="default" @click="post">发布</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: '',
				content: '',
				imgArr: []
			}
		},
		methods: {
			chooseImg(res) {
				uni.chooseImage({
					count: 1,
					success:res =>{
						// console.log(res)
						this.imgArr = res.tempFilePaths
					}
				})
			},
			previewImg(current) {
				uni.previewImage({
					current,
					urls: this.imgArr
				})
			},
			post() {
				if(this.title=='')
					uni.showToast({
						icon: 'error',
						title: '标题不能为空'
					})
				else if(this.content=='')
					uni.showToast({
						icon: 'error',
						title: '内容不能为空'
					})
				else
					console.log(this.title,this.content,this.imgArr)
			},
			splice(index) {
				this.imgArr.splice(index,1)
			}
		}
	}
</script>

<style lang="scss">
	.input{
		margin: 10px 10px;
	}
	.pics{
		width: 355px;
		margin: 10px 20px;
		.imgArr{
			display: inline-flex;
			margin: 5px 5px;
			.imgArritem{
				width: 100px;
				height: 100px;
				overflow: hidden;
				.close{
					width: 23px;
					height: 22px;
					position: absolute;
					margin-left: 75px;
					z-index: 999;
					background: #8d8d8d;
					opacity: 0.3;
					border-radius: 50px;
				}
				image{
					width: 100%;
					height: 100%;
					border-radius: 10px;
					object-fit: cover;
				}
			}
			
		}
		.add{
			width: 100px;
			height: 100px;
			border: 1px dashed #ccc;
			border-radius: 10px;
			text-align: center;
			line-height: 100px;
			display: block;
		}
		.added{
			background: #fcfcfc;
		}
	}
	.post{
		width: 75%;
		background: #d81e06;
		color: #fff;
	}
	.posted{
		background: #bf1202;
	}
</style>
