<template>
	<!-- #ifdef APP-PLUS -->  
	<view class="status_bar">  
	    <view class="top_view"></view>  
	</view>  
	<!-- #endif -->
</template>

<script>
	export default {  
	    data() {  
	        return {}  
	    },  
	    onNavigationBarButtonTap() {  
	        console.log("点击了自定义按钮");  
	    }  
	}  
</script>

<style>
	.status_bar {  
	    height: var(--status-bar-height);  
	    width: 100%;  
	    background-color: #F8F8F8;  
	}  
	.top_view {  
	    height: var(--status-bar-height);  
	    width: 100%;  
	    position: fixed;  
	    background-color: #F8F8F8;  
	    top: 0;  
	    z-index: 999;  
	}
</style>
