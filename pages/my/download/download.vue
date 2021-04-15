<template>
	<view>
		<view v-for="(mustwatch,index) in mustwatchs" :key="index" >
			<!-- <image :src="getCover(mustwatch.cover)"></image> -->
						<text>{{mustwatch.title}}</text>
			<text>{{mustwatch.owner.name}}</text>

			<image :src="mustwatch.pic"></image>
			<text>{{mustwatch.stat.view}}</text>
			<text>{{mustwatch.stat.danmaku}}</text>
			<text>{{mustwatch.achievement}}</text>
		</view>  
	</view>
</template>

<script>
	export default {
		data() {
			return {
				mustwatchs:[],
			}
		},
		methods: {
			getCover(url){
				console.log(url+">>>>>>>>>>>>>>>>")
				let res = "https://" + url.substring(7);
				console.log(res)
				return res
			},
			onLoad(){
				uni.request({
					url: 'https://api.bilibili.com/x/web-interface/popular/precious?page_size=100&page=1',
					// url: 'https://api.bilibili.com/x/web-interface/web/channel/category/channel_arc/list?id=0',
					success: (res) => {
						// console.log(res.data.data)
						// console.log(res);
						this.mustwatchs = res.data.data.list
						// for(let i =0;i<this.mustwatchs.length;i++ ){
						// 	this.mustwatchs = res.data.data
						// }
						console.log(this.mustwatchs);
						
						
					}
				})
			}
		}
	}
</script>

<style>

</style>
