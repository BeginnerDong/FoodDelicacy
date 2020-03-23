<template>
	<view>
		
		<view class="userHead flex pdt20">
			<view><image class="photo" src="../../static/images/about-img.png" mode=""></image></view>
			<view style="width: 70%;">
				<view class="fs14 pdb5">哆啦A梦</view>
			</view>
		</view>
		
		<view class="userBox2 flexRowBetween color6 fs12 pdtb15 center">
			<view class="item" @click="Router.navigateTo({route:{path:'/pages/userOrder/userOrder'}})">
				<view class="icon">
					<image src="../../static/images/about-icon.png"></image>
				</view>
				<view>待核销</view>
			</view>
			<view class="item" @click="Router.navigateTo({route:{path:'/pages/userOrder/userOrder'}})">
				<view class="icon">
					<image src="../../static/images/about-icon1.png"></image>
				</view>
				<view>待收货</view>
			</view>
			<view class="item" @click="Router.navigateTo({route:{path:'/pages/userOrder/userOrder'}})">
				<view class="icon">
					<image src="../../static/images/about-icon2.png"></image>
				</view>
				<view>配送中</view>
			</view>
			<view class="item" @click="Router.navigateTo({route:{path:'/pages/userOrder/userOrder'}})">
				<view class="icon">
					<image src="../../static/images/about-icon3.png"></image>
				</view>
				<view>已完成</view>
			</view>
		</view>
		<view class="f5H5"></view>
		
		<view class="twoBox flexRowBetween mglr4 pdtb15 fs14">
			<view class="item flexColumn" @click="Router.navigateTo({route:{path:'/pages/user_address/user_address'}})">
				<view class="icon"><image src="../../static/images/about-icon4.png" mode=""></image></view>
				<view>收货地址</view>
			</view>
			<view class="item flexColumn" @click="Router.navigateTo({route:{path:'/pages/user-tidings/user-tidings'}})">
				<view class="icon"><image src="../../static/images/about-icon5.png" mode=""></image></view>
				<view>我的消息</view>
			</view>
			<view class="item flexColumn" @click="Router.navigateTo({route:{path:'/pages/user-myCoupon/user-myCoupon'}})">
				<view class="icon"><image src="../../static/images/about-icon6.png" mode=""></image></view>
				<view>我的优惠券</view>
			</view>
		</view>
		<view class="f5H5"></view>
		
		<view class="swiper pdtb15">
			<!-- <view class="swiper-title">{{title}}</view> -->
			<swiper class="swiper-tall pr" :indicator-dots="indicatorDots" :autoplay="autoplay" :previous-margin="previousMargin"
			 :next-margin="nextMargin" :circular="circular" @change="change" :current="swiperCurrentIndex">
				<swiper-item class="swiper-container" v-for="(img,index) in imgs" :key="index"
				 :item-id="index" :data-year="index">
					<view class="swiper-item" :animation="animationData[index]">
						<view class="flex fs12">
							<view class="logo mgr10"><image src="../../static/images/about-img1.png" mode=""></image></view>
							<view>小吊梨汤</view>
						</view>
						<view class="flexCenter pdtb20">
							<view class="fs15 ftw mny">卡余额：56</view>
						</view>
						<view class="flexCenter">
							<view class="btn" @click="Router.navigateTo({route:{path:'/pages/chargeMoney/chargeMoney'}})">充值</view>
						</view>
					   <image class="bj" src="../../static/images/about-img2.png" mode=""></image>
					</view>
				</swiper-item>
			</swiper>
		</view>
		
		
		<!--底部tab键-->
		<view class="navbar">
			<view class="navbar_item" @click="Router.redirectTo({route:{path:'/pages/index/index'}})">
				<view class="nav_img">
					<image src="../../static/images/nabar1.png" />
				</view>
				<view class="text">首页</view>
			</view>
			<view class="navbar_item" @click="Router.redirectTo({route:{path:'/pages/like/like'}})" >
				<view class="nav_img">
					<image src="../../static/images/nabar2.png" />
				</view>
				<view class="text">收藏</view>
			</view>
			<view class="navbar_item" @click="Router.redirectTo({route:{path:'/pages/car/car'}})" >
				<view class="nav_img">
					<image src="../../static/images/nabar3.png" />
				</view>
				<view class="text">购物车</view>
			</view>
			<view class="navbar_item" @click="Router.redirectTo({route:{path:'/pages/user/user'}})" >
				<view class="nav_img">
					<image src="../../static/images/nabar4-a.png" />
				</view>
				<view class="text this-text">我的</view>
			</view>
		</view>
		<!--底部tab键 end-->
		
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
				
				screenHeight: 0,
				animationData: {
					0:{},
					1:{},
					2:{}
				},
				title: '0',
				indicatorDots: false,
				autoplay: false,
				previousMargin: uni.upx2px(82)+'px',
				nextMargin: uni.upx2px(82)+'px',
				circular: true,
				zoomParam: 1.10,
				swiperCurrentIndex: 0,
				data: [],
				max: 0,
				imgs:[
					'../../static/images/about-img2.png',
					'../../static/images/about-img2.png',
					'../../static/images/about-img2.png'
				]
			}
		},
		computed:{
			fullHeight() {
				const res = uni.getSystemInfoSync();
				return res.windowHeight - uni.upx2px(60) - (res.statusBarHeight+44)+'px';
			}
		},
		onLoad() {
			const self = this;
			self.animation = uni.createAnimation();
			self.animation.scale(self.zoomParam).step();
			self.animationData[0] = self.animation.export();
			//self.$Utils.loadAll(['getMainData'], self);
		},
		methods: {
			change(e) {
				const self = this;
				self.swiperCurrentIndex = e.detail.current;
				self.title = e.detail.currentItemId;
				for (let key in self.animationData) {
					if (e.detail.currentItemId == key) {
						self.animation.scale(self.zoomParam).step();
						self.animationData[key] = self.animation.export();
					} else {
						self.animation.scale(1.0).step();
						self.animationData[key] = self.animation.export();
					}
				}
			}
		}
	};
</script>

<style>
	/* @import "../../assets/style/editInfor.css"; */
	@import "../../assets/style/navbar.css";
	page{padding-bottom: 140rpx;}
	
	.userHead{box-sizing: border-box;position: relative;width: 100%;/* height: 420rpx; */}
	.userHead .photo{width: 120rpx;height: 120rpx;border-radius: 50%;margin-right: 20rpx;border: 2px solid #ffecca;;box-sizing: border-box;}
	
	.userBox2{width: 100%;height: 160rpx;box-sizing: border-box;}
	.userBox2 .item{width: 25%;}
	.userBox2 .item .icon{width: 48rpx;height:48rpx;display: block;margin: 0 auto;margin-bottom: 10rpx;position: relative;}
	.userBox2 .item .icon image{width: 100%;height: 100%;}
	
	.twoBox .item{width: 33.33%;}
	.twoBox .item .icon{width: 60rpx;height: 60rpx;display: block;margin: 0 auto 20rpx auto;}
	.twoBox .item .icon image{width: 100%;height: 100%;}
	
	
	.swiper-container {
		display: flex;
		align-items: center;
		/* overflow:initial; */
	}
	.swiper-tall {
		display: flex;
		align-items: center;
		height: 400rpx;
	}
	.swiper-item {
		height: 300rpx;
		width: 530rpx;
		text-align: center;
		border-radius: 10rpx;
		margin: 30rpx auto;
		position: relative;
		padding: 20rpx;
		box-sizing: border-box;
	}
	.swiper-item .mny{letter-spacing: 6rpx;}
	.swiper-item .logo{width: 50rpx;height: 50rpx;border-radius: 50%;}
	.swiper-item image{width: 100%;height: 100%;}
	.swiper-item .btn{width: 140rpx;height: 56rpx;line-height: 56rpx;text-align: center;color: #fff;background: #FCC401;border-radius: 30rpx;}
	.swiper-item .bj{position: absolute;top: 0;right: 0;bottom: 0;left: 0;z-index: -1;}
	
	
</style>
