<template>
	<view>
		<!-- 自定义导航栏 -->
		<uni-nav-bar :statusBar="true"  @click-right="openAdd">
			<!-- 左边 -->
			<block slot="left">
				<view class="nav-left">
					<view class="icon iconfont icon-qiandao">
</view>
				</view>
				
			</block>
			<!-- 中间 -->
			<block >
				<view class="nav-tab-bar u-f-ajc">
					
					<block v-for="(tab,index) in tabBars" :key="tab.id" >
						<view class="u-f-ajc" :class="{'active':tabIndex==index}" @tap="changeTab(index)">
							{{tab.name}}
							<view v-if="(tabIndex==index)" class="nav-tab-bar-line"></view>
						</view>
					</block>
					
					
				
				</view>
			</block>
			<!-- 右边 -->
			<block slot= "right">
				<view class="nav-right u-f-ajc">
					<view class="icon iconfont icon-bianji1"></view>
				</view>
				
			</block>
		</uni-nav-bar>
		<view class="ss">
			
		</view>
	</view>
</template>

<script>
	import uniNavBar from "../../components/uni-nav-bar/uni-nav-bar.vue";
	export default {
		components:{
			uniNavBar
		},
		data() {
			return {
				tabIndex:0,
				tabBars:[
					{name:"关注",id:"guanzhu"},
					{name:"话题",id:"huati"}
				]
			}
		},
		methods: {
			changeTab(index){
				this.tabIndex=index
			},
			openAdd(){
				uni.navigateTo({
					url:'../add-input/add-input',
				})
			}
		}
	}
</script>

<style>

.nav-left>view, .nav-right>view{
	font-size: 45upx;
}
.nav-left>view{
	color: #e9a459;
}
.nav-left{
	margin-left: 16upx;
}
	.nav-right{
		width: 100%;
	}
.nav-tab-bar{
	width: 100%;
	margin-left: -20upx;
	position: relative;
	
}
.nav-tab-bar>view{
	font-size: 33upx;
	padding: 0 15upx;
	font-weight: bold;
	color:#9fa09f
}
.active{
	color: #333333!important;
}

.nav-tab-bar-line{
	border-bottom: 5upx solid #fdd12c;
	border-top: 5upx solid #fdd12c;
	width:70upx;
	border-radius: 20upx;
	position: absolute;
	bottom:12upx;
}

</style>
