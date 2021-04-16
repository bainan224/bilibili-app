<template>
	<view>
       <view class="uni-padding-wrap ">
			<segmented-control :current="currentItem" :values="items" :style-type="'text'" :active-color="'#f3a8cb'"
				@clickItem="onClickItem" style="margin-top: 45px;"/>
		</view>
		<view class="content">
			<!-- 选项卡1的内容 -->
			<view v-if="currentItem === 0">
				
				<view class="input-view mt-0" style="position: relative;">
					<view class="iconfont icon-wddl" type="search" style="position: absolute; margin-left: 17px; margin-top: -4px;"></view>
					<input
						class="nav-bar-input bg-hover-light rounded-circle pl-5 ml-3 mt-2" type="text"
						placeholder="搜索你感兴趣的频道" @click="search" v-model="keyword">
				</view>
				
				<view class="top">
						   <view class="flex flex-column" style="width: 20%;align-items: center;">
							   <image class="img" src="../../static/image/index2/index/ic_launcher_round.png"/>
							   <text class="text-muted">哔哩哔哩</text>
						   </view>
						   <view class="flex flex-column" style="width: 10%;align-items: center;">
						   	    <image class="img" src="../../static/image/index2/index/ic_share_weibo.png"/>
						   		<text class="text-muted">微博</text>
						   </view>
						   <view class="flex flex-column" style="width: 20%;align-items: center;">
						   		<image class="img" src="../../static/image/index2/index/ic_share_wechat_moments.png"/>
						   		<text class="text-muted">微信朋友圈</text>
						   </view>
						   <view class="flex flex-column" style="width: 16%;align-items: center;">
						   		<image class="img" src="../../static/image/index2/index/ic_share_qq.png"/>
						   		<text class="text-muted">QQ空间</text>
						   </view>
						   <view class="flex flex-column " style="width: 15%;align-items: center;">
						   		<image class="img img3" src="../../static/image/index2/index/tjdy.png"/>
						   		<text class="text-muted">添加订阅</text>
						   </view>
				</view>
				
				<view class="present">
					<view>
					<text class="text-muted" style="margin-left: 20rpx;">最近看过的频道</text>
					
					</view>
				</view>
				
				
				<view>
					<view style="height: 30px; display: flex; flex-direction: row;">
					<view class="text-muted mt-2" style="margin-left: 20rpx;">热门频道 </view>
					<view class=" text-muted font-sm mt-2" style="margin-left: 450rpx;">换一换</view>
					<view class="iconfont icon-shuaxin ml-1 " style="font-size: 23px;"></view>
					</view>
					<view class="top">
							   <view class="flex flex-column" style="width: 18%;align-items: center;">
							   	    <image class="img" src="../../static/image/index2/index/bili_socialize_sina.png"/>
							   		<text class="text-muted">微博</text>
							   </view>
							   <view class="flex flex-column" style="width: 20%;align-items: center;">
							   		<image class="img" src="../../static/image/index2/index/bili_socialize_wx_moment.png"/>
							   		<text class="text-muted">微信朋友圈</text>
							   </view>
							   <view class="flex flex-column" style="width: 20%;align-items: center;">
							   		<image class="img" src="../../static/image/index2/index/bili_socialize_wx_chat.png"/>
							   		<text class="text-muted">微信</text>
							   </view>
							   <view class="flex flex-column" style="width: 20%;align-items: center;">
							   		<image class="img" src="../../static/image/index2/index/bili_socialize_qq_chat.png"/>
							   		<text class="text-muted">QQ</text>
							   </view>
							   <view class="flex flex-column" style="width: 20%;align-items: center;">
							   		<image class="img" src="../../static/image/index2/index/bili_socialize_im.png"/>
							   		<text class="text-muted">热聊</text>
							   </view>
					</view>
					<view class="present top">
						<image class="img2 ml-2" src="../../static/image/index2/index/bili_socialize_wx_chat.png"/>
						<view class="flex flex-column ml-2" style="width: 30%;">
							<text class="  font" >微信聊天</text>
							<text class=" text-muted font-sm" >新增拍一拍功能</text>
						</view>
						<view class="flex justify-center align-center" style="background-color: #f3a8cb; height: 50rpx; width: 150rpx; border-radius: 10%;margin-left: 80px; ">
							<text class="text-white">去看看</text>
						</view>
					</view>	
					
					
					
					
					
				</view>
				
				<view v-for="(archive,index) in archives" :key="index">
					<view v-for="(channel,index) in channels" :key="index" >
					
				<card-list :channel="channel" :archive="archive"></card-list>
				</view>
				</view>
			</view>
		</view>

		

	</view>
</template>

<script>
	import SegmentedControl from '@/components/segmented-control/segmented-control.vue'
	import cardList from '@/components/card-list/card-list.vue'
	export default {
		components: {
			SegmentedControl
		},
		data() {
			return {
				channels: [],
				archives: [],
				items: ['频道', '分区'],
				currentItem: 0,
				updateVData: '',
				keyword: ''
			};
		},
		
		methods: {

			search() {
				uni.navigateTo({
					url:'../search/search'
				})
			},
			onClickItem(e) {
				if (this.currentItem !== e.currentIndex) {
					this.currentItem = e.currentIndex
				}
			},
			onLoad() {
				uni.request({
					url: 'https://api.bilibili.com/x/web-interface/web/channel/category/channel_arc/list?id=0',
					success: (res) => {
						console.log(res);
						console.log(res.data.data.archive_channels);
						this.channels = res.data.data.archive_channels
						for (let i = 0; i < this.channels.length; i++) {
							this.archives = res.data.data.archive_channels[i].archives
							console.log(this.archives);
						}
			
					}
				});
			},

			
		}

	}
</script>

<style scoped>
	page {
		height: 100%;
	}
    .top{
		display: flex;
		flex-direction: row ;
		width: 100%;
		align-items: center;
		margin-top: 20rpx;
	}
	.img{
		background-color: #fff;
		width: 100rpx;
		height: 100rpx;
	}
	.img2{
		background-color: #E6E6E6;
		margin-top: 5px;
		margin-bottom: 5px;
		
		width: 80rpx;
		height: 80rpx;
	}
	.img3{
		border-radius: 100%;
	}
	.present{
		margin-left: 15px;
		margin-right: 15px;
		border-radius: 5%;
		background-color: #e6e6e6;
	}
	.uni-padding-wrap {
		width: 700rpx;
		height: 200rpx;
		position: fixed;
		top: 0;
		z-index: 999;
		background-color: #fff;
		border-bottom: 1px solid #ddd;
	}

	.content {
		position: absolute;
		margin-top: 110px;
		z-index: 1;
	}
	.nav-bar-input {
		width: 300px;
	}
</style>
