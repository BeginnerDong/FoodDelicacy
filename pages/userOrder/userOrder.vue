<template>
	<view>
		
		<view class="topNavFix f5bj">
			<view class="orderNav whiteBj boxShaow color6 mgb15 flexRowBetween">
				<view class="tt" :class="curr==1?'on':''" @click="changeCurr('1')">全部</view>
				<view class="tt" :class="curr==2?'on':''" @click="changeCurr('2')">待核销</view>
				<view class="tt" :class="curr==3?'on':''" @click="changeCurr('3')">待收货</view>
				<view class="tt" :class="curr==4?'on':''" @click="changeCurr('4')">配送中</view>
				<view class="tt" :class="curr==5?'on':''" @click="changeCurr('5')">已完成</view>
			</view>
		</view>
		
		<view class="topNavH"></view>
		
		<view>
			<view class="mglr4 pdt15">
				<view class="proRow">
					<view class="item">
						<view class="fs12 flexRowBetween mgb10">
							<view class="color9">交易时间：2020-01-18</view>
							<view class="red">待核销</view>
						</view>
						<view class="flexRowBetween">
							<view class="pic">
								<image src="../../static/images/the-orderl-img.png" mode=""></image>
							</view>
							<view class="infor">
								<view class="avoidOverflow2 fs13">美味的鸡蛋饼</view>
								<view class="fs12 color6">200g</view>
								<view class="B-price flexRowBetween">
									<view class="price">138</view>
									<view class="fs13">×1</view>
								</view>
							</view>
						</view>
						<view class=" mgt15">核销码：<span class="pubColor">12</span></view>
					</view>
					<view class="item">
						<view class="fs12 flexRowBetween mgb10">
							<view class="color9">交易时间：2020-01-18</view>
							<view class="red">待收货</view>
						</view>
						<view class="flexRowBetween">
							<view class="pic">
								<image src="../../static/images/the-orderl-img.png" mode=""></image>
							</view>
							<view class="infor">
								<view class="avoidOverflow2 fs13">美味的鸡蛋饼</view>
								<view class="B-price flexRowBetween">
									<view class="price">56.00</view>
									<view class="fs13">×1</view>
								</view>
							</view>
						</view>
					</view>
					<view class="item">
						<view class="fs12 flexRowBetween mgb10">
							<view class="color9">交易时间：2020-01-18</view>
							<view class="red">配送中</view>
						</view>
						<view class="flexRowBetween">
							<view class="pic">
								<image src="../../static/images/the-orderl-img.png" mode=""></image>
							</view>
							<view class="infor">
								<view class="avoidOverflow2 fs13">美味的鸡蛋饼</view>
								<view class="B-price flexRowBetween">
									<view class="price">56.00</view>
									<view class="fs13">×1</view>
								</view>
							</view>
						</view>
						<view class="underBtn flexEnd mgt15">
							<view class="Bbtn">确认收货</view>
						</view>
					</view>
					
					<view class="item">
						<view class="fs12 flexRowBetween mgb10">
							<view class="color9">交易时间：2020-01-18</view>
							<view class="red">已完成</view>
						</view>
						<view class="flexRowBetween">
							<view class="pic">
								<image src="../../static/images/the-orderl-img.png" mode=""></image>
							</view>
							<view class="infor">
								<view class="avoidOverflow2 fs13">美味的鸡蛋饼</view>
								<view class="B-price flexRowBetween">
									<view class="price">56.00</view>
									<view class="fs13">×1</view>
								</view>
							</view>
						</view>
					</view>
					
				</view>
			</view>
		</view>
		
		
		<!-- 无数据 -->
		<view class="nodata"><image src="../../static/images/nodata.png" mode=""></image></view>
		
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
				is_show:false,
				curr:1
			}
		},
		onLoad() {
			const self = this;
			//self.$Utils.loadAll(['getMainData'], self);
		},
		methods: {
			changeCurr(curr){
				const self = this;
				if(curr!= self.curr){
					self.curr = curr
				}
			}
		}
	};
</script>

<style>
	@import "../../assets/style/orderNav.css";
	@import "../../assets/style/proList.css";
	page{background: #F5F5F5;}
	
	.topNavFix{width: 100%;height: 80rpx;position: fixed;top:88rpx;right: 0;left: 0;box-sizing: border-box;z-index: 22;}
	.topNavH{height: 80rpx;}
	
	.proRow .item{margin-bottom: 30rpx;padding-top: 20rpx;}
	.proRow .item .pic{width: 160rpx;height: 160rpx;}
	.proRow .item .infor{width: 72%;height: 160rpx;}
	
	.orderNav .tt.on::after{bottom: 0;width: 60rpx;height: 4rpx;}
</style>
