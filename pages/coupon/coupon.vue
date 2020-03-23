<template>
	<view>
		
		<view class="flex orderNav center color6 whiteBj">
			<view class="tt" :class="curr==1?'on':''" @click="currChange('1')">可用优惠券</view>
			<view class="tt" :class="curr==2?'on':''" @click="currChange('2')">不可用优惠券</view>
		</view>
		<view class="mglr4 mgt15">
			<view class="cuponList" v-if="curr==1">
				<view class="item mgb15" v-for="(item,index) in cuponList" :key="index"  @click="seltCurrChange(index)">
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
						<view class="rrTex">
								<image class="seltIcon" :src="seltCurr==index?'../../static/images/couponsl-icon.png':''" mode=""></image>
						</view>
					</view>
					
				</view>
			</view>
			
			<view class="cuponList noCan" v-if="curr==2">
				<view class="item mgb15" v-for="(item,index) in cuponList" :key="index"  >
					<view class="infor">
						<view class="bj"><image src="../../static/images/couponsl-img5.png" mode=""></image></view>
						<view class="flexRowBetween">
							<view class="left flexCenter">
								<view class="mny">20</view>
							</view>
							<view class="text">
								<view class="fs15 ftw color9 avoidOverflow">小吊梨汤</view>
								<view class="fs12 color9 mgt10">仅限制定商品</view>
								<view class="color9 fs10 mgt5 ">满100使用</view>
							</view>
						</view>
						<view class="data color9 fs10 center">有效期：2019.09.19-2019.09-30</view>
						<view class="rrTex">
							不可用
						</view>
					</view>
					
					<view class="f5bj pdlr4 pdt20 pdb10 reason" >
						<view class="fs13">不可使用原因</view>
						<view class="color9 fs12">订单中没有符合条件的商品</view>
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
	
</style>
