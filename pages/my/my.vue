<template>
	<view>
		<!-- 未登录 -->
		<template v-if="!loginStatus">
			<view class="flex align-center p-2" hover-class="bg-light">
				<image src="/static/default.jpg" @click="gotoZoom" style="width: 100rpx;height: 100rpx;" class="rounded-circle"></image>
				<view class="flex flex-column flex-1 px-2">
					<text class="font text-muted">登录，体验更多功能</text>
				</view>
				<text class="iconfont icon-youjiantou" @click="login"></text>
			</view>
			<view class="flex align-center px-3 py-2">
				<view class="flex-1 flex flex-column align-center justify-center" v-for="(item, index) in myData" :key="index">
					<text class="font-lg font-weight-bold">{{ item.num }}</text>
					<text class="font text-muted">{{ item.name }}</text>
				</view>
			</view>
		</template>

		<template v-else>
			<view class="flex align-center p-2" hover-class="bg-light">
				<image :src="user.avatar" style="width: 100rpx;height: 100rpx;" class="rounded-circle">
				</image>
				<view class="flex flex-column flex-1 px-2">
					<text class="font-lg font-weight-bold text-dark">{{user.nickname}}</text>
					<text class="font text-muted">B币：0.0 硬币：8.0</text>
				</view>
				<text class="iconfont icon-jinru" @click="userSet"> 空间</text>
			</view>

			<view class="flex align-center px-3 py-2">
				<view class="flex-1 flex flex-column align-center justify-center" v-for="(item, index) in myData" :key="index">
					<text class="font-lg font-weight-bold">{{ item.num }}</text>
					<text class="font text-muted">{{ item.name }}</text>
				</view>
			</view>
			

		</template>
			<view style="margin-left:7%;">
				<!-- <button class="margin: auto 7%; icon-wenjianxiazai"></button> -->
				<!-- <view
				class="flex flex-column flex flex-column align-center justify-center">
				<text class="font text-muted">{{ item.name }}</text>
				</view> -->
				
				<!-- 基本功能1 -->
				<view style="display: flex; flex-direction: row;justify-content: space-between; margin-right: 8%;">
					<view class=" iconfont icon-wenjianxiazai width 20%">	
						<h2 class="text1">离线缓存</h2>
					</view>
					<view class=" iconfont icon-lishijilu1 width 20%">
						<h2 class="text1">历史记录</h2>
					</view>			
					<view class=" iconfont icon-shoucang1 width 20%">	
						<h2 class="text1">我的收藏</h2>
					</view>
					<view class="iconfont icon-shaohouzaikanx width 20%">
						<h2 class="text1">稍后再看</h2>
					</view>
				</view>
				</br>
				
				<!-- 创作中心 -->
				<view  style="display: flex; flex-direction: row; margin-right: 5%;">
					<view style="font-weight: 800; margin: auto -4%;">创作中心</view>
					<button class="btn1 iconfont icon-fabu2" >发布</button>
				</view>
				<view class="chuangzuozhongxin" style="display: flex; justify-content: space-around; flex-wrap: wrap; margin: auto -5%; margin-right: 2%;">
					<view class="iconfont icon-chuangzuoshouyex ">
						<h2 class="text1">创作首页</h2>
					</view>
					<view class=" iconfont icon-jiang ">	
						<h2 class="text1">up主推荐</h2>
					</view>
					<view class=" iconfont icon-daka ">	
						<h2 class="text1">打卡挑战</h2>
					</view>
					<view class=" iconfont icon-huodong ">
						<h2 class="text1">有奖活动</h2>
					</view>			
				</view>
				</br>
				
				<!-- 推荐服务 -->
				
				<view  style="display: flex; flex-direction: row; ">
					<view style="font-weight: 800; margin: auto -4%;">推荐服务</view>
				</view>
				<view class="tuijianfuwu1" >
					<view style="width: 130rpx;" class="iconfont icon-wodekecheng ">
						<h2 class="text1">我的课程</h2>
					</view>
					<view class=" iconfont icon-SIMka ">	
						<h2 class="text1">免流量服务</h2>
					</view>
					<view class=" iconfont icon-gexingzhuangban ">	
						<h2 class="text1">个性装扮</h2>
					</view>
					<view class=" iconfont icon-yaohaoyoulinghongbao">
						<h2 class="text1">邀好友赚红包</h2>
					</view>
				<!-- </view> -->
				<!-- <view class="tuijianfuwu2" > -->
					<view class="iconfont icon-qianbao ">
						<h2 class="text1">我的钱包</h2>
					</view>
					<view class=" iconfont icon-youxi ">	
						<h2 class="text1">游戏中心</h2>
					</view>
					<view class=" iconfont icon-huiyuangou ">	
						<h2 class="text1">会员购中心</h2>
					</view>
					<view class=" iconfont icon-zhibo">
						<h2 class="text1">直播中心</h2>
					</view>	
				<!-- </view> -->
				<!-- <view style="display: flex;  margin: auto -2%;"> -->
					<view class=" iconfont icon-fankui " style="width: 160rpx;">
						<h2 class="text1">反馈论坛</h2>
					</view>
					<view class=" iconfont icon-fuli" style="width: 185rpx;">
						<h2 class="text1">充能领福利</h2>
					</view>	
					
				</view>
				
				
				</br>
				<view  style="display: flex; flex-direction: row; ">
					<view style="font-weight: 800; margin: auto -4%;">更多服务</view>
				</view>
				<!-- <uni-list-item title="联系客服" showExtraIcon>
					<text slot="icon" class="iconfont icon-kefu">联系客服</text>
				</uni-list-item> -->
				
				
				
				<view>
					<view class=" iconfont icon-kefu " >
						<text class="text1">联系客服</text>
						<text class="iconfont icon-youjiantou" style="text-align: right;"></text>
						</view>
					<view class=" iconfont icon-ketang">
						<text class="text1">课堂模式</text></view>
					<view class="iconfont icon-yusan">
						<text class="text1">青少年模式</text></view>
					<view class="iconfont icon-shezhi1">
						<text class="text1">设置</text></view>
					</view>
					</br>
		
			</view>
	</view>
</template>

<script>
	
	import {
		mapState
	} from 'vuex';
	export default {
	
		data() {
			return {
				myData: [{
						name: '动态',
						num: 1
					},
					{
						name: '关注',
						num: 13
					},
					{
						name: '粉丝',
						num: 0
					}

				]
			};
		},
		computed: {
			...mapState({
				loginStatus: state => state.loginStatus,
				user: state => state.user
			}),
			//用户头像
			avatar() {
				return this.user.avatar ? this.user.avatar : '/static/default.jpg';
			}
		},
		methods: {
			login() {
				uni.navigateTo({
					url: '../login/login'
				});
			},
			gotoZoom() {
				uni.navigateTo({
					url: '../zoom/zoom'
				});
			},
			userSet() {
				uni.navigateTo({
					url: '../user-set/user-set'
				});
			}
		}
	};
</script>

<style>
.icon-shaohouzaikanx,
	.icon-wenjianxiazai,
	.icon-shoucang1,
	.icon-lishijilu1{
		font-size: 30px;
		color: #0A98D5;
		text-align: center;
		/* display: flex; */
		flex-direction: column;
	}
	.text1{
		font-size: 25rpx;
		font-weight: normal;
		color: #000000;
		vertical-align: middle;
		
	}
	.btn1{
		margin-right:0rpx;
		background-color:#EC407A ;
		color: #FFFFFF;
	}
	
	.chuangzuozhongxin{
		
	}
	
	.tuijianfuwu1{
	display: flex;
	justify-content: space-around;
	flex-wrap: wrap;
	/* margin: auto -2%; */
	margin-left: -2%;	
	}
	/* .tuijianfuwu2{
	display: flex;
	justify-content: space-around; 
	flex-wrap: wrap; 
	margin: auto -3%;
	margin-left: -2%;
	margin-right: 4%;	
	} */
	
	.icon-chuangzuoshouyex,
	.icon-jiang,
	.icon-daka,
	.icon-huodong{
		font-size: 30px;
		color: #F9A825;
		text-align: center;
		flex-direction: column;
	}
	.icon-wodekecheng,
	.icon-SIMka,
	.icon-gexingzhuangban,
	.icon-yaohaoyoulinghongbao,
	.icon-qianbao,
	.icon-youxi,
	.icon-huiyuangou,
	.icon-zhibo,
	.icon-fankui,
	.icon-fuli
	{
		font-size: 30px;
		color: #F48FB1;
		text-align: center;
		flex-direction: column;
		
	}
	.icon-kefu,.icon-ketang,.icon-yusan,.icon-shezhi1{
		font-size: 30px;
		color: #F48FB1;
		text-align: left;
		margin-bottom:-25px;
	}
	
</style>
