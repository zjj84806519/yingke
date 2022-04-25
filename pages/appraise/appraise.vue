<template>
	<view class="appraise">
		<view class="grade">
			<view v-show="!rateValue">点击星星评分</view>
			<view v-show="rateValue==1">很差</view>
			<view v-show="rateValue==2">较差</view>
			<view v-show="rateValue==3">还行</view>
			<view v-show="rateValue==4">推荐</view>
			<view v-show="rateValue==5">力荐</view>
			<uni-rate touchable v-model="rateValue"></uni-rate>
		</view>
		<uni-easyinput type="textarea" v-model="review" placeholder="说说看过之后的感受吧" placeholderStyle="font-size:15px;"
					   trim="both" :clearable="false"></uni-easyinput>
		<button @click="getReview(rateValue,review)">确认</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				rateValue: 0,
				review: ''
			}
		},
		methods: {
			getReview(rateValue,review) {
				if(review.length!=0&&rateValue!=0){
					console.log(rateValue,review)
					// this.$emit('getReview', this.rateValue, this.review)
				}
					
				else
					uni.showToast({
						title: '请点击评分或输入内容',
						icon: 'none'
					})
			}
		}
	}
</script>

<style lang="scss">
	.appraise{
		.grade{
			text-align: center;
			vertical-align: middle;
			color: #C0C0C0;
		}
	}
</style>
