<template>
	<view>
		<view class="mglr4 mgt15">
			<view class="flex seltTake center fs12 color6">
				<view class="btn" :class="curr==1?'on':''" @click="currChange('1')">外卖订单</view>
				<view class="btn" :class="curr==2?'on':''" @click="currChange('2')">食堂包邮</view>
			</view>
			<view class="" v-show="curr==1">
				<view class="whiteBj radius10 mgb15" >
					<view><image class="w" style="height: 8rpx;" src="../../static/images/the-orderl-icon.png" mode="widthFix"></image></view>
					<view class="pdlr4 pdt10 pdb15 flexCenter fs14 color6" style="height: 140rpx;box-sizing: border-box;" @click="Router.navigateTo({route:{path:'/pages/user_address/user_address'}})">
						<image style="width: 30rpx;height: 30rpx;" src="../../static/images/addressl-icon4.png" mode=""></image>
						<view class="mgl10">添加地址</view>
					</view>
				</view>
				<view class="whiteBj radius10 mgb15" >
					<view><image class="w" style="height: 8rpx;" src="../../static/images/the-orderl-icon.png" mode="widthFix"></image></view>
					<view class="pdlr4 pdt10 pdb15">
						<view class="flexRowBetween" @click="Router.navigateTo({route:{path:'/pages/user_address/user_address'}})">
							<view class="fs13 color6">
								<view class="flex mgt5">
									<view class="mgr15 color2">张思德</view>
									<view>15689562352</view>
								</view>
								<view class="mgt5">陕西省西安市雁塔区高新大都荟</view>
							</view>
							<view class="flexEnd" style="width: 20%;">
								<image class="arrowR" src="../../static/images/home-icon7.png" mode=""></image>
							</view>
						</view>
					</view>
				</view>
			</view>
			
			<view class="proRow mgt15 radius10 whiteBj oh pdt15">
				<view class="flex pdlr4 mgb10">
					<view class="storeIcon"><image src="../../static/images/shopping-icon.png" mode=""></image></view>
					<view class="fs13 mgl10">小龙坎</view>
				</view>
				<view class="item flexRowBetween" >
					<view class="pic oh"><image src="../../static/images/the-orderl-img.png" mode=""></image></view>
					<view class="infor">
						<view class="tit">好孩子儿童餐具宝宝学吃饭</view>
						<view class="color6 fs10">小份+微辣+杂酱</view>
						<view class="flexRowBetween B-price">
							<view class="price ftw">88</view>
							<view class="flexEnd color9 fs13">×1</view>
						</view>
					</view>
				</view>
				<view class="item flexRowBetween" >
					<view class="pic"><image src="../../static/images/the-orderl-img.png" mode=""></image></view>
					<view class="infor">
						<view class="tit">好孩子儿童餐具宝宝学吃饭</view>
						<view class="color6 fs10">小份+微辣+杂酱</view>
						<view class="flexRowBetween B-price">
							<view class="price ftw">88</view>
							<view class="flexEnd color9 fs13">×1</view>
						</view>
					</view>
				</view>
			</view>
		
			<view class="pdlr4 pdt15 pdb15 mgt15 radius10 whiteBj oh flexRowBetween">
				<view>优惠券</view>
				<view class="flexEnd fs10" @click="Router.navigateTo({route:{path:'/pages/coupon/coupon'}})">-20元<image class="arrowR" src="../../static/images/home-icon7.png" mode=""></image></view>
			</view>
			
			<view class="pdlr4 pdt15 pdb15 mgt15 radius10 whiteBj oh flex">
				<view class="mgr10">备注</view>
				<view class="beizhu"><input type="text" value="" placeholder="请输入备注" placeholder-class="placeholder" /></view>
			</view>
		</view>
		
		<view class="xqbotomBar">
			<view class="flex mgl15 fs12">总计：<view class="price fs14 ftw">178</view></view>
			<view class="payBtn">结算</view>
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
				curr:1
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
			}
		}
	};
</script>

<style>
	@import "../../assets/style/detail.css";
	@import "../../assets/style/proList.css";
	page{background: #F5F5F5;padding-bottom: 140rpx;}
	
	
	.storeIcon image{width: 28rpx;height: 28rpx;}
	.seltTake .btn{width: 140rpx;height: 44rpx;line-height: 44rpx;border-radius: 30rpx;border: 1px solid #d0d0d0;margin: 0 30rpx 30rpx 0;}
	.seltTake .btn.on{color: #fcc401;border-color: #fcc401;}
	
	.proRow .item{padding-top: 0;}
	.proRow .item .pic{width: 140rpx; height: 140rpx;border-radius: 10rpx;}
	.proRow .item .infor{width: 75%; height: 140rpx;}
	
	.beizhu{width: 85%;}
	.beizhu input{width: 100%;height: 40rpx;line-height: 40px;font-size: 26rpx;color: #666;}
	
</style>
