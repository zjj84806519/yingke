<template>
	<view>
		<view class="review-list" v-for="(item,index) in review" :key="item.id">
			<view class="top">
				<image :src="item.avatarUrl"></image>
				<view class="u-tit">
					<view class="b">{{ item.userName }}</view>
					<view class="u-tit-s">
						<view>
							<uni-rate v-show="item.grade" :value="item.grade*0.5" size="15px"></uni-rate>
						</view>
						<view>{{ item.date }}</view>
					</view>
				</view>
			</view>
			<view class="content">{{ item.content }}</view>
			<view class="like" @click="like(index)">
				<uni-icons :type="rev_like[index]==1?'hand-up-filled':'hand-up'" size="25px" :color="rev_like[index]?'#ff9500':''"></uni-icons>
				<view>{{ item.like }}</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props: ['review','rev_like'],
		name:"review-item",
		data() {
			return {
				
			};
		},
		methods: {
			like(index) {
				if(this.rev_like[index]){
					this.rev_like[index] = 0
					this.review[index].like--
				}
				else{
					this.rev_like[index] = 1
					this.review[index].like++
				}
				// console.log(this.rev_like)
				this.$forceUpdate()
			}
		}
	}
</script>

<style lang="scss">
	.review-list{
		background: #fcfcfc;
		border-radius: 10px;
		border: 1px solid #eaeaea;
		box-shadow: 5px 5px 10px #eaeaea;
		margin: 10px 10px 10px 0px;
		padding: 10px 10px;
		.top{
			display: flex;
			image{
				width: 40px;
				height: 40px;
				border-radius: 50px;
			}
			.u-tit{
				margin-left: 10px;
				.u-tit-s{
					display: flex;
					font-size: 13px;
					color: #C0C0C0;
				}
			}
		}
		.content{
			
		}
		.like{
			width: 25px;
			display: flex;
		}
	}
</style>
