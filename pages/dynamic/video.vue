<template>
	<view>
		<uni-nav-bar fixed="flase">
			<view slot="default" style="padding: 70rpx; background-color: white; ">
				<text @click="gotovideo" class="nav1">视频</text></view>
			<view slot="default" style="padding: 70rpx; background-color: white; ">
				<text @click="gotodynamic" class="nav1">综合</text></view>
			<view slot="right">
			<i class="iconfont icon-bianji" @click="toPublish"></i>
			</view>
		</uni-nav-bar>
		
		<view class="search" @click="gotosearch">
			<mSearch :show="false"
			model="1"
			button="index"
			placeholder="查找精彩动态内容"
			>
			</mSearch>
			    {{val1}}
		</view>
	</view>
</template>

<script>
	import mSearch from '../../components/mehaotian-search/mehaotian-search.vue';
	import uniNavBar from '../../components/uni-nav-bar/uni-nav-bar.vue'
	export default {
		 components: {
			 uniNavBar,
			 mSearch
			 },
			data() {
			return {
				keyword: '',
				val1: '',
				
			}
		},
	
		methods: {
			gotovideo() {
			uni.navigateTo({
				url:"./video"
				})	
			},
			gotodynamic() {
				uni.switchTab({
					url:"./dynamic"
				})
			},
			gotosearch() {
				uni.navigateTo({
					url:"../search/search"
				})
			},
			toPublish(){
				uni.navigateTo({
					url:"./publish"
				})
			}
		},
	}
</script>

<style>
	.nav1 {
		text-decoration:underline;
		color:#333333;
		colorPressed:#FD597C
		/* font-size:400rpx; */
		/* font-weight: bold; */
		
	}
</style>
