<template>
	<view>
		<!-- 自定义导航栏 -->
		<uni-nav-bar :statusBar="true" rightText="发布" left-icon="back" @click-left="back" @click-right="submit">
			<view class="u-f-ajc" @tap="changelook">
				所有人可见
				<view class="icon iconfont icon-xialazhankai"></view>
			</view>
		</uni-nav-bar>
	</view>
</template>

<script>
		import uniNavBar from "../../components/uni-nav-bar/uni-nav-bar.vue";
		
	export default {
		data() {
			return {
				
			}
		},
		components:{
			uniNavBar
		},
		methods: {
			// 返回
			back(){
				uni.navigateBack({
					delta:1
				})
			},
			// 发布
			submit(){
				console.log("发布")
			},
			// 隐私
			changelook(){
				console.log("隐私")
			}
			
		},
		onNavigationBarButtonTap(e){
			// index:0 取消按钮
			if(e.index == 0){
				uni.navigateBack({
					// 向上返回一级
					delta:1
				});
			}
			
		},
	}
</script>

<style>

</style>
