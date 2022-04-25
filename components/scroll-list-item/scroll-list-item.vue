<template>
	<view>
		<scroll-view class="scroll-list" scroll-x="true" >
			<view class="scroll-item" v-for="(item,index) in array" :key="index">
				<view class="pics">
					<image :src="item.imgUrl" mode="aspectFill" @click="navigator(item.id)" ></image>
				</view>
				<view>{{ item.second }}</view>
				<view class="s-third">
					<view v-show="item.third>0?true:false">
						<uni-rate style="margin-top: 5px;" :readonly="true" :value="item.third" size="13px"/>
					</view>
					<view :title="item.third" :class="item.third>0?'third':'text'">{{ item.third }}</view>
				</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	import unirateItem from '../uni-rate/uni-rate.vue'
	export default {
		props: ['array'],
		name:"scroll-list-item",
		data() {
			return {
				rateValue: 0
			};
		},
		components: {
			'uni-rate': unirateItem
		},
		methods: {
			navigator(id){
				this.$emit('scrollItemClick',id)
			}
		}
	}
</script>

<style lang="scss">
	.scroll-list{
		width: 100%;
		margin-top: 20px;
		overflow: hidden;
		white-space: nowrap;
		.scroll-item{
			display: inline-block;
			margin-left: 10px;
			.pics{
				width: 95px;
				height: 140px;
				object-fit: hidden;
				image{
					width: 100%;
					height: 100%;
					border-radius: 10px;
					object-fit: cover;
				}
			}
			.s-third{
				display: flex;
				.third{
					font-size: 15px;
					color: #ffca3e;
				}
				.text{
					width: 95px;
					overflow: hidden;
					text-overflow: ellipsis;
				}
			}
			
		}
		// overflow-x: hidden;
	}
</style>
