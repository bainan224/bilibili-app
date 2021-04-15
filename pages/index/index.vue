<template>
	<view>
		<uni-nav-bar>
			<view slot="left" @click="gotoSetting">
				<image class="avatar"
					src="http://first-bucket20201002.oss-cn-hangzhou.aliyuncs.com/img/img/avatar/me.jpg">
			</view>
			<view slot="mod">
				<view class="input" @click="gotoSearch">
					<text class="iconfont icon-wddl" style="color: #d1d1d1;" />
				</view>
			</view>
			<view slot="right">
				<i class="iconfont icon-youxi right-icon" style="margin-left:-100rpx;"></i>
				<i class="iconfont icon-xinfeng right-icon" style="margin-left:10px;font-weight:bold;"></i>
			</view>
		</uni-nav-bar>
		<view class="tab-container">
			<tabControl :current="current" :values="tabs" bgc="#fff" :fixed="true" :scrollFlag="true" :isEqually="false"
				@clickItem="onClickItem"></tabControl>
			<swiper class="swiper" style="height: 100%;" @change="scollSwiper" :current="current">
				<swiper-item v-for="(item, index) in tabs" :key="index">
					<scroll-view scroll-y="true" style="height: 100%;">{{ item }}</scroll-view>
				</swiper-item>
			</swiper>
		</view>
		<view class="show">
			<view v-show="currentIndex === 0">
				<h2>直播</h2>
			</view>

			<view v-show="currentIndex === 1">
				<h2>推荐</h2>
			</view>

			<view v-show="currentIndex === 2">
				<view class="top">
					<view class="flex flex-column " style="width: 33%;align-items: center;">
						<image class="img" src="../../static/image/index/icon_rank.png" />
						<text>排行榜</text>
					</view>
					<view class="flex flex-column" style="width: 34%;align-items: center;">
						<image class="img" src="../../static/image/index/icon_weekly.png" />
						<text>每周必看</text>
					</view>
					<view class="flex flex-column" style="width: 33%;margin-right: 0;align-items: center;">
						<image class="img" src="../../static/image/index/icon_history.png">
							<text>入站必刷</text>
					</view>
				</view>
				<view>
					<view class="card" v-for="(item,index) in items" :key="index">
						<view style="width: 50%;height: 100%; align-items: center;margin:5rpx;"
							@click="play(item.short_link)">
							<image :src=item.pic class="card-img">
						</view>
						<view class="flex flex-column card-text" style="width: 50%;padding-left: 16rpx;">
							<text class="font text-muted card-title">{{ item.title}}</text>
							<view class="card-lable" v-if="item.rcmd_reason.content != null">
							    <text class="card-lable-text">{{ item.rcmd_reason.content}}</text>
							</view>
							<view class="flex flex-row align-center" style="margin-bottom: -10rpx;">
								<image class=" card-text-img" src="../../static/image/index/biligame_up.png">
								<text class="card-text">{{item.owner.name}}</text>
							</view>
							<view class="flex flex-row align-center" style="margin-bottom: -20rpx;">
								<image class="card-text-img" src="../../static/image/index/biligame_video_play_count.png">
								<text class="card-text" >
								{{(item.stat.view /10000).toFixed(1)}}万观看 04-16
								</text>
							</view>	
						</view>

					</view>
				</view>
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

				tabs: ['直播', '推荐', '热门', '追番', '影视', '抗击肺炎', '建党百年'],
				current: 1,
				currentIndex: 1,


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

		onLoad() {
			uni.request({
				url: 'https://api.bilibili.com/x/web-interface/popular?ps=20&pn=1',
				success: (res) => {
					this.items = res.data.data.list
					console.log(this.items)
					console.log(res);

				}
			});
		},

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
			gotoSetting() {
				uni.navigateTo({
					url: '../my/setting/setting'
				})
			},
			play(e) {
				console.log("进入播放页")
				console.log(e)
				let url = e
				plus.runtime.openURL(url,function(res){
					console.log(res);
				})
			}

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
		width: 400rpx;
		border-radius: 30px;
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

	.show {
		margin-top: 3px;
	}

	.tab-container {
		width: 100%;
		margin-top: 78rpx;
		border-bottom: 1px solid #d1d1d1;
	}

	.top {

		display: flex;
		flex-direction: row;
		width: 100%;
		align-items: center;
		margin-top: 20rpx;

	}

	.img {
		background-color: #FFFFFF;
		width: 100rpx;
		height: 100rpx;
	}

	.card {
		margin-top: 30rpx;
		display: flex;
		flex-direction: row;
		align-items: center;
		width: 100%;
		height: 240rpx;
		border-bottom: 1px solid #d1d1d1;
	}

	.card-img {
		margin-left: 20rpx;
		margin-right: 30rpx;
		width: 95%;
		height: 90%;
		border-radius: 5px;
	}

	.card-text {
		color: #BBBBBB;
		font-size: 26rpx;
		width: 95%;
		
	}

	.card-title {
		color: #000000;
		margin-top: -50rpx;
		overflow: hidden;
		-webkit-line-clamp: 2;
		text-overflow: ellipsis;
		display: -webkit-box;
		-webkit-box-orient: vertical;
	}

	.card-text-img {
		
			background-color: #FFFFFF;
			width: 30rpx;
			height: 30rpx;
		}
	.card-lable{
		height: 30rpx;
		margin-bottom: 8rpx;
		
	}	
	.card-lable-text{
		font-size: 26rpx;
		color: #FF502E;
		margin-bottom: 20rpx;
	}
</style>
