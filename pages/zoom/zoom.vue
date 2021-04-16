<template>
  <view>
  <uni-nav-bar>
    <view solt="left">
      <i calss="iconfont icon-right-angle" ></i>
    </view>
    <view solt="left">
      <i calss="iconfont icon-right-angle"></i>
    </view>
  </uni-nav-bar>
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
        <text class="font-lg font-weight-bold text-dark">折耳啵啾</text>
		<text style="color: #6D6D72; background-color:#dedede; height: 40rpx;">大会员</text>
      </view>
    </view>
  <view style="height: 1%;">
    <text>这个人很神秘，什么都没有写</text>
  </view>
    <view class="flex align-center px-3 py-2" style="height: 5%">
      <view class="flex align-center" style="border-top:10rpx #000000;">
        <text class="font-lg font-weight-bold text-dark" style="width: 300rpx; height: 50rpx;" @click="changIndex(1)">主页</text>
		<text class="font-lg font-weight-bold text-dark" style="width: 300rpx; height: 50rpx;" @click="changIndex(2)">动态</text>
		<text class="font-lg font-weight-bold text-dark" style="width: 300rpx; height: 50rpx;" @click="changIndex(3)">收藏</text>  
      </view>
    </view>
  <view style="height: 2%;" v-show="Index === 1">
    <view  style="height: 2%;">
       <text class="font-lg font-weight-bold text-dark" style="font-size: 15px;">收藏</text>  
	   <text style="float: right;" @click="changIndex(3)">查看更多</text>
    </view>
     <!-- 图文卡片模式 -->
	 <view class="card">
		 <uni-card
		   title=""
		   mode="style"
		   :is-shadow="true"
		   thumbnail="/static/zoom/3.webp"     
		 >
		 默认收藏夹
		</uni-card>
     </view>
     <view>
       <text class="font-lg font-weight-bold text-dark" style="font-size: 15px;">我推荐的视频</text>  
	   <text style="float: right;" @click="gotoMyrec">查看更多</text>
     </view>
     <view class="card1">
       <!-- 图文卡片模式 -->
       <uni-card
         title="90.9万"
         mode="style"
         :is-shadow="true"
         thumbnail="/static/zoom/4.webp"
         extra=""
       >
       【对阿网】英语四级考试全套课程
       </uni-card>
       <uni-card
         title="82.4万"
         mode="style"
         :is-shadow="true"
         thumbnail="/static/zoom/6.webp"  
       >
       【纯干货】10天过英语四级的复习方法
       </uni-card>
    </view>  
  </view>
  <view class="flex align-center " style="height: 2%;" v-show="Index === 2">
    <text class="font-lg font-weight-bold text-dark" style="font-size: 15px;">动态</text>  
  </view>
  <view style="height: 2%;" v-show="Index === 3">
	<view>
		<text class="font-lg font-weight-bold text-dark" style="font-size: 15px;">我的创建</text>  
	</view>
    <view>
		<text class="font-lg font-weight-bold text-dark" style="font-size: 15px;">我的收藏</text> 
	</view>
	 
  </view>
  </view>
</template>

<script>
  import uniNavBar from "../../components/uni-ui/uni-nav-bar/uni-nav-bar.vue"
  export default {
    components:{
      uniNavBar
    },
    data() {
      return{
     Index: 1,
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
      changIndex(e) {
      this.Index = e
    },
	gotoMyrec(){
		uni.navigateTo({
			url:'../myrec/myrec'
		})
	 }
    }
  };
</script>

<style>
.card{
	height: 400rpx;
	width: 400rpx;
	
}
.card1 {
   height: 400rpx;
   width: 800rpx;
   border-radius:30rpx;
   display: flex;
   align-items: flex-start;
}
</style>
