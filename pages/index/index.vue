<template>
	<view>
		<uni-nav-bar>
			<view slot="left">
				<image class="avatar" 
					src="http://first-bucket20201002.oss-cn-hangzhou.aliyuncs.com/img/img/avatar/me.jpg">
			</view>
			<view slot="mod">
				<view class="input" @click="gotoSearch">
					<text class="iconfont icon-wddl" style="color: #d1d1d1;" />
				</view>
			</view>
			<view slot="right">
				<i class="iconfont icon-youxi right-icon" style="margin-left:-40px;"></i>
				<i class="iconfont icon-xinfeng right-icon" style="margin-left:10px;font-weight:bold;"></i>
			</view>
		</uni-nav-bar>
		<view >
				<tabControl :current="current" :values="items" bgc="#fff" :fixed="true" :scrollFlag="true" :isEqually="false" @clickItem="onClickItem"></tabControl>
				<!-- 使用 swiper 配合 滑动切换 -->
				<swiper class="swiper" style="height: 100%;" @change="scollSwiper" :current="current">
					<swiper-item v-for="(item, index) in items" :key="index">
						<!-- 使用 scroll-view 来滚动内容区域 -->
						<scroll-view scroll-y="true" style="height: 100%;">{{ item }}</scroll-view>
					</swiper-item>
				</swiper>
		</view>
		<view class="show">
			<view v-show="currentIndex === 0" >
				<h2 >直播</h2>
			</view>
			
			<view v-show="currentIndex === 1" >
				<h2>推荐</h2>
			</view>
			
			<view v-show="currentIndex === 2">
				<h2>热门</h2>
			</view>
			
			<view v-show="currentIndex === 3">
				<h2>追番</h2>
			</view>
			
			<view v-show="currentIndex === 4">
				<h2>影视</h2>
			</view>
			
			<view v-show="currentIndex === 5">
				<h2>抗击肺炎</h2>
			</view>
			
			<view v-show="currentIndex === 6">
				<h2>建党百年</h2>
			</view>
			
		</view>
		


	</view>
</template>

<script>
	import uniNavBar from '../../components/uni-ui/uni-nav-bar/uni-nav-bar.vue'
    import tabControl from '@/components/tabControl/tabControl.vue';

	export default {
		components: {
			uniNavBar,
            tabControl
		},
		data() {
			return {
						items: ['直播', '推荐', '热门', '追番', '影视','抗击肺炎','建党百年'],
						current: 0,
                        currentIndex: 1
			}
		},
		// onLoad() {
		// 	uni.request({
		// 		url: 'https://api.bilibili.com/x/web-interface/popular?ps=20&pn=1',
		// 		success: (res) => {
		// 			console.log(res);
		// 		}
		// 	});
		// },
		methods: {
			onClickItem(val) {
						this.current = val.currentIndex;
					},
					scollSwiper(e) {
						this.current = e.target.current;
						console.log(this.current)
						this.currentIndex = e.target.current;
					},
			gotoSearch() {
				console.log("进入搜索页面")
				uni.navigateTo({
					url: '../search/search',
					success() {
						console.log("#####################")
					},
					fail(err) {
						console.log(err)
						console.log("错误****************************")
					}
				});

			},

		},
	};
</script>
<style>
	.avatar {
		border-radius: 50%;
		margin: 40rpx 20rpx 0rpx 20rpx;
		width: 90rpx;
		height: 90rpx;
	}

	.title {
		font-size: 22px;
		margin-top: 5rpx;
		margin-left: 30rpx;
	}

	.right-icon {
		font-size: 22px;

	}

	.input {
		float: left;
		height: 30px;
		margin-top: 10px;
		width: 200px;
		border-radius:30px;
		background-color: #f6f6f6;
	}

	.border {
		width: 100%;
		position: absolute;
		z-index: 3;
		bottom: 0;
		left: 0;
		right: 0;
		height: 1px;
		content: '';
		-webkit-transform: scaleY(.5);
		transform: scaleY(.5);
		background-color: #e5e5e5
	}
	.show{
		margin-top: 50px;
	}
	
	
</style>
