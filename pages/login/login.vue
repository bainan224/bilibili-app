<template>
	<view>
		<uni-status-bar>
			<view>
				<view class="iconfont icon-right-angle flex font-lg pl-2 pt-3" style="width: 360rpx;height: 100rpx;"
				 @click="back">
				</view>
				<view class="text-left" style="margin-top: -50px; margin-left: 40px; font-size: 36rpx;">
					{{status?'手机验证码登录':'账号密码登录'}}
				</view>
				<view class="text-right font-sm mr-2" style="margin-top: -33px;font-size: 36rpx;" @click="changeStatus">{{status?'账号密码登录':'验证码登录'}}</view>
			</view>
		</uni-status-bar>

		<view class="w-100" style="margin-top: 120rpx;">
			<image class="w-100" style="height: 120px;" src="../../static/login/5.png" />
		</view>

		<view class="px-4" style="padding-top: 60rpx;padding-bottom: 70rpx; ">
			<template v-if="!status">
				<view class="mb-2">
					<input type="text" v-model="phone" placeholder="手机号" class="border-bottom p-2" />
				</view>
				<view class="mb-2 flex align-stretch">
					<input type="password" v-model="password" placeholder="请输入密码" class="border-bottom p-2 flex-1" />
					<view class="border-bottom flex align-center justify-center font text-muted" style="width: 150rpx;">
						忘记密码？
					</view>
				</view>
			</template>
			<template v-else>
				<view class="mb-2 flex align-stretch">
					<view class="border-bottom flex align-center justify-center font px-2">+86</view>
					<input type="text" v-model="phone" placeholder="手机号" class="border-bottom p-2 flex-1" />
				</view>
				<view class="mb-2 flex align-stretch">
					<input type="text" v-model="code" placeholder="请输入验证码" class="border-bottom p-2 flex-1" />
					<view class="border-bottom flex align-center justify-center font-sm text-white" :class="codeTime > 0 ? 'bg-main-disabled':'bg-main'"
					 style="width: 180rpx;" @click="getCode">
						{{codeTime > 0 ?codeTime +'s':'获取验证码'}}
					</view>
				</view>
			</template>
		</view>

		<view class="py-2 px-3">
			<button class="bg-main text-white" style="border-radius: 50rpx; border: 0;" type="primary" :disabled="disabled"
			 :class="disabled ? 'bg-main-disabled':'bg-main'" @click="submit" :loading="loading">
				{{loading?'登录中...':'登录'}}
			</button>
		</view>


		<view class="ml-3 text-muted">
			<view>
			未注册或未绑定的哔哩哔哩的手机号，将帮你注册新账号
			 </view>  
			  <view class="flex align-center justify-center text-muted">登录即代表你同意
			<text class="text-pink">用户协议</text>
			和
			<text class="text-pink">隐私政策</text>
			</view>
		</view>
		<view class="flex align-center justify-center text-muted">
			遇到问题?
		<text class="text-pink">查看帮助</text>
		</view>

	</view>
</template>

<script>
	import uniStatusBar from '@/components/uni-ui/uni-status-bar/uni-status-bar.vue';
	export default {
		components: {
			uniStatusBar
		},
		data() {
			return {
				status: false,
				password: '',
				phone: '',
				code: '',
				codeTime: 0,
				loading: false
			};
		},
		onLoad() {},
		computed: {
			disabled() {
				if ((this.phone === '' || this.password === '') && (this.phone === '' || this.code === '')) {
					return true;
				}
				return false;
			}
		},
		methods: {
			back() {
				uni.navigateBack({
					delta:1
				})
			},
			//初始化表单
			initForm() {
				this.phone = '';
				this.password = '';
				this.code = '';
			},
			//切换登录方式
			changeStatus() {
				this.initForm();
				this.status = !this.status;
			},
			//获取验证码
			getCode() {
				//防止重复获取
				if (this.codeTime > 0) {
					return;
				}
				//验证手机号
				if (!this.validate()) return;
				//请求数据
				this.$H
					.post('/user/sendcode?phone=' + this.phone, {
						native: true
					}).then(res => {
						//倒计时
						this.codeTime = 60;
						let timer = setInterval(() => {
							if (this.codeTime >= 1) {
								this.codeTime--;
							} else {
								this.codeTime = 0;
								clearInterval(timer)
							}
						}, 1000);
					});
			},
			//表单验证
			validate() {
				//手机号正则表达式
				var mPattern = /^1[34578]\d{9}$/;
				if (!mPattern.test(this.phone)) {
					uni.showToast({
						title: '手机号格式不正确',
						icon: 'none'
					});
					return false;
				}
				//更多验证
				return true;
			},
			appLogin() {
				let self = this;
				uni.login({
					provider: 'weixin',
					success: function(loginRes) {
						uni.getUserInfo({
							provider: 'weixin',
							success: infoRes => {
								console.log(infoRes);
								let wxLoginDto = {
									wxOpenId: infoRes.userInfo.openId,
									nickname: infoRes.userInfo.nickName,
									avatar: infoRes.userInfo.avatarUrl,
									gender: infoRes.userInfo.gender
								};
								self.loading = true;
								self.$H
									.post('/user/wxLogin', wxLoginDto)
									.then(res => {
										self.loading = false;
										console.log(res);
										if (res) {
											console.log(res);
											//修改vuex的state，持久化存储
											self.$store.commit('login', res);
											uni.switchTab({
												url: '../my/my'
											});
										} else {
											uni.showModal({
												title: '登录失败'
											});
											return;
										}
									});
							}
						});
					}
				});
			},
			submit() {
				//表单验证
				let url = '';
				let data = '';
				if (this.status) {
					//手机验证码登录
					if (!this.validate())
						return;
					url = '/user/phonelogin';
					data = {
						phone: this.phone,
						code: this.code
					};
				} else {
					//账号密码登录
					url = '/user/login'
					data = {
						phone: this.phone,
						password: this.password
					};
				}
				this.loading = true;
				this.$H
					.post(url, data)
					.then(res => {
						this.loading = false;
						console.log(res)
						if (res) {
							console.log(res);
							//修改vuex的state.持久化存储
							this.$store.commit('login', res);
							//提示和跳转
							uni.showModal({
								title: '登录成功',
								content: '去看看',
								success: function(res) {
									if (res.confirm) {
										uni.switchTab({
											url: '../my/my'
										});
									} else if (res.cancel) {
										console.log('用户点击取消');
										return;
									}
								}
							});
						} else {
							uni.showModal({
								title: '登录失败'
							});
							return;
						}
					})
					.catch(err => {
						//登录失败
						self.loading = false;
					});
			}

		}
	}
</script>

<style>

</style>
