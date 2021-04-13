<template>
	<view class="container">	 
		<view class="input" >
			<textarea  placeholder="分享我的哔哩哔哩动态" class="input-text"/>
		</view>
		<view class="image-list">
			    <view class="add">
			    	<image src="../../static/image/publish/pic-add.png" id="pic-add"></image>
			    </view>
		</view>
		<view class="address">
				<image src="../../static/publish/coordinate.png" class="dingwei"></image>
			<button type="default" style="width: 100px; height: 30px; font-size: 20rpx; ">
				你在哪里？</button>
		</view>
		<div class="footer">
			<image src="../../static/publish/pic.png" ></image>
			<image src="../../static/publish/bili.png" ></image>
			<image src="../../static/publish/vote.png" ></image>
			<image src="../../static/publish/add.png" ></image>
		</div>
		</view>
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
		.address {
			width: 150px;
			height: 30px;
			/* background-color: #555555; */
			bottom: 60px;
		

		}
		.dingwei {
			width: 65rpx;
			height: 30px;
			flex: left;
			align-items: flex-start;
			/* margin-top: 10px; */
		}
		button {
			margin-top: 10px;
			
		}
		
		 .footer {
		        width: 100%;
		        height: 50px;
		        background: #dce1eb;
		        line-height: 40px;
		        text-align: center;
		        position: fixed;
		        bottom: 0;
		    }
			.footer image {
					width: 60rpx;
					height: 45rpx;
					float: left;
					margin: 25rpx;
					
				}

</style>
