<template>
	<view>
		<!-- 导航栏 -->
		<uni-nav-bar fixed="flase">
			<view slot="default" style="padding: 70rpx; background-color: white; ">
				<text @click="gotovideo">视频</text></view>
			<view slot="default" style="padding: 70rpx; background-color: white; ">综合</view>
			<view slot="right">
			<i class="iconfont icon-bianji" @click="toPublish"></i>
			</view>
		</uni-nav-bar>
		
		<view class="search" @click="gotosearch">
			<mSearch :show="false"
			model="1"
			button="index"
			placeholder="查找精彩动态内容"
			>
			</mSearch>
			    {{val1}}
		</view>
		  
		<!-- 话题 -->
		<view class="NoticeBar">
			<text style="font-size: 30rpx; font-weight: bold;">话题</text>
			<uni-notice-bar text="传统文化" background-color="white" color="#33333" @click="getct"></uni-notice-bar>
			<uni-notice-bar text="大学生" background-color="white" color="#33333"></uni-notice-bar>
			<uni-notice-bar @getmore="getMore" :showGetMore="true" moreText="查看更多 >" 
			single="true" text="疑犯追踪" background-color="white" color="#33333" moreColor="#87CEEB"></uni-notice-bar>
		</view>
		
		<!-- 卡片 -->
		<view class="card1">
			<uni-card
				title="南工团委"
				extra="更多"
				thumbnail="/static/card/tx.png"
				mode="title"
				isFull="false"
				>
				南京工业职业技术大学2020年信仰公开课签到、签退二维码。
				<br/>
			<image src="../../static/card/01.jpg" style="width: 200rpx; height: 200rpx;" />
			<!-- 自定义底部按钮 -->
				<view style="display: flex; flex-direction: row; justify-content: space-around; align-items: center;">
					<view >
						<image src="../../static/card/05.png" style="width: 25px; height: 25px; background-color: white; justify-content: space-around; align-items: center" />
						<text style="align-items: center;">转发</text>
					</view>
					<view >
						<image src="../../static/card/04.png" style="width: 30px; height: 30px; background-color: white; justify-content: space-around; align-items: center" />
						<text style="align-items: center;">评论</text>
					</view>
					<view >
						<image src="../../static/card/03.png" style="width: 30px; height: 30px; background-color: white; justify-content: space-around; align-items: center" />
						<text style="align-items: center;colorP" @click="ad">10</text>
					</view>	
				</view>		
			</uni-card>
		</view>
		
		<view class="card2">
			<uni-card
				title="南工团委"
				extra="更多"
				thumbnail="/static/card/tx.png"
				mode="title"
				isFull="false"
				>
				南京工业职业技术大学第21届大学生校园文化艺术节——经典诵读大赛签到、签退二维码。
				<br/>
			<image src="../../static/card/01.jpg" style="width: 200rpx; height: 200rpx;" />
			<!-- 自定义底部按钮 -->
				<view style="display: flex; flex-direction: row; justify-content: space-around; align-items: center;">
					<view >
						<image src="../../static/card/05.png" style="width: 25px; height: 25px; background-color: white; justify-content: space-around; align-items: center" />
						<text style="align-items: center;">转发</text>
					</view>
					<view >
						<image src="../../static/card/04.png" style="width: 30px; height: 30px; background-color: white; justify-content: space-around; align-items: center" />
						<text style="align-items: center;">6</text>
					</view>
					<view >
						<image src="../../static/card/03.png" style="width: 30px; height: 30px; background-color: white; justify-content: space-around; align-items: center" />
						<text style="align-items: center;">15</text>
					</view>	
				</view>		
			</uni-card>
		</view>
		
		<view class="card3">
			<uni-card
				title="南工团委"
				extra="更多"
				thumbnail="/static/card/tx.png"
				mode="title"
				isFull="false"
				>
				南京工业职业技术学院（本科）第21届大学生校园文化艺术节——十佳歌手“云”演签到、签退二维码。
				<br/>
			<image src="../../static/card/01.jpg" style="width: 200rpx; height: 200rpx;" />
			<!-- 自定义底部按钮 -->
				<view style="display: flex; flex-direction: row; justify-content: space-around; align-items: center;">
					<view >
						<image src="../../static/card/05.png" style="width: 25px; height: 25px; background-color: white; justify-content: space-around; align-items: center" />
						<text style="align-items: center;">转发</text>
					</view>
					<view >
						<image src="../../static/card/04.png" style="width: 30px; height: 30px; background-color: white; justify-content: space-around; align-items: center" />
						<text style="align-items: center;">1</text>
					</view>
					<view >
						<image src="../../static/card/03.png" style="width: 30px; height: 30px; background-color: white; justify-content: space-around; align-items: center" />
						<text style="align-items: center;">8</text>
					</view>	
				</view>		
			</uni-card>
		</view>
		
	</view>			
</template>

<script>
	 import mSearch from '../../components/mehaotian-search/mehaotian-search.vue';
	import uniNavBar from '../../components/uni-nav-bar/uni-nav-bar.vue'
	export default {
		 components: {
			 uniNavBar,
			 mSearch
			 },
			data() {
			return {
				keyword: '',
				val1: '',
				
			}
		},

		methods: {
			getct (){
				uni.switchTab({
					url:"../index/index"
				})
			},
			gotovideo() {
			uni.navigateTo({
				url:"./video"
				})	
			},
			getMore() {
				uni.switchTab({
					url:"../index/index"
				})
			},
			gotosearch() {
				uni.navigateTo({
					url:"../search/search"
				})
			},
			toPublish(){
				uni.navigateTo({
					url:"./publish"
				})
			}
		},
	}
</script>

<style lang="stylus">
	.cardx
	  margin 15px
	  
		
</style>
