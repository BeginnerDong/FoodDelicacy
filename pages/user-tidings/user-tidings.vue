<template>
	<view>
		
		
		<view class="tidingBox  mglr4">
			<view class="item flexRowBetween" v-for="(item,index) in tidingData" :key="index">
				<view class="ll"><image src="../../static/images/messagel-icon.png" mode=""></image></view>
				<view class="rr">
					<view class="tit">系统消息</view>
					<view class="fs12 color6">通知消息显示内容洗澡洗内容通知消息显示内容洗澡洗内容发动机康师傅好公司放感觉多少个发估计是的发的是厨房摆的设计风格地方</view>
				</view>
			</view>
		</view>
		
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				Router:this.$Router,
				showView: false,
				score:'',
				wx_info:{},
				tidingData:[{},{},{}]
			}
		},
		onLoad() {
			const self = this;
			//self.$Utils.loadAll(['getMainData'], self);
		},
		methods: {
		}
	};
</script>

<style>
	@import "../../assets/style/editInfor.css";
	page{padding-bottom: 140rpx;}
	
	.tidingBox .item{border-bottom: 1px solid #eee;padding: 30rpx 0; align-items: flex-start;}
	.tidingBox .item .ll{width: 84rpx;height: 84rpx;}
	.tidingBox .item .ll image{width: 100%;height: 100%;}
	.tidingBox .item .rr{width: 85%;line-height: 36rpx;}
	.tidingBox .item .rr .tit{margin-bottom: 8rpx;}
</style>
