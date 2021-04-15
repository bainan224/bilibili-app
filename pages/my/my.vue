<template>
	<view>
		
		<view class="nav-item">
			<navigator class="content" hover-class="none" url="./setting/setting">
				<text class="text">设置</text>
				<i class="iconfont icon-youjiantou"></i>
			</navigator>
		</view>
		
		<!-- 未登录 -->
		<template v-if="!loginStatus">
			<view class="flex align-center p-2" hover-class="bg-light">
				<image src="/static/default.jpg" style="width: 100rpx;height: 100rpx;" class="rounded-circle"></image>
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
			userSet() {
				uni.navigateTo({
					url: '../user-set/user-set'
				});
			}
		}
	};
</script>

<style>

</style>
