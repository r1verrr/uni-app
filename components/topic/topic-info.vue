<template>
	<view>
		
		<!-- 模糊背景 -->
		<view class="topic-bg">
			<image :src="item.titlepic" mode="aspectFill" lazy-load></image>
		</view>
		<!-- 话题信息 -->
		<view class="topic-info">
			<view class="topic-info-l u-f-ac">
				<image :src="item.titlepic" mode="widthFix" lazy-load></image>
				<view >#{{item.title}}#</view>
				</view>
			<view class="topic-info-c u-f-ac">
			<view>动态 {{item.totalnum}}</view>
			<view>今日 {{item.todaynum}}</view>
			</view>
			<view class="topic-info-b">
				{{item.desc}}
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		props:{
			item:Object
		}
	}
</script>

<style scoped>
	.topic-bg {
		width: 100%;
		height: 300upx;
		position: relative;
		overflow: hidden;
	}
	
	.topic-bg>image {
		width: 100%;
		position: absolute;
		/* 模糊背景 */
		filter: blur(10px);
	}
	
	.topic-info {
		padding: 0 20upx;
	}
	
	.topic-info-l {
		position: relative;
	}
	.topic-info-l>image{
		width: 150upx;
		height: 150upx;
		border-radius: 20upx;
		position: absolute;
		top: -75upx;
	}
	.topic-info-l>view{
		font-size: 40upx;
		margin-left: 150upx;
		flex: 1;
	}
	.topic-info-c {
		padding: 35upx 0 15upx 0;
	}
	.topic-info-c>view{
		color: #ceccce;
	}
	.topic-info-r {
		color: #a5a4a5;
		font-size: 35upx;
		padding-bottom: 10upx;
	}
</style>
