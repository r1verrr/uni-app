<template>
	<view>
		<!-- 话题介绍 -->
		<topicInfo :item="topicInfo"></topicInfo>
		<!-- tabbar切换 -->
		<swiper-tab-head :tabBars="tabBars" :tabIndex="tabIndex" @tabtap="tabtap" scrollItemStyle="width:50%" scrollStyle="border-bottom:0"></swiper-tab-head>
		<!-- 列表 -->
		<view class="topic-detail-list">
			<block v-for="(item,index) in tablist " :key="index">
				<template v-if="tabIndex==index">
					<!-- 列表 -->
					<block v-for="(list,listindex) in item.list" :key="listindex">
						<common-list :item="list" :index="listindex"></common-list>
					</block>
					<!-- 上拉加载 -->
				</template>
			</block>
		</view>
		
	</view>
</template>

<script>
	import topicInfo from "../../components/topic/topic-info.vue"
	import swiperTabHead from "../../components/index/swiper-tab-head.vue";
	import commonList from "../../components/common/common-list.vue"
	export default {
		components: {
			topicInfo,
			swiperTabHead,
			commonList
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
				],
				tablist:[
					{loadtxet:"上拉加载更多",
						list:[
							{
							userpic: "../../static/demo/userpic/12.jpg",
							username: "嘿嘿",
							sex: 0, //0 男 1 女 
							age: 25,
							isguanzhu: false,
							title: "我是标题",
							titlepic: "",
							video: false,
							share: false,
							path: "厦门 湖里",
							sharenum: 20,
							commentnum: 30,
							goodnum: 20
						}
						
						]}
					
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
