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

o
加载更多