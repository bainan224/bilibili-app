<template>
	<view class="container">	
	<view class="status_bar">  
	    <view class="top_view"></view>  
	</view>  
		<view class="input" >
			<textarea  placeholder="分享我的哔哩哔哩动态" class="input-text"/>
		</view>
		<view class="image-list">
			    <view class="add">
			    	<image src="../../static/image/publish/pic-add.png" id="pic-add"></image>
			    </view>
		</view>
		<div class="footer">
			<view class=""></view>
			<view class=""></view>
			<view class=""></view>
			<view class=""></view>
			<view class=""></view>
			<view class=""></view>
		</div></view>
	</view>
</template>

<script> 
export default {  
    data() {  
        return {}  
    } 
}  
</script>

<style>
	.container {
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
		/* position: absolute;
		bottom: 10%; */
		width: 100%;
		/* height: 40rpx; */
		background-color: red;
	}
	.image-list {
		margin: 20px;
	}
	.add {
		width: 100px;
		height: 100px;
		/* padding: 10px 0 0 10px; */
		border: #000 solid 1rpx;
		border-style: dashed;
	}
		#pic-add {
			width: 80px;
			height: 80px;
			margin: 11px;
		}
		  .footer {
		        width: 100%;
		        height: 50px;
		        background: #b4bbcb;
		        line-height: 40px;
		        text-align: center;
		        /* 方法一 */
		        position: fixed;
		        bottom: 0;
		    }

</style>
