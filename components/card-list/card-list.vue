<template>
	<view class="my-card" @click="open">
		<view class="thumb">
			<view class="flex flex-column flex-1 px-2">
				<text class="font text-dark">{{channel.name}}</text>
				<text class="font-sm  text-muted">刚刚更新</text>
			</view>
			<image :src="channel.cover" class="img" mode="aspectFill" />
			<view class="title ml-3 multiple-line box " style="margin-left:12px">{{archive.name}}</view>
			<view class="title1 ml-3 mt-1 text-muted">精选视频{{channel.featured_count}}个  ></view>
		</view>
		<view class="detail">
			<view class="like mt-2">
				<text class="add text-pink">{{channel.archive_count}}  订阅</text>
			</view>
			
			<image :src="channel.cover" class="img" mode="aspectFill" />
			<!-- <view>
				<view class="video-card_info">
					<span class="play-text">
					<image src="../../static/image/index/biligame_video_play_count.png" />
					<view>{{archive.view_count}}</view>
					</span>
					<span class="like-text">
						<image src="../../static/image/index/ic_album_comment_count.png" />
					</span>
					<span class="play-duraiton">{{archive.like_count}}</span>
				</view>
				<view>{{archive.duration}}</view>  
			</view> -->
			
		</view>
	</view>
</template>

<script>
	export default {
	    name: 'cardList',
	    props: ['channel','archive'], //通过props传值，父组件中将article传过来
	    computed: {
	      //计算属性，文章摘要的长度超出，就用。。。代替
	      title() {
	        let title = this.rank.title;
	        if (title && title.length > 12) {
	          title = title.substring(0, 12) + '...';
	        }
	        return title;
	      }
	    },
	    methods: {
	      open() {
	        console.log("click");
	        //在子组件my-card.vue中将点击事件传回父组件index.vue
	        this.$emit('open');
	      }
	    }
	  };
</script>

<style lang="scss" scoped>
	.box {
		width: 160px; // 别漏了定义宽度
	}
	
	.multiple-line {
		display: -webkit-box;
		-webkit-box-orient: vertical;
		-webkit-line-clamp: 2;
		overflow: hidden;
	}
	// .video-card_info {
	// 	z-index: 1;
	// 	position: absolute;
	// 	width: 100%;
	// 	align-items: center;
	// 	bottom: 5px;
	// 	font-size: 12px;
	// 	padding:0 8px;
	// 	display: flex;
	// }
	// .video-card_info .play-text {
	// 	margin-right: 12px;
	// }
	// .video-card_info .like-text {
	// 	flex: 1;
	// } 
	.my-card {
		padding: 20rpx 20rpx;
		border-bottom: 1px dashed #ddd;
		display: flex;
		background-color: #fff;
		font-size: 14px;

		.thumb {
			width: 300rpx;
			height: 500rpx;
			position: relative;

			.img {
				width: 340rpx;
				height: 240rpx;
				border-radius: 10%;
				position: absolute;
				margin-top: 15rpx;
				left: 10rpx;
			}
			.title {
				margin-top: 120px;
			}
			
		}

		.detail {
			padding-left: 92px;
			// word-wrap: break-word;
			width: 220rpx;
			position: relative;
			display: flex;
			flex-direction: column;
			.like {
				height: 20px;
				width: 190rpx;
				display: flex;
				justify-content: center;
				align-items: center;
				border-radius: 10%;
				border: 1px solid #FFB6C1;

			}
			.img {
				width: 340rpx;
				height: 240rpx;
				border-radius: 10%;
				position: absolute;
				margin-top: 110rpx;
				left: 60rpx;
			}
		}
	}
</style>
