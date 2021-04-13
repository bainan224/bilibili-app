<template>
	<view>
		<uni-nav-bar>
			<view slot="left">
				<image class="avatar" 
					src="http://first-bucket20201002.oss-cn-hangzhou.aliyuncs.com/img/img/avatar/me.jpg">
			</view>
			<view slot="mod">
				<view class="input" >
					<text class="iconfont icon-wddl" style="color: #d1d1d1;" />
				</view>
			</view>
			<view slot="right">
				<i class="iconfont icon-youxi right-icon" style="margin-left:-40px;"></i>
				<i class="iconfont icon-xinfeng right-icon" style="margin-left:10px;font-weight:bold;"></i>
			</view>
		</uni-nav-bar>
		<view style="display: flex; flex-direction: row; width: 100%;">
			<view style="width: 20%;">
				<view class="btn" @click="changeCard('broadcast')">
					<text class="title">直播</text>
				</view>
			</view>
			<view style="width: 20%;">
				<view class="btn" @click="changeCard('recommend')">
					<text class="title">推荐</text>
				</view>
			</view>
			<view style="width: 20%;">
				<view class="btn" @click="changeCard('hot')">
					<text class="title">热门</text>
				</view>
			</view>
			<view style="width: 20%;">
				<view class="btn" @click="changeCard('watching')">
					<text class="title">追番</text>
				</view>
			</view>
			<view style="width: 20%;">
				<view class="btn" @click="changeCard('video')">
					<text class="title">影视</text>
				</view>
			</view>
		</view>

		<view v-show="currentIndex === 'broadcast'" @click="gotoSearch">
			<h2 >直播</h2>
		</view>

		<view v-show="currentIndex === 'recommend'">
			<h2>推荐</h2>
		</view>

		<view v-show="currentIndex === 'hot'">
			<h2>热门</h2>
		</view>

		<view v-show="currentIndex === 'watching'">
			<h2>追番</h2>
		</view>

		<view v-show="currentIndex === 'video'">
			<h2>影视</h2>
		</view>


	</view>
</template>

<script>
	import uniNavBar from '../../components/uni-ui/uni-nav-bar/uni-nav-bar.vue'


	export default {
		components: {
			uniNavBar,

		},
		data() {
			return {
				currentIndex: 'recommend',

			}
		},
		onLoad() {
			uni.request({
				url: 'https://api.bilibili.com/x/web-interface/popular?ps=20&pn=1',
				success: (res) => {
					console.log(res);
				}
			});
		},
		methods: {
			changeCard(value) {
				console.log(value);
				this.currentIndex = value;

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
		margin-top: 10px;
		padding-top: 1px;
		padding-bottom: 13px;
		width: 200px;
		border-radius: 5%;
		height: 25px;
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
</style>
