<template>
	<view class="index-list">
		<view class="index-list1 u-f-ac u-f-jsb">
			<view class="u-f-ac">
				<image :src="item.userpic" mode="widthFix" lazy-load></image>
				{{item.username}}
			</view>
			<view class="u-f-ac" v-show="item.isguanzhu">
				<view class="icon iconfont icon-zengjia"></view>关注
			</view>	
		</view>
		<view class="index-list2">{{item.title}}</view>
		<view class="index-list3 u-f-ajc">
			<!-- 图片 -->
			<image :src="item.titlepic" mode="widthFix" lazy-load></image>
			<!-- 视频 -->
			<template v-if="item.type == 'video'">
				<view class="index-list-play icon iconfont icon-bofang"></view>
					<view class="index-list-playinfo">
						{{item.playnum}}  {{item.long}}
					</view>
		
			</template>
					</view>
		<view class="index-list4 u-f-ac u-f-jsb">
			<view class="u-f-ac">
				<view class="u-f-ac " :class="{'acitve':(item.infonum.index == 1)}" ><view class="icon iconfont icon-icon_xiaolian-mian"></view >{{item.infonum.dingnum}}</view>
				<view class="u-f-ac" :class="{'acitve':(item.infonum.index == 2)}"><view class="icon iconfont icon-kulian"></view>{{item.infonum.cainum}}</view>
			</view>
			<view class="u-f-ac">
				<view class="u-f-ac"><view class="icon iconfont icon-pinglun1"></view >{{item.commentnum}}</view>
				<view class="u-f-ac"><view class="icon iconfont icon-zhuanfa"></view>{{item.sharenum}}</view>
			</view>
		</view>
		
	</view>
</template>

<script>
	export default{
		props:{
			item:Object,
			index:Number
		}
	}
</script>

<style scoped>
	.index-list{
		padding: 20upx;
		border-bottom: 1upx solid #EEEEEE; 
		
	}
	.index-list1>view:first-child{
		color: #f8f2f7;
		}
		.index-list1>view:first-child image{
			width: 80upx;
			height: 80upx;
			border-radius: 100%;
			margin-right: 10upx; 
		}
		.index-list1>view:last-child{
		background: #F4F4F4;
		border-radius: 5upx;
		padding: 0 10upx;
		
		}
		.index-list1>view:last-child>view{
		
		}
	.index-list2{
		padding-top: 15upx;
		font-size: 32upx;
	}
	.index-list3{
			padding-top: 15upx;
			position: relative;
	}
	.index-list3>image{
		width: 100%;
		border-radius: 20upx;
	}
	.index-list4 view{
		color: #999999;
	}
	.index-list4{
		padding: 15upx 0;
	}
	.index-list4>view>view>view{
		margin-right: 10upx;
	}
	.index-list4>view>view:first-child{
		margin-right: 10upx;
	}
	.index-list-play{
		position: absolute;
		font-size: 80upx;
		color: #FFFFFF;
		
	}
	.index-list-playinfo{
		position: absolute;
		background: #555b40;
		color: #FFFFFF;
		bottom: 8upx;
		right: 8upx;
		border-radius: 40upx;
		font-size: 25upx;
		padding: 0 10upx;
		}
		.index-list4 .acitve,.index-list4 .acitve>view{
			color: #c8e323;
		}
</style>
