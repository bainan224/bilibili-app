<template>
	<view>
		 <view
		 	class="card" 
		 	v-for="(mustwatch,index) in mustwatchs"
		 	:key="index">
			<!-- <image :src="getCover(mustwatch.cover)"></image> -->
			<!-- <text>{{mustwatch.achievement}}</text> -->	 
			
		 	<view style="width: 50%;height: 100%; align-items: center;margin:0rpx;">
		 	<image :src="getCover(mustwatch.pic)" class="card-img">
		 	</view>	
			
		     <view class="flex flex-column card-text" style="width: 50%;">
		 		<text class="mustwatch-name">{{ mustwatch.title}}</text>
		 		<text class="title">{{mustwatch.owner.name}}</text>
		 		<text class="title">{{ mustwatch.stat.view /10000}}万观看·{{mustwatch.stat.danmaku/10000}}万弹幕</text>
				<text class="title">2019-04</text>
				<text class="content">
				<i class="iconfont icon-gengduo"></i>
				</text>
		 	</view>	  
		 </view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				mustwatchs:[],
			}
		},
		methods: {
			getCover(url){
				// console.log(url+">>>>>>>>>>>>>>>>")
				let res = "https://" + url.substring(7);
				// console.log(res)
				return res
			},
			onLoad(){
				uni.request({
					url: 'https://api.bilibili.com/x/web-interface/popular/precious?page_size=100&page=1',
					// url: 'https://api.bilibili.com/x/web-interface/web/channel/category/channel_arc/list?id=0',
					success: (res) => {
						// console.log(res.data.data)
						console.log(res);
						this.mustwatchs = res.data.data.list
						// for(let i =0;i<this.mustwatchs.length;i++ ){
						// 	this.mustwatchs = res.data.data
						// }
						console.log(this.mustwatchs);

					}
				})
			}
		}
	}
</script>

<style>
.title{
	    font-size: 26rpx;
		color: #909090;
}

.content {
	line-height: 1.6em;
	flex: 1;
	display: flex;
	justify-content: space-between;
	margin-top: -50rpx;
	margin-left: 370rpx;
	color: #909090;

}

.mustwatch-name {
    font-size: 30rpx;
    line-height: 1.4;
    padding: 4rpx 0 0 12rpx;
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-line-clamp: 2;
    overflow: hidden;
    text-overflow: ellipsis;
}

.card{
		margin-top: 20rpx;
		display: flex;
		flex-direction: row;
		align-items: center;
		width: 100%;
		height: 240rpx;
		border-bottom: 2px solid #d1d1d1;
	}
	.card-img{
		margin-left: 15rpx;
		width: 95%;
		height: 90%;
		border-radius: 5px;
	}
	.card-text{
		margin: 20rpx;
		width: 95%;
	}
	
</style>
