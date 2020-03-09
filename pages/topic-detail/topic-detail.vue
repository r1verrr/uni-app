<template>
	<view>
		<!-- 话题介绍 -->
		<topicInfo :item="topicInfo"></topicInfo>
		<!-- tabbar切换 -->
		<swiper-tab-head :tabBars="tabBars" :tabIndex="tabIndex" @tabtap="tabtap" scrollItemStyle="width:50%" scrollStyle="border-bottom:0"></swiper-tab-head>
	</view>
</template>

<script>
	import topicInfo from "../../components/topic/topic-info.vue"
	import swiperTabHead from "../../components/index/swiper-tab-head.vue";
	export default {
		components: {
			topicInfo,
			swiperTabHead
		},
		data() {
			return {
				topicInfo: {
					titlepic: "../../static/demo/topicpic/13.jpeg",
					title: "记忆",
					desc: "我是描述",
					totalnum: 200,
					todaynum: 100
				},
				tabIndex: 0,
				tabBars: [{
						name: "默认",
						id: "guanzhu"
					},
					{
						name: "最新",
						id: "zuixin"
					}
				]
			}
		},
		methods: {
			// 点击事件
			tabtap(index){
				this.tabIndex=index;
			},
			}
		}
</script>

<style>

</style>
