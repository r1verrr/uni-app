<template>
	<view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		// 监听原生标题导航按钮点击事件
		onNavigationBarButtonTap(e){
			// index:0 取消按钮
			if(e.index == 0){
				uni.navigateBack({
					// 向上返回一级
					delta:1
				});
			}
			
		},
		// 监听搜索框文本变化
		onNavigationBarSearchInputChanged(e) {
			console.log(e.text)
		},
		// 监听点击搜索按钮事件
		onNavigationBarSearchInputConfirmed() {
			console.log(e.text)
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
