<template>
	<view class="dl">
		<scroll-view scroll-x class="uni-swiper-tab" :style="scrollStyle">
			<block v-for="(tab,index) in tabBars" :key="tab.id">
				<view class="swiper-tab-list" 
				      :class="{'active':tabIndex == index}"
							@tap="tabtap(index)"
							:style="scrollItemStyle">
					{{tab.name}}
					<view class="swiper-tab-line"></view>
				</view>
			</block>
		</scroll-view>
	</view>
</template>

<script>
	export default{
		props:{
			tabBars:Array,
			tabIndex:Number,
			scrollStyle:{
				type:String,
				default:""
			},
			scrollItemStyle:{
				type:String,
				default:""
			}
			
		},
		methods:{
			tabtap(index){
				this.$emit('tabtap',index);
			},
		}
	}
</script>
		
<style>
	.dl{
		border-bottom: 1upx solid #EEEEEE;
		width: 100%;
		white-space: nowrap;
		line-height: 100upx;
		height: 100upx;
		border-bottom: 1px solid #c8c7cc;
	}
	.swiper-tab-list{
		color: #989798;
		font-weight: bold;
	}
	.uni-tab-bar .active{
		color: #1d1c1d;
	}
	.active .swiper-tab-line{
		border-bottom: 6upx solid #ece579;
		width: 70upx;
		margin: auto;
		border-top: 6upx solid #FEDE33;
		border-radius: 20upx;	
	}
</style>
