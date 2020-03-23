<template>
	<view>
		
		<view class="flex orderNav center color6 whiteBj">
			<view class="tt" :class="curr==1?'on':''" @click="currChange('1')">待使用</view>
			<view class="tt" :class="curr==2?'on':''" @click="currChange('2')">已使用</view>
			<view class="tt" :class="curr==3?'on':''" @click="currChange('3')">已过期</view>
		</view>
		<view class="mglr4 mgt15">
			<view class="cuponList" v-if="curr==1">
				<view class="item mgb15" v-for="(item,index) in cuponList" :key="index">
					<view class="infor">
						<view class="bj"><image src="../../static/images/couponsl-img.png" mode=""></image></view>
						<view class="flexRowBetween">
							<view class="left flexCenter">
								<view class="mny">20</view>
							</view>
							<view class="text">
								<view class="fs15 ftw avoidOverflow">小吊梨汤</view>
								<view class="fs12 color6 mgt10">仅限制定商品</view>
								<view class="color9 fs10 mgt5 ">满100使用</view>
							</view>
						</view>
						<view class="data color9 fs10 center">有效期：2019.09.19-2019.09-30</view>
						<view class="rrTex">点击使用</view>
					</view>
				</view>
			</view>
			
			<view class="cuponList" v-if="curr==2">
				<view class="item mgb15" v-for="(item,index) in cuponList" :key="index" >
					<view class="infor">
						<view class="bj"><image src="../../static/images/couponsl-img.png" mode=""></image></view>
						<view class="userIcon"><image src="../../static/images/couponsl-img2.png" mode=""></image></view>
						<view class="flexRowBetween">
							<view class="left flexCenter">
								<view class="mny">20</view>
							</view>
							<view class="text">
								<view class="fs15 ftw avoidOverflow">小吊梨汤</view>
								<view class="fs12 color6 mgt10">仅限制定商品</view>
								<view class="color9 fs10 mgt5 ">满100使用</view>
							</view>
						</view>
						<view class="data color9 fs10 center">有效期：2019.09.19-2019.09-30</view>
						<view class="rrTex">已使用</view>
					</view>
				</view>
			</view>
			
			<view class="cuponList" v-if="curr==3">
				<view class="item mgb15" v-for="(item,index) in cuponList" :key="index" >
					<view class="infor">
						<view class="bj"><image src="../../static/images/couponsl-img.png" mode=""></image></view>
						<view class="userIcon"><image src="../../static/images/couponsl-img1.png" mode=""></image></view>
						<view class="flexRowBetween">
							<view class="left flexCenter">
								<view class="mny">20</view>
							</view>
							<view class="text">
								<view class="fs15 ftw avoidOverflow">小吊梨汤</view>
								<view class="fs12 color6 mgt10">仅限制定商品</view>
								<view class="color9 fs10 mgt5 ">满100使用</view>
							</view>
						</view>
						<view class="data color9 fs10 center">有效期：2019.09.19-2019.09-30</view>
						<view class="rrTex">已过期</view>
					</view>
				</view>
			</view>
			
		</view>
		
		<!-- 无数据时显示 -->
		<view class="nodata" style="width: 378rpx;height: 409rpx;"><image src="../../static/images/couponsl-img4.png" mode=""></image></view>
		
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
				curr:1,
				cuponList:[{},{}],
				seltCurr:0
			}
		},
		onLoad() {
			const self = this;
			//self.$Utils.loadAll(['getMainData'], self);
		},
		methods: {
			currChange(curr){
				const self = this;	
				if(curr!=self.curr){
					self.curr = curr
				}
			},
			seltCurrChange(index){
				const self = this;
				self.seltCurr = index
			}
		}
	};
</script>

<style>
	@import "../../assets/style/orderNav.css";
	@import "../../assets/style/cupon.css";
	page{background: #F5F5F5;padding-bottom: 140rpx;}
	.userIcon{width: 160rpx;height: 160rpx;position: absolute;top: 50%;right: 60rpx;transform: translateY(-50%);}
	.userIcon image{width: 100%;height: 100%;}
</style>
