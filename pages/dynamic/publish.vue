<template>
	<view class="container0" >	 
		<div class="input" coordinate="true" >
			<textarea  placeholder="分享我的哔哩哔哩动态" class="input-text" />
		</div >
		<view class="image-list">
			    
			    	<image src="../../static/publish/ic_add_gray.png"  id="pic-add" @click="upload"></image>
			    
		</view>
		<div class="address" @click="getAdress">
					<image src="../../static/publish/1.png" style="background-color: #FFFFFF;" class="dingwei"></image>
					<div type="default" class="text" >
						你在哪里？
					</div>
		</div>
		<div class="footer">
				<image src="../../static/publish/ic_publish_pic.png" v-show="show "  @click="changeImg" class="mt-2  ml-2 "></image>
				<image src="../../static/publish/img_painting_publish_emoji.png"  v-show="show"  @click="changeImg"  class="mt-2  ml-3"></image>
				<image src="../../static/publish/ic_publish_at.png"  v-show="show"  @click="changeImg" class="mt-2  ml-3"></image>
				<image src="../../static/publish/ic_publish_topic.png"  v-show="show"  @click="changeImg" class="mt-2 ml-3"></image>
				<image src="../../static/publish/ic_publish_vote.png"  v-show="show"  @click="changeImg" class="mt-2  ml-3"></image>
				<image src="../../static/publish/ic_group_manager_add.png"  v-show="show"  @click="changeImg" class="mt-2 ml-3"></image>
				<image src="../../static/publish/ic_publish_keyboard.png"  v-show="!show"  @click="changeImg" class="mt-2 "></image>
		  </div>
		
	</view>

</template>

<script> 
export default {  
    data() {  
        return {
			images:[],
			
			show: true,
			
		}  
    },
	 methods:{
		 upload:function() {
			 
		 },
		 changeImg:function() {
			 this.show =  !this.show 
		 },
		 getAdress:function(){ 
			uni.chooseLocation({
			    success: function (res) {
			        console.log('位置名称：' + res.name);
			        console.log('详细地址：' + res.address);
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
			margin-left: 52px;
			margin-top: 2px;
			border-radius: ;
			/* margin-left: -200px; */
			
		}
		
		
		
		 .address {
		        width: 150px;
		        height: 40px;
		        background: #FFF;
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
