<template>
	<view >
		<view>
			<image style="border-radius: 50%; margin:30rpx 30rpx 30rpx 30rpx; width: 120rpx; height: 120rpx;" src="http://first-bucket20201002.oss-cn-hangzhou.aliyuncs.com/img/img/avatar/me.jpg">
		</view>
		<view style="display: flex; flex-direction: row; width: 100%;border-bottom:5rpx #e9e8e5;">
			<view style="width: 20%;" >
				<view class="btn" @click="changeCard('broadcast')" >
					<text style="font-size: 22px;margin-top: 5rpx;margin-left:30rpx;">直播</text>
				</view>
			</view>
			<view style="width: 20%;" >
				<view class="btn" @click="changeCard('recommend')" >
					<text style="font-size: 22px;margin-top: 5rpx;">推荐</text>
				</view>
			</view>
			<view style="width: 20%;" >
				<view class="btn" @click="changeCard('hot')" >
					<text style="font-size: 22px;margin-top: 5rpx;">热门</text>
				</view>
			</view>
			<view style="width: 20%;" >
				<view class="btn" @click="changeCard('watching')" >
					<text style="font-size: 22px;margin-top: 5rpx;">追番</text>
				</view>
			</view>
			<view style="width: 20%;" >
				<view class="btn" @click="changeCard('video')" >
					<text style="font-size: 22px;margin-top: 5rpx;">影视</text>
				</view>
			</view>
		</view>
		<view v-show="currentIndex === 'broadcast'">
		<h2>直播</h2>
		</view>
		
		<view v-show="currentIndex === 'recommend'">
		<h2>推荐</h2>
		</view>
		
		<view v-show="currentIndex === 'hot'">
		<h2>热门</h2>
		</view>
		
		<view v-show="currentIndex === 'watching'">
		<h2>追番</h2>
		</view>
		
		<view v-show="currentIndex === 'video'">
		<h2>影视</h2>
		</view>
		
		
		
		
	</view>
</template>

<script>
	
	export default {
		data() {
			return {
				currentIndex: 'recommend',
			}
		},
		methods: {
			changeCard(value) {
						  console.log(value);
						  this.currentIndex = value;
						 
			},
		}
	};
</script>
