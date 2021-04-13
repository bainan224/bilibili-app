<template>
	<view>
		<h2>频道页面</h2>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		onLoad() {
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
