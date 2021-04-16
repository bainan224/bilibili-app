<template>
	<view >
	<uni-nav-bar >
		<!-- 顶部返回与发布 -->
		<view slot="left" @click="gotoDynamic" >
			<i class="iconfont icon-right-angle " style="margin-left: 20px;" ></i>
		</view>
		<view slot="right" @click="gotoDynamic" >
			<i class="iconfont icon-tubiao-06  " style="font-size: 35px; margin-left:-30px; " ></i>
		</view>
	</uni-nav-bar>
	<view class="container0" >	
	 <!-- 文本框 分享的文字内容 -->
		<div class="input" coordinate="true" >
			<textarea  placeholder="分享我的哔哩哔哩动态" class="input-text" />
			<text class="words-num">{{wordsNum}}</text>
		</div >
		<view class="image-list">
			<!-- 显示图片，可以预览删除 -->
				<view class="image-wrap">
			<image v-for="image in images " :src="image" mode="aspectFill" style="width: 100px; height: 100px; margin: 10px;" @click="onPreviewImage" :data-imgsrc="image"></image>
					<!-- <i class="iconfont icon-delete delete" @click="onDelImage"  :data-index="image"></i> -->
				</view>
			<!-- </view> -->
			<view class="image-wrap selectphoto" :hidden="!selectphoto" @click="onChooseImage">
			    	<image src="../../static/publish/ic_add_gray.png"  id="pic-add" ></image>
			</view>		
		</view>
		<!-- 获取定位 -->
		<div class="address" @click="getAdress">
					<image src="../../static/publish/1.png" style="opacity: 0.5;" class="dingwei"></image>
					<div type="default" class="text" >
						你在哪里？
					</div>
		</div>
		<!-- 底部图标 -->
		<div class="footer" style=" :bottom: 'footerBottom px';">
				<image src="../../static/publish/ic_publish_pic.png" v-show="show "  @click="changeImg" class="mt-2  ml-2 "></image>
				<image src="../../static/publish/img_painting_publish_emoji.png"  v-show="show"  @click="changeImg"  class="mt-2  ml-3"></image>
				<image src="../../static/publish/ic_publish_at.png"  v-show="show"  @click="changeImg" class="mt-2  ml-3"></image>
				<image src="../../static/publish/ic_publish_topic.png"  v-show="show"  @click="changeImg" class="mt-2 ml-3"></image>
				<image src="../../static/publish/ic_publish_vote.png"  v-show="show"  @click="changeImg" class="mt-2  ml-3"></image>
				<image src="../../static/publish/ic_group_manager_add.png"  v-show="show"  @click="changeImg" class="mt-2 ml-3"></image>
				<image src="../../static/publish/ic_publish_keyboard.png"  v-show="!show"  @click="changeImg" class="mt-2 "></image>
		  </div>
		
	</view>	
	</view>

</template>

<script> 
import uniNavBar from '../../components/uni-ui/uni-nav-bar/uni-nav-bar.vue'
// 输入的文字最大个数
const MAX_WORDS_NUM = 140
// 输入文字内容
let  content =''
// 用户信息
let userInfo = {}
export default {  
	components:{
		uniNavBar
	},
    data() {  
        return {
			//输入的文字数
			wordsNum: 0,
			footerBottom: 10,
			images:[],
			urls:[],
			selectphoto:true,
			address:'',
			show: true,
			
		}  
    },
	 methods:{
		 gotoDynamic() {
			 uni.switchTab({
			 	url:"./dynamic",
				success() {
					console.log(1)
				},fail() {
					console.log(2)
				}
			 })
		 },
		  onLoad: function (options) {
		     console.log(options)
		     userInfo = options
		   },
		onChooseImage() {
					 uni.chooseImage({
					 	count:6,
						sizeType:['original','compressed'],
						sourceType:['album','camera'],
						success:(res) => {
							console.log(res)
							this.images = res.tempFilePaths;
							console.log(this.images)
						},
						
					 })
		 },
		 onPreviewImage(current) {
			 console.log(current)
			 uni.previewImage({
			 	urls:this.images,
				current: current
			 })
		 },
		 // onDelImage(event) {
			//  console.log(event)
			//  this.$data.images.splice(event.target.dataset.index)
			//  this.setData({
			// 	 images: this.$data.images
			//  })
			//    console.log(this.data.images.length)
			//      // 等于5，就可以显示选择图片元素来
			//      if (this.data.images.length === MAX_IMG_NUM - 1) {
			//        this.setData({
			//          selectPhoto: true,
			//        })
			//      }
		 // },
		
		 
		 upload:function() {
			 
		 },
		 changeImg:function() {
			 this.show =  !this.show 
		 },
		 getAdress:function(){ 
			uni.chooseLocation({
			    success: function (res) {
			        console.log('详细地址：' + res.address);
					this.address = res.address
					console.log(this.address)
			        console.log('纬度：' + res.latitude);
			        console.log('经度：' + res.longitude);
			    }
			});
		 }
	 }
}  
</script>

<style scoped>
	 
	.container0 {
		width: 100%;
	}
	.input {
		
		width: 100%;
		/* height: 400rpx; */
		background-color: #FFFFFF;
		color: #0062CC;
	}
	.input .input-text {
		width: 95%;
		padding: 20rpx;
	}
	
	.bottom {
		width: 100%;
	
		background-color: red;
	}
	.image-list {
		margin: 20px;
	}
		#pic-add {
			width: 100px;
			height: 100px;
			margin-top: 11px;
		}
	.image-wrap {
		position: relative;
	}
	.delete {
		position: absolute;
		top: 0;
	}

		.dingwei {
			position: absolute;
			width: 65rpx;
			height: 30px;
			left: 20px;
			background-color: #FFFDEF;
		
		}
		.text {
			/* position: absolute; */
			width: 70px;
			height: 22px;
			margin-left: 55px;
			margin-top: 2px;
			border-radius: ;
			/* margin-left: -200px; */
			
		}
		
		
		
		 .address {
		        width: 150px;
		        height: 40px;
		        /* background: #FFF; */
		        line-height: 40px;
		        text-align: center;
		        position: fixed;
				bottom: 50px;
				/* border: #000000 solid 2px; */
				
		    }
			 .footer {
				width: 100%;
				height: 48px;
				background: #dce1eb;
				line-height: 40px;
				text-align: center;
				position: fixed;
				bottom: 0;
			/* 	margin-top: 0; */
			}
			 .footer image {
					width: 65rpx;
					height: 55rpx;
					float: left;
					/* margin-top: 25rpx; */
					/* margin-left: 20px; */
					background-color: #DCE1EB;
					
			}
			

</style>
