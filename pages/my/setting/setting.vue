<template>
	<view>
		<uni-nav-bar class="top" @click="back">
			<ul>
				<view slot="left" >
					<i class="iconfont icon-right-angle"></i>
					<text class="margin">设置</text>
				</view>
			</ul>
		</uni-nav-bar>
		

		<view class="container">
			<ul>
				<view class="nav-item">
					<navigator class="content" hover-class="none" url="">
						<text class="text">账号资料</text>
						<i class="iconfont icon-youjiantou"></i>
					</navigator>
				</view>

				<view class="nav-item">
					<navigator class="content" hover-class="none" url="">
						<text class="text">安全隐私</text>
						<i class="iconfont icon-youjiantou"></i>
					</navigator>
				</view>

				<view class="nav-item">
					<navigator class="content" hover-class="none" url="">
						<text class="text">收货信息</text>
						<i class="iconfont icon-youjiantou"></i>
					</navigator>
				</view>
			</ul>

			<ul>
				<view class="nav-item">
					<navigator class="content" hover-class="none" url="">
						<text class="text">开屏开启画面设置</text>
						<i class="iconfont icon-youjiantou"></i>
					</navigator>
				</view>
				<view class="nav-item">
					<navigator class="content" hover-class="none" url="">
						<text class="text">首页推荐设置</text>
						<i class="iconfont icon-youjiantou"></i>
					</navigator>
				</view>
				<view class="nav-item">
					<view class="content" bind:tap="onTapQrCode">
						<text class="text">播放设置</text>
						<i class="iconfont icon-youjiantou"></i>
					</view>
				</view>
				<view class="nav-item">
					<navigator class="content" hover-class="none" url="">
						<text class="text">离线设置</text>
						<i class="iconfont icon-youjiantou"></i>
					</navigator>
				</view>
				<view class="nav-item">
					<navigator class="content" hover-class="none" url="">
						<text class="text">追番/追剧设置</text>
						<i class="iconfont icon-youjiantou"></i>
					</navigator>
				</view>
			</ul>

			<ul>
				<view class="nav-item">
					<navigator class="content" hover-class="none" url="">
						<text class="text">推送设置</text>
						<i class="iconfont icon-youjiantou"></i>
					</navigator>
				</view>

				<view class="nav-item">
					<navigator class="content" hover-class="none" url="../download/download">
						<text class="text">下载管理</text>
						<i class="iconfont icon-youjiantou"></i>
					</navigator>
				</view>
				<view class="nav-item">
					<navigator class="content" hover-class="none" url="">
						<text class="text">清理存储空间</text>
						<i class="iconfont icon-youjiantou"></i>
					</navigator>
				</view>
				<view class="nav-item">
					<navigator class="content" hover-class="none" url="">
						<text class="text">其他设置</text>
						<i class="iconfont icon-youjiantou"></i>
					</navigator>
				</view>
			</ul>

			<ul>
				<view class="settime">
					<navigator class="content" hover-class="none" url="">
						<text class="text">定时提醒</text>
						<span class="subtext">不开启</span>
						<i class="iconfont icon-youjiantou"></i>
					</navigator>
				</view>
			</ul>

			<ul>
				<view class="nav-item">
					<navigator class="content" hover-class="none" url="">
						<text class="text">深色模式</text>
						<i class="iconfont icon-youjiantou"></i>
					</navigator>
				</view>
			</ul>

			<ul>
				<view class="nav-item">
					<navigator class="content" hover-class="none" url="">
						<text class="text">我的客服</text>
						<i class="iconfont icon-youjiantou"></i>
					</navigator>
				</view>
				<view class="nav-item">
					<navigator class="content" hover-class="none" url="">
						<text class="text">关于哔哩哔哩</text>
						<i class="iconfont icon-youjiantou"></i>
					</navigator>
				</view>
				<view class="nav-item">
					<navigator class="content" hover-class="none" url="">
						<text class="text">广告合作</text>
						<i class="iconfont icon-youjiantou"></i>
					</navigator>
				</view>
			</ul>

			<ul>
				<view class="nav-item">
					<navigator class="content" hover-class="none" url="">
						<text class="text">用户协议</text>
						<i class="iconfont icon-youjiantou"></i>
					</navigator>
				</view>
				<view class="nav-item">
					<navigator class="content" hover-class="none" url="">
						<text class="text">隐私政策</text>
						<i class="iconfont icon-youjiantou"></i>
					</navigator>
				</view>
				<view class="nav-item">
					<navigator class="content" hover-class="none" url="">
						<text class="text">隐私权限设置</text>
						<i class="iconfont icon-youjiantou"></i>
					</navigator>
				</view>
			</ul>

			<ul>
				<view class="exit">
					<navigator class="content" hover-class="none" url=""><text>退出登录</text></navigator>
				</view>
			</ul>
		</view>
	</view>
</template>

<script>
export default {
	comments: {},
	methods: {
		back() {
			uni.switchTab({
				url: '/pages/my/my'
			});
		}
	}
};
</script>

<style>
.nav {
	display: flex;
	justify-content: space-between;
	align-items: center;
	box-sizing: border-box;
	padding: 0 30rpx;
	min-height: 100rpx;
	background-color: #fff;
	border-bottom: 20rpx solid #ededed;
}
.nav-item {
	display: flex;
	justify-content: space-between;
	align-items: center;
	box-sizing: border-box;
	padding: 0 30rpx;
	min-height: 100rpx;
	background-color: #fff;
	border-bottom: 1rpx solid #ccc;
}

.settime {
	display: flex;
	justify-content: space-between;
	align-items: center;
	box-sizing: border-box;
	padding: 0 30rpx;
	/* min-height: 10rpx; */
	background-color: #fff;
	border-bottom: 0rpx solid #ccc;
}

.content {
	font-size: 32rpx;
	line-height: 1.6em;
	flex: 1;
	display: flex;
	justify-content: space-between;
}
.text {
	color: #4b4b4b;
}

.subtext {
	color: #959595;
	margin-left: -690rpx;
	margin-top: 30rpx;
	font-size: 20rpx;
}
.right {
	font-size: 32rpx;
	color: 32rpx;
	width: 20rpx;
	height: 20rpx;
}

ul {
	display: block;
	list-style-type: disc;
	margin-block-start: 0em;
	margin-block-end: 1em;
	margin-inline-start: -20rpx;
	margin-inline-end: -10px;
	padding-inline-start: 0rpx;
}

.iconfont icon-right-angle {
	color: #4b4b4b;
}

.container {
	background-color: #ededed;
	margin-top: 0rpx;
}

.margin {
	margin-left: 10rpx;
}

.exit {
	display: flex;
	/* justify-content:center; */
	/* align-items: center; */
	box-sizing: border-box;
	padding: 0 300rpx;
	min-height: 70rpx;
	background-color: #fff;
	border-bottom: 0rpx solid #ededed;
}

.top{
	display: flex;
	justify-content: space-between;
	align-items: center;
	box-sizing: border-box;
	padding: 0 30rpx;
	min-height: 100rpx;
	background-color: #fff;
	border-bottom: 20rpx solid #ededed;
	margin-top: 80rpx;
}
</style>
