<template>
<view>
	<h2>首页</h2>
		<view class='box'>
			<!-- {{msg}} -->
		</view>
		<text class='iconfont icon-shipin '></text>
		<!-- <text v-if="true" v-html="hhh">wwww</text> -->
		<!-- <button type="primary" @click="List">获取数据</button> -->
		
		<view v-for="(item,index) in list" :key="index">
			<view>{{item}}</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
			// list: [],
			}
		},
		onLoad() {
		   
			uni.request({
			        url: "https://api.bilibili.com/x/web-interface/popular?ps=20&pn=1",                  
			        success: (res) => {
			            console.log(res);
			        }          
		})

			uni.request({
				url: "https://api.bilibili.com/x/web-interface/popular?ps=20&pn=1",  
				success: (res) => {
							console.log(res);
							}
		})
		},

		methods: {
			}
		}
</script>

<style>

</style>
