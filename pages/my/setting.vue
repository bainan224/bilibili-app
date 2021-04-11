<template>
	<view class="nav">
		<view class="nav-item">
			<!-- navigator可以方便地实现页面跳转，这里把hover-class置为none，
			去掉点击变灰地效果，自己可以尝试下（类似网页a标签地处理） -->
			<navigator class="content" hover-class="none" url="">
				<text class="text">开屏开启画面设置</text>
				<image src="../../static/image/setting/right.png" id="pic-add1"></image>
			</navigator>
		</view>
		<view class="nav-item">
			<navigator class="content" hover-class="none" url="">
				<text class="text">首页推荐设置</text>
				<image src="../../static/image/setting/right.png" id="pic-add2"></image>
			</navigator>
		</view>
		<view class="nav-item">
			<view class="content" bind:tap="onTapQrCode">
				<text class="text">播放设置</text>
				<image src="../../static/image/setting/right.png" id="pic-add3"></image>
			</view>
		</view>
		<view class="nav-item">
			<navigator class="content" hover-class="none" url="">
				<text class="text">离线设置</text>
				<image src="../../static/image/setting/right.png" id="pic-add3"></image>
			</navigator>
		</view>
		<view class="nav-item">
			<navigator class="content" hover-class="none" url="">
				<text class="text">追番/追剧设置</text>
				      <i class="right">
						  </i>
				<image src="../../static/image/setting/right.png" id="pic-add4"></image>
				</i>
			</navigator>
		</view>
		<view class="nav-item">
			<navigator class="content" hover-class="none" url="">
				<text class="text">推送设置</text>
				<image src="../../static/image/setting/right.png" id="pic-add3"></image>
			</navigator>
		</view>
		<view class="nav-item">
			<navigator class="content" hover-class="none" url="">
				<text class="text">下载管理</text>
				<image src="../../static/image/setting/right.png" id="pic-add3"></image>
			</navigator>
		</view>
		<view class="nav-item">
			<navigator class="content" hover-class="none" url="">
				<text class="text">清理存储空间</text>
				<image src="../../static/image/setting/right.png" id="pic-add2"></image>
			</navigator>
		</view>
		<view class="nav-item">
			<navigator class="content" hover-class="none" url="">
				<text class="text">其他设置</text>
				<image src="../../static/image/setting/right.png" id="pic-add3"></image>
			</navigator>
		</view>
		<view class="nav-item">
			<navigator class="content" hover-class="none" url="">
				<text class="text">定时提醒</text>
				<image src="../../static/image/setting/right.png" id="pic-add3"></image>
			</navigator>
		</view>
		<view class="nav-item">
			<navigator class="content" hover-class="none" url="">
				<text class="text">深色模式</text>
				<image src="../../static/image/setting/right.png" id="pic-add3"></image>
			</navigator>
		</view>
		<view class="nav-item">
			<navigator class="content" hover-class="none" url="">
				<text class="text">我的客服</text>
				<image src="../../static/image/setting/right.png" id="pic-add3"></image>
			</navigator>
		</view>
		<view class="nav-item">
			<navigator class="content" hover-class="none" url="">
				<text class="text">关于哔哩哔哩</text>
				<image src="../../static/image/setting/right.png" id="pic-add2"></image>
			</navigator>
		</view>
	</view>
</template>

<script></script>

<style>
page {
	background-color: #ededed;
}

.nav {
	/* overflow: hidden; */
	margin: 20rpx;
	box-sizing: border-box;
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

.content {
  font-size: 32rpx;
  line-height: 1.6em;
  flex: 1;
  display: flex;
  /* justify-content: space-between; */
}

.text {
	color: #4b4b4b;
	
}
.right {
  font-size: 32rpx;
  color: 32rpx;
  width: 20px;
  height: 20px;
  
  
}

#pic-add1 {
	width: 20px;
	height: 20px;
	margin: 0px;
	left: 170px;
}

#pic-add2 {
	width: 20px;
	height: 20px;
	margin: 0px;
	left: 195px;
}

#pic-add3 {
	width: 20px;
	height: 20px;
	margin: 0px;
	left: 220px;
}
#pic-add4 {
	width: 20px;
	height: 20px;
	margin: 0px;
	left: 170px;
}
</style>
