<template>
	<uni-nav-bar>
	<view slot="mod"> 
	</view>
	<view slot="right"> 
	<i class="iconfont icon-bianji" @click="toPublish"></i>
	</view>
	</uni-nav-bar>
</template>

<script>
	import uniNavBar from '../../components/uni-ui/uni-nav-bar/uni-nav-bar.vue'
	export default {
		components:{
			uniNavBar
		},
		
		data() {
			return {
				
			}
		},
		// onNavigationBarButtonTap:function(){
		//           uni.navigateTo({
		//           	url:"./publish"
		//           })   
		//  },
		methods: {
			toPublish() {
				uni.navigateTo({
					url:"./publish"
				})
			}
			
			
		}
	}
</script>

<style>

</style>
