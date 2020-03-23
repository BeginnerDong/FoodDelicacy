<template>
	<view>
		
		<view class="topSeach flexRowBetween boxShaow">
			<view class="flex ftw">西安·雁塔区<image style="width: 20rpx;height: 11rpx;margin-left: 10rpx;" src="../../static/images/home-icon.png" mode=""></image></view>
			<view class="seachbox" style="width: 468rpx;">
				<view class="flex rr" style="width: 100%;">
					<button class="seachBtn" type="button"><image src="../../static/images/home-icon1.png" mode=""></image></button>
					<view class="input">
						<input type="text" name="" value="" placeholder="搜索" placeholder-class="placeholder" />
					</view>
				</view>
			</view>
		</view>
		<view class="topSeachH"></view>
		
		<view class="pdt10 pdb5 flexRowBetween orderNav fs15 color6">
			<view class="tt" :class="curr==1?'on':''" @click="changeCurr('1')">附近小吃城</view>
			<view class="tt" :class="curr==2?'on':''" @click="changeCurr('2')">附近美食店</view>
		</view>
		
		<!-- 小吃店列表 -->
		<view class="pdlr4 snackList" v-show="curr==1">
			<view class="item boxShaow radius10 mgb15" v-for="(item,index) in storeData" :key="index" @click="Router.navigateTo({route:{path:'/pages/snackDetail/snackDetail'}})">
				<view class="flexCenter pdb15">
					<view class="storeName">
						<view class="bj"><image src="../../static/images/home-icon2.png" mode=""></image></view>
						<view class="tit">老伙夫小吃城(雁塔区)</view>
					</view>
				</view>
				<view class="flex fs12">
					<view class="L-icon"><image src="../../static/images/home-icon3.png" mode=""></image></view>
					<view class="avoidOverflow">陕西省西安市雁塔区高新大都荟4号楼2009</view>
				</view>
				<view class="infor flexRowBetween pdt10 fs12 color9">
					<view class="flex ll">
						<view class="L-icon"><image src="../../static/images/home-icon4.png" mode=""></image></view>
						<view class="">
							<view class="flex">
								<view class="color6">快餐小吃</view>
								<view class="pdl10 pdr5">37分钟</view>
								<view>2.4km</view>
							</view>
							<view class="flex mgt5">
								<view class="starBox flex">
									<image src="../../static/images/home-icon5.png" mode=""></image>
									<image src="../../static/images/home-icon5.png" mode=""></image>
									<image src="../../static/images/home-icon5.png" mode=""></image>
									<image src="../../static/images/home-icon5.png" mode=""></image>
									<image src="../../static/images/home-icon6.png" mode=""></image>
								</view>
								<view class="mgl5 fs10">月售615</view>
							</view>
						</view>
					</view>
					
					<view class="rr flexRowBetween">
						<view class="flex imgs">
							<image src="../../static/images/home-img.png" mode=""></image>
							<image src="../../static/images/home-img.png" mode=""></image>
						</view>
						<view class="flexEnd" @click="albumsShow">图集<image class="arrowR mgl5" src="../../static/images/home-icon7.png" mode=""></image></view>
					</view>
					
				</view>
				
			</view>
		</view>
		
		<!-- 美食店列表 -->
		<view class="pdlr4 foodShop" v-show="curr==2">
			<view class="item flexRowBetween" v-for="(item,index) in foodShopData" :key="index"  @click="Router.navigateTo({route:{path:'/pages/foodShopDetail/foodShopDetail'}})">
				<view class="pic"><image src="../../static/images/home-img1.png" mode=""></image></view>
				<view class="infor">
					<view class="avoidOverflow fs15 ftw">小吊梨汤<span class="mgl10">(高新大都荟店)</span></view>
					<view class="flex mgt5">
						<view class="starBox flex">
							<image src="../../static/images/home-icon5.png" mode=""></image>
							<image src="../../static/images/home-icon5.png" mode=""></image>
							<image src="../../static/images/home-icon5.png" mode=""></image>
							<image src="../../static/images/home-icon5.png" mode=""></image>
							<image src="../../static/images/home-icon6.png" mode=""></image>
						</view>
						<view class="mgl5 fs10 color6">月售615</view>
					</view>
					<view class="flexRowBetween fs11 color6 mgt5">
						<view class="flex addrs">
							<view>
								<image class="drsIcon" src="../../static/images/home-icon3.png" mode=""></image>
							</view>
							<view class="tex avoidOverflow">雁塔区高新大都荟A座2007</view>
						</view>
						<view class="flexEnd">2.4km</view>
					</view>
				</view>
			</view>
		</view>
		
		<!-- 无数据时显示 -->
		<view class="nodata"><image src="../../static/images/nodata.png" mode=""></image></view>
		
		<!-- 图集弹框显示 -->
		<view class="black-bj" v-show="is_show"></view>
		<view class="albumsShow whiteBj radius10" v-show="is_albumsShow">
			<view class="pdb15 center">老火锅小吃城(雁塔区)</view>
			<view>
				<swiper class="swiper-box" indicator-dots="true" autoplay="true" interval="3000" duration="1000" indicator-active-color="#fcc401">
					<block v-for="(item,index) in labelData" :key="index">
						<swiper-item class="swiper-item">
							<image :src="item" class="slide-image" />
						</swiper-item>
					</block>
				</swiper>
			</view>
			<view class="closeBtn" @click="albumsShow">×</view>
		</view>
		
		
		<!--底部tab键-->
		<view class="navbar">
			<view class="navbar_item" @click="Router.redirectTo({route:{path:'/pages/index/index'}})">
				<view class="nav_img">
					<image src="../../static/images/nabar1-a.png" />
				</view>
				<view class="text this-text">首页</view>
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
					<image src="../../static/images/nabar4.png" />
				</view>
				<view class="text">我的</view>
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
				is_show: false,
				wx_info:{},
				is_show:false,
				curr:1,
				storeData:[{},{},{},{},{}],
				foodShopData:[{},{},{},{},{}],
				labelData:[
					'../../static/images/detailsl-img2.png',
					'../../static/images/detailsl-img2.png'
				],
				is_albumsShow:false
			}
		},
		onLoad() {
			const self = this;
			// self.$Utils.loadAll(['getMainData'], self);
		},
		methods: {
			changeCurr(curr){
				const self = this;
				if(curr!= self.curr){
					self.curr = curr
				}
			},
			albumsShow(){
				const self = this;
				self.is_show = !self.is_show
				self.is_albumsShow = !self.is_albumsShow
			},
			getMainData() {
				const self = this;
				console.log('852369')
				const postData = {};
				postData.tokenFuncName = 'getProjectToken';
				self.$apis.orderGet(postData, callback);
			}
		}
	};
</script>

<style>
	@import "../../assets/style/navbar.css";
	@import "../../assets/style/seach.css";
	@import "../../assets/style/orderNav.css";
	
	page{padding-bottom: 140rpx;}	
	.topSeach{padding: 30rpx 4%;position:fixed ;top: 88rpx;right: 0;left: 0; z-index: 2;background: #fff;}
	.topSeachH{height: 120rpx;}
	
	.orderNav .tt.on{font-weight: bold; color: #222;}
	.orderNav .tt.on:after{background: #fcc401;width: 120rpx;height: 10rpx;bottom:26rpx ;z-index: -1;}
	
	.L-icon image{width: 28rpx;height: 28rpx; margin-right: 20rpx;}
	
	
	/* 小吃店列表 */
	.snackList .item{width: 100%;height: 286rpx;box-sizing: border-box;background: #fff;padding: 30rpx 4%;}
	.storeName{min-width: 420rpx;height: 66rpx;box-sizing: border-box;border-radius: 35rpx;position: relative;}
	.storeName .bj,.storeName .bj image{width:100%;height: 66rpx;}
	.storeName .tit{width: 100%;text-align: center;height: 62rpx;box-sizing: border-box;line-height: 58rpx;position: absolute;top: 50%;left: 50%;transform: translate(-50%,-50%);padding: 0 30rpx;}
	.snackList .item .infor{line-height: 30rpx;}
	.snackList .item .ll{width: 55%;height: 70rpx;align-items: flex-start;position: relative;}
	.snackList .item .ll .L-icon{margin-top: 4rpx;}
	.snackList .item .ll:after{content: '';position: absolute;right: 0;top: 50%;transform: translateY(-50%);width: 1px;height: 50rpx;background: #eee;}
	.snackList .item .rr{width: 40%;}
	.snackList .item .rr .imgs image{width: 66rpx;height: 66rpx;margin-right: 10rpx;}
	
	/* 美食店列表 */
	.foodShop .item{width: 100%;height: 130rpx;box-sizing: border-box;background: #fff;margin-bottom: 50rpx;}
	.foodShop .item .pic{width: 180rpx;height: 130rpx;}
	.foodShop .item .pic image{width: 100%;height: 100%;}
	.foodShop .item .infor{width: 71%;line-height: 36rpx;}
	.foodShop .item .infor .drsIcon{width: 28rpx;height: 28rpx;margin-right: 6rpx;}
	.foodShop .item .infor .addrs{width: 78%;}
	
	
	.albumsShow{width: 92%;background: #fff;position: fixed;top: 18%;left: 50%;transform: translateX(-50%);z-index: 50;padding: 30rpx 45rpx;box-sizing: border-box;}
	.swiper-box{width: 600rpx;height: 600rpx;margin: 0 auto;box-sizing: border-box;overflow: hidden;border-radius: 10rpx;}
	.swiper-box swiper-item{width: 100%;box-sizing: border-box;overflow: hidden;}
	.swiper-box swiper-item image{width: 100%;height: 100%;box-sizing: border-box;}
</style>
