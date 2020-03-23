<template>
	<view>
		
		<view class="mglr4 mgt15">
			<view class="cuponList">
				<view class="item mgb15" v-for="(item,index) in cuponList" :key="index"  @click="takeOk()">
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
						<view class="rrTex">点击领取</view>
					</view>
					
				</view>
			</view>
			
		</view>
		
		<!-- 无数据时显示 -->
		<view class="nodata" style="width: 378rpx;height: 409rpx;"><image src="../../static/images/couponsl-img4.png" mode=""></image></view>
		
		<view class="takeOkShow flexCenter white" v-show="is_takeOkShow">
			<view class="center">领取成功</view>
			<view class="closeBtn" @click="takeOk()">×</view>
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
				is_show:false,
				cuponList:[{},{}],
				seltCurr:0,
				is_takeOkShow:false
			}
		},
		onLoad() {
			const self = this;
			//self.$Utils.loadAll(['getMainData'], self);
		},
		methods: {
			takeOk(){
				const self = this;
				self.is_takeOkShow = !self.is_takeOkShow
			}
		}
	};
</script>

<style>
	@import "../../assets/style/orderNav.css";
	@import "../../assets/style/cupon.css";
	page{background: #F5F5F5;padding-bottom: 140rpx;}
	.takeOkShow{width: 320rpx;height: 120rpx;border-radius: 10rpx;background: rgba(0,0,0,0.5);position: fixed;top: 50%;left: 50%;transform: translate(-50%,-50%); z-index: 55;}
	.closeBtn{bottom: auto;left: auto;top: -24rpx;right: -44rpx;}
</style>
