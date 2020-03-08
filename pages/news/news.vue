<template>
	<view>
		<!-- 自定义导航栏 -->
		<newsNavBar :tabBars="tabBars" :tabIndex="tabIndex" @change-tab="changeTab"></newsNavBar>

		<view class="uni-tab-bar">
			<!-- style不能用upx -->
			<swiper class="swiper-box" :style="{height:swiperheight+'px'}" :current="tabIndex" @change="tabChange">
				<!-- 关注 -->
				<swiper-item>
					<scroll-view scroll-y class="list" @scrolltolower="loadmore">

						<block v-for="(item,index) in guanzhu.list" :key="index">
							<common-list :item="item" :index="index"></common-list>
						</block>
						<!-- 上拉加载 -->
						<load-more :loadtext="guanzhu.loadtext"></load-more>
					</scroll-view>

				</swiper-item>
				<!-- 话题 -->
				<swiper-item>
					<scroll-view scroll-y class="list">
						<!-- 搜索框 -->
						<view class="serch-input">
							<input class="uni-input" placeholder="搜索内容" placeholder-class="topic-search icon iconfont icon-sousuo" />
						</view>
						<!-- 轮播图 -->
						<swiper class="topic-swiper" :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
							<block v-for="(item,index) in topic.swiper" :key="index">
								<swiper-item>
									<image :src="item.src" mode="widthFix" lazy-load></image>
								</swiper-item>
							</block>
							

						</swiper>
						<!-- 热门分类 -->
						<view class="topic-nav">
							<view class="u-f-ac u-f-jsb">
								<view > 热门分类</view>
								<view class="u-f-ajc">更多<view class="icon iconfont icon-jinru "></view></view>
							</view>
							<view class="u-f-ac">
								<view>最新</view>
								<view>游戏</view>
								<view>打卡</view>
								<view>故事</view>
								<view>喜爱</view>
								<view>xx</view>
							</view>
							
						</view>
						<!-- 最近更新 -->

						话题

					</scroll-view>

				</swiper-item>
			</swiper>
		</view>

	</view>
</template>

<script>
	import newsNavBar from '../../components/news/new-nav-bar.vue'
	import commonList from "../../components/common/common-list.vue"
	import loadMore from "../../components/common/load-more.vue"
	export default {
		components: {
			newsNavBar,
			commonList,
			loadMore
		},
		data() {
			return {
				swiperheight: 500,
				tabIndex: 1,
				tabBars: [{
						name: "关注",
						id: "guanzhu"
					},
					{
						name: "话题",
						id: "huati"
					}
				],
				guanzhu: {
					loadtext: "上拉加载更多",
					list: [
						// 文字
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
						},

						// 图文
						{
							userpic: "../../static/demo/userpic/12.jpg",
							username: "嘿嘿",
							sex: 0, //0 男 1 女 
							age: 25,
							isguanzhu: false,
							title: "我是标题",
							titlepic: "../../static/demo/datapic/13.jpg",
							video: false,
							share: false,
							path: "厦门 湖里",
							sharenum: 20,
							commentnum: 30,
							goodnum: 20
						},

						// 视频
						{
							userpic: "../../static/demo/userpic/12.jpg",
							username: "嘿嘿",
							sex: 0, //0 男 1 女 
							age: 25,
							isguanzhu: false,
							title: "我是标题",
							titlepic: "../../static/demo/datapic/13.jpg",
							video: {
								looknum: "20w",
								long: "2:47"
							},
							share: false,
							path: "厦门 湖里",
							sharenum: 20,
							commentnum: 30,
							goodnum: 20
						},
						// 分享
						{
							userpic: "../../static/demo/userpic/12.jpg",
							username: "嘿嘿",
							sex: 0, //0 男 1 女 
							age: 25,
							isguanzhu: false,
							title: "我是标题",
							titlepic: "",
							video: false,
							share: {
								title: "我是分享的标题",
								titlepic: "../../static/demo/datapic/14.jpg"
							},
							path: "厦门 湖里",
							sharenum: 20,
							commentnum: 30,
							goodnum: 20
						},
					]
				},
				topic:{
					swiper:[
					{ src:"../../static/demo/banner2.jpg" },
					{ src:"../../static/demo/banner2.jpg" },
					{ src:"../../static/demo/banner2.jpg" },
					]
				}
					
			}
		},
		onLoad() {
			uni.getSystemInfo({
				success: (res) => {
					let height = res.windowHeight - uni.upx2px(100)
					this.swiperheight = height;
				}
			})
		},
		methods: {
			// 点击切换
			changeTab(index) {
				this.tabIndex = index;
			},
			// 滑动切换
			tabChange(e) {
				this.tabIndex = e.detail.current;
			},
			// 上拉加载
			loadmore() {
				if (this.guanzhu.loadtext != "上拉加载更多") {
					return;
				}
				// 修改状态
				this.guanzhu.loadtext = "加载中...";
				// 获取数据
				setTimeout(() => {
					//获取完成
					let obj = {
						userpic: "../../static/demo/userpic/12.jpg",
						username: "嘿嘿",
						sex: 0, //0 男 1 女 
						age: 25,
						isguanzhu: false,
						title: "我是标题",
						titlepic: "../../static/demo/datapic/13.jpg",
						video: {
							looknum: "20w",
							long: "2:47"
						},
						share: false,
						path: "厦门 湖里",
						sharenum: 20,
						commentnum: 30,
						goodnum: 20
					};
					this.guanzhu.list.push(obj);
					this.guanzhu.loadtext = "上拉加载更多";
				}, 1000);
			},

			// 点击事件
		}
	}
</script>

<style scoped>
.serch-input{
	padding: 20upx;
}
.serch-input>input{
	background: #F4F4F4;
	border-radius: 10upx;
}
.topic-search{
	display: flex;
	justify-content: center;
	font-size: 28upx;
}
	
.topic-swiper{
	padding: 0 20upx 40upx 40upx;
}
.topic-swiper>image{
	width: 100%;
	border-radius: 10upx;
}

.topic-nav{
	border-bottom: 1upx solid #EEEEEE;
	border-top: 1upx solid  #EEEEEE;
	padding: 20upx;
}
.topic-nav>view:first-child{
	margin-bottom: 10upx;
	
}
.topic-nav>view:first-child view{
	color:#9E9E9E;
	border: 1upx solid;
}
.topic-nav>view:first-child>view:first-child{
	
}
.topic-nav>view:last-child>view{
	flex: 1;
	background: #dddddd;
	color: #a09fa0;
	border-radius: 10upx;
	margin: 0 10upx;
	text-align: center;
}
</style>
