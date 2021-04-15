<template>
	<view>
		<h2>动态页面</h2>
		 <!-- <view class="left" >
		    <i class="iconfont icon-bianji" @click="onPublish"></i>
		  </view> -->
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		onNavigationBarButtonTap:function(){
		          uni.navigateTo({
		          	url:"./publish"
		          })   
		 },
		methods: {
			
			
		}
	}
</script>

<style>

</style>
