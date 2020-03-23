<template>
	<view>
		
		<view class="userHead pdl15 pdt20 flexRowBetween whiteBj">
			<view class="flex" style="width: 70%;">
				<view><image class="photo" src="../../static/images/about-img.png" mode=""></image></view>
				<view style="width: 70%;">
					<view class="fs14">哆啦A梦</view>
				</view>
			</view>
			<view class="pubBj pdl10 pdr10" style="height: 56rpx;line-height: 56rpx;border-radius:30rpx 0 0 30rpx;letter-spacing: 4rpx;" @click="Router.redirectTo({route:{path:'/pages/index/index'}})">切换美食荟</view>
		</view>
		
		<view class="userBox2 flexRowBetween color6 fs12 pdtb15 center whiteBj">
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
		
		<view class="twoBox flexRowBetween pdlr4 pdt15 pdb15 fs14 whiteBj">
			<view class="item flexColumn" @click="Router.navigateTo({route:{path:'/pages/user_address/user_address'}})">
				<view class="icon"><image src="../../static/images/about-icon4.png" mode=""></image></view>
				<view>收货地址</view>
			</view>
			<view class="item flexColumn" @click="Router.navigateTo({route:{path:'/pages/user-tidings/user-tidings'}})">
				<view class="icon"><image src="../../static/images/about-icon5.png" mode=""></image></view>
				<view>我的消息</view>
			</view>
		</view>
		<view class="f5H5"></view>
		
		
		<!--底部tab键-->
		<view class="navbar">
			<view class="navbar_item" @click="Router.redirectTo({route:{path:'/pages/snackShop/snackShop'}})">
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
			<view class="navbar_item" @click="Router.redirectTo({route:{path:'/pages/snackShop-user/snackShop-user'}})" >
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
				wx_info:{}
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
	/* @import "../../assets/style/editInfor.css"; */
	@import "../../assets/style/navbar.css";
	page{padding-bottom: 140rpx;background: #F5F5F5;}
	
	.userHead{box-sizing: border-box;position: relative;width: 100%;/* height: 420rpx; */}
	.userHead .photo{width: 120rpx;height: 120rpx;border-radius: 50%;margin-right: 20rpx;border: 2px solid #ffecca;;box-sizing: border-box;}
	
	.userBox2{width: 100%;height: 160rpx;box-sizing: border-box;}
	.userBox2 .item{width: 25%;}
	.userBox2 .item .icon{width: 48rpx;height:48rpx;display: block;margin: 0 auto;margin-bottom: 10rpx;position: relative;}
	.userBox2 .item .icon image{width: 100%;height: 100%;}
	
	.twoBox .item{width: 50%;}
	.twoBox .item .icon{width: 60rpx;height: 60rpx;display: block;margin: 0 auto 20rpx auto;}
	.twoBox .item .icon image{width: 100%;height: 100%;}
	
	
	
	.cards {
		height: 357rpx;
		width: 100%;
		text-align: center;
		border-radius: 10rpx;
		margin: 30rpx auto;
		position: relative;
		padding: 20rpx;
		box-sizing: border-box;
	}
	.cards .mny{letter-spacing: 6rpx;}
	.cards .logo{width: 50rpx;height: 50rpx;border-radius: 50%;}
	.cards image{width: 100%;height: 100%;}
	.cards .btn{width: 140rpx;height: 56rpx;line-height: 56rpx;text-align: center;color: #fff;background: #FCC401;border-radius: 30rpx;}
	.cards .bj{position: absolute;top: 0;right: 0;bottom: 0;left: 0;z-index: -1;}
	
	
</style>
