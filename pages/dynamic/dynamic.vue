<template>
	<view>
		<h2>动态页面</h2>
		 <view class="left" bindtap="onPublish">
		    <i class="iconfont icon-fabu"></i>
		  </view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			onPublish () {
				navigate("../dynamic/publish.vue")
			}
		}
	}
</script>

<style>

</style>
