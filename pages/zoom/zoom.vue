<template>
    <view>
	<view class="flex align-center " style="height: 20%;">
      <image
        src="/static/zoom/2.jpg"
        mode="aspectFill"
        style="weight:400rpx; height:200rpx;">
      </image>
    </view>
    <view class="flex align-center p-2 " hover-class="bg-light" style="height: 20%;">
		<image style="border-radius: 50%;  width: 200rpx; height: 200rpx;" src="http://first-bucket20201002.oss-cn-hangzhou.aliyuncs.com/img/img/avatar/me.jpg"></image>
		<view 
			class="flex-1 flex row align-center justify-center" 
			v-for="(item,index) in myData"
			:key="index">
			<text class="font-lg font-weight-bold">{{ item.num }}</text>
			<text class="font text-muted">{{ item.name}}</text>			  
        </view>	
    </view>
	<view style="width: 100%; color: pink; height: 1%;">
			 <button style="width: 500rpx;margin-right: 30rpx;margin-top: -50rpx; color:pink;" type="button">编辑资料</button>	
	</view>	
    <view class="flex align-center " style="height: 1%;">
      <view class="flex align-center">
        <text class="font-lg font-weight-bold text-dark">折耳啵唧</text>
      </view>
    </view>
	<view style="height: 1%;">
		<text>这个人很神秘，什么都没有写</text>
	</view>
    <view class="flex align-center px-3 py-2" style="height: 5%">
      <view class="flex align-center" style="border-top:10rpx #000000;">
        <text class="font-lg font-weight-bold text-dark" style="width: 300rpx; height: 50rpx;">主页</text>
		<text class="font-lg font-weight-bold text-dark" style="width: 300rpx; height: 50rpx;">动态</text>
		<text class="font-lg font-weight-bold text-dark" style="width: 300rpx; height: 50rpx;">收藏</text>	
      </view>
    </view>
	<view class="flex align-center " style="height: 2%;">
		<text class="font-lg font-weight-bold text-dark" style="font-size: 15px;">收藏</text>	
	</view>
	<view style="height: 24%;">
		<image src="/static/zoom/4.jpg" style="width: 50rpx height:80rpx" ></image>
	</view>
	<view class="flex align-center " style="height: 2%;">
		<text class="font-lg font-weight-bold text-dark" style="font-size: 15px;">我推荐的视频</text>
		
	</view>
	<view style="height: 24%;">
		<image src="/static/zoom/5.jpg" style="width: 50rpx height:80rpx"></image>
	</view>
  </view>
</template>

<script>
  export default {
    data() {
      return{
        myData:[
          {
            name: '粉丝',
            num: 0
          },
          {
            name: '关注',
              num: 0
          },
          {
              name: '获赞',
              num: 0
          }
        ]
      };
    },
    methods:{
      
    }
  };
</script>

<style>
</style>
