<template>
	<view>
		<!-- 导航栏 -->
		<uni-nav-bar>
			<view slot="left" class="left-item">
				会员购
			</view>
			<view slot="mod" class="title-item">
				官方直营·正品保证
			</view>
			<view slot="right">
				<i class="iconfont icon-youxi right-icon" style="margin-left:-40px;"></i>
				<i class="iconfont icon-xinfeng right-icon" style="margin-left:10px;font-weight:bold;"></i>
			</view>
		</uni-nav-bar>
		<!-- 搜索框 -->
		
		<!-- 展示图片 -->
		<view class="image-view1">
			<view>
				<image class="img-small" src="../../static/smallcard/Garage Kit.png">
					<h2 class="reduce">手办</h2>
				</image>
			</view>
			<view>
				<image class="img-small" src="../../static/smallcard/periphery.png">
					<h2 class="reduce">周边</h2>
				</image>
			</view>
			<view>
				<image class="img-small" src="../../static/smallcard/movie.png">
					<h2 class="reduce">展演电影</h2>
				</image>
			</view>
			<view>
				<image class="img-small" src="../../static/smallcard/book.png">
					<h2 class="reduce">图书漫画</h2>
				</image>
			</view>
			<view>
				<image class="img-small" src="../../static/smallcard/games.png">
					<h2 class="reduce">游戏相关</h2>
				</image>
			</view>
		</view>
		<view class="image-view2">
			<view>
				<image class="img-small" src="../../static/smallcard/skirt.png">
					<h2 class="reduce">服饰鞋包</h2>
				</image>
			</view>
			<view>
				<image class="img-small" src="../../static/smallcard/teacher.png">
					<h2 class="reduce">阴阳师</h2>
				</image>
			</view>
			<view>
				<image class="img-small" src="../../static/smallcard/singer.png">
					<h2 class="reduce">虚拟歌手</h2>
				</image>
			</view>
			<view>
				<image class="img-small" src="../../static/smallcard/fate.png">
					<h2 class="reduce">Fate</h2>
				</image>
			</view>
			<view>
				<image class="img-small" src="../../static/smallcard/all.png">
					<h2 class="reduce">全部分类</h2>
				</image>
			</view>
		</view>
		<view class="card">
			<!-- 轮播图 -->
			<swiper  class="swiper" :autoplay="true" :interval="2000" 
					:duration="500" :circular="true" indicator-dots="true"
					indicator-active-color="red" indicator-color="white" >
				<swiper-item>
					<image class="img-swiper" src="../../static/swiper-photos/01.jpg"></image>
				</swiper-item>
				<swiper-item>
					<image class="img-swiper" src="../../static/swiper-photos/02.jpg"></image>
				</swiper-item>
				<swiper-item>
					<image class="img-swiper" src="../../static/swiper-photos/03.jpg"></image>
				</swiper-item>
				<swiper-item>
					<image class="img-swiper" src="../../static/swiper-photos/04.jpg"></image>
				</swiper-item>
				<swiper-item>
					<image class="img-swiper" src="../../static/swiper-photos/05.jpg"></image>
				</swiper-item>
				<swiper-item>
					<image class="img-swiper" src="../../static/swiper-photos/06.jpg"></image>
				</swiper-item>
			</swiper>
			<!-- box -->
			<view class="right-box">
				<view style="font-size: 32rpx; font-weight: 600; margin: 12rpx;">魔力赏</view>
				<view style="color: #8A6DE9; margin-top: -50rpx; margin-left: 120rpx;">
					免费试玩赢奖励
				</view>
				<image src="../../static/card/07.png" style="width: 100rpx; height: 160rpx; margin-left: 50rpx;"></image>
				<image src="../../static/card/08.png" style="width: 100rpx; height: 160rpx; margin-left: 40rpx;"></image>
			</view>
		</view>
		<!-- </view> -->
		<!-- 今日上新 -->
		<!-- 卡片 -->
		<view v-for="(vip,index) in Vips" :key="index">
			<uni-card title="" :thumbnail="vip.cover" mode="style">
				<template v-slot="footer">
					<view class="footer-box">
						<view style="font-size: 32rpx; font-weight: 600;">{{vip.project_name}}</view>
						<view style="color: #FF4A6A;">{{vip.sale_flag}}</view>
						<view style="color: #FF4A6A; margin-top: 10rpx; font-weight: 600;">￥{{vip.price_high}}</view>
					</view>
				</template>
			</uni-card>
		</view>
	</view>
</template>

<script>
	import uniNavBar from '../../components/uni-ui/uni-nav-bar/uni-nav-bar.vue'
	import uniCard from '@/components/uni-ui/uni-card/uni-card.vue'
	import uniList from '../../components/uni-ui/uni-list/uni-list.vue'
	import uniListItem from '../../components/uni-ui/uni-list-item/uni-list-item.vue'
	export default {
	    components: {uniNavBar, uniCard, uniList, uniListItem},
		data() {
			return {
				keyword: '',
				Vips: [],
			};
		},
		onLoad() {
			uni.request({
				url:'https://show.bilibili.com/api/ticket/project/listV3?version=133&page=1&pagesize=20&platform=web&area=-1&p_type=全部类型&style=1&buvid=9E1A8BC2-CC7E-45EA-9C9B-BCCCCAE10112184999infoc&mid=480185780',
				success: (res) => {
				// console.log(res);
				this.Vips = res.data.data.result;
				for (let i = 0; i < this.Vips.length; i++) {
					this.Vips[i].cover = 'https:'+this.Vips[i].cover
					// console.log(this.Vips[i].cover);
				}
				
				}
			});

		},
			methods: {
				
			}
		}
</script>

<style>
.left-item {
	font-size: 40rpx;
	font-weight: 600;
}
.title-item {
	color: #6D6D72;
	font-size: 28rpx;
}
.icon-item1 {
	margin-left: 20%;
	font-size:46rpx;
	color: #555555;
}
.icon-item2 {
	margin-left: 10%;
	font-size:46rpx;
	color: #555555;
}
.icon-item3 {
	margin-right: 0rpx;
	font-size:46rpx;
	color: #555555;
}
.image-view1 {
	display: flex;
	flex-direction: row;
	flex-wrap: wrap;
	justify-content: space-around;
	align-items: flex-start;
}
.image-view2 {
	margin-top: 30rpx;
	display: flex;
	flex-direction: row;
	flex-wrap: wrap;
	justify-content: space-around;
	align-items: flex-start;
}
.img-small {
	height: 100rpx;
	width: 100rpx;
}
.reduce {
	font-size: 24rpx;
	align-items: center;
	display: flex;
	flex-direction: column;
}
.swiper {
	margin-left: 15rpx;
	margin-top: 40rpx;
 	height: 250rpx;
	width: 340rpx;
}
.img-swiper{  
    width: 340rpx;  
    height: 140px;
	border-radius:40rpx
} 
.right-box {
	margin-left: 35rpx;
	margin-top: 40rpx;
	height: 250rpx;
	width: 340rpx;
	background-image: linear-gradient(Lavender,white);
	border-radius:40rpx
}
.card {
	 border-radius:30rpx;
	 display: flex;
}
.card1 {
	 height: 400rpx;
	 width: 750rpx;
	 border-radius:30rpx;
	 display: flex;
	 align-items: flex-start;
}
.card2 {
	 margin-top: 30%;
	 height: 400rpx;
	 width: 750rpx;
	 border-radius:30rpx;
	 display: flex;
	 justify-content: space-around;
	 align-items: flex-start;
}
</style>
