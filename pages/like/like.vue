<template>
	<view>
		
		<view class="mglr4 mgt15">
			<view class="boxShaow radius10 stallsBox mgb15" v-for="(item,index) in stallsData" :key="index">
				<view class="pdtb10 flexRowBetween">
					<view class="">外婆水饺</view>
					<view class="flexEnd color6 fs12"><image class="phoneIcon mgr5" src="../../static/images/detailsl-icon2.png" mode=""></image>15626352356</view>
				</view>
				<view class=" foodList">
					<view class="item" v-for="(item,index) in mainData" :key="index" @click="Router.navigateTo({route:{path:'/pages/foodShopDetail/foodShopDetail'}})">
						<view class="pic"><image src="../../static/images/detailsl-img1.png" mode=""></image></view>
						<view class="flexRowBetween mgt10">
							<view class="name fs12 avoidOverflow">咖喱鸡肉</view>
							<view class="likeIcon">
								<image src="../../static/images/home-icon8.png" mode=""></image>
							</view>
						</view>
						<view class="flexRowBetween mgt10">
							<view class="price fs13">88</view>
							<view class="flexEnd">
								<view class="numBox flex">
									<view class="btn" @click="counter(index,'-')">-</view>
									<view class="num">{{item.count}}</view>
									<view class="btn pubBj white add" @click="counter(index,'+')">+</view>
								</view>
							</view>
						</view>
						<view class="fs10 color6 pdt5" v-if="item.isLable">小份+微辣+油泼</view>
						<view class="flexEnd pdt5" v-if="item.isSeltbtn"><view class="selBtn flexCenter"  @click="specsShow">选规格</view></view>
					</view>
				</view>
			</view>
		</view>
		
		<!-- 无数据时显示 -->
		<view class="nodata"><image src="../../static/images/nodata.png" mode=""></image></view>
		
	
		
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
					<image src="../../static/images/nabar2-a.png" />
				</view>
				<view class="text this-text">收藏</view>
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
				mainData:[
					{isSelect:true,price:'59.00',count:'1',isLable:false,isSeltbtn:false},
					{isSelect:false,price:'59.00',count:'1',isLable:true,isSeltbtn:false},
					{isSelect:false,price:'59.00',count:'1',isLable:true,isSeltbtn:true},
					{isSelect:false,price:'59.00',count:'1',isLable:true,isSeltbtn:false},
					{isSelect:false,price:'59.00',count:'1',isLable:true,isSeltbtn:false},
					{isSelect:true,price:'59.00',count:'1',isLable:false,isSeltbtn:true}
					
				],
				stallsData:[{},{}]
			}
		},
		onLoad() {
			const self = this;
			// self.$Utils.loadAll(['getMainData'], self);
		},
		methods: {
			counter(index,type) {
				const self = this;
				if (type == '+') {
					self.mainData[index].count++;
				} else {
					if (self.mainData[index].count > 1) {
						self.mainData[index].count--;
					}
				};
				self.$Utils.setStorageArray('cartData', self.mainData[index], 'id', 999);
				self.countTotalPrice();
			},
			choose(index) {
				const self = this;
				
				if (self.mainData[index].isSelect) {
					self.mainData[index].isSelect = false;
				} else {
					self.mainData[index].isSelect = true;
				};
				self.$Utils.setStorageArray('cartData', self.mainData[index], 'id', 999);
				
				self.checkChooseAll();
				self.countTotalPrice();
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
	@import "../../assets/style/detail.css";
	@import "../../assets/style/orderNav.css";
	
	page{padding-bottom: 140rpx;}	
	
	
	.swiper-box{width: 600rpx;height: 600rpx;margin: 0 auto;box-sizing: border-box;overflow: hidden;border-radius: 10rpx;}
	.swiper-box swiper-item{width: 100%;box-sizing: border-box;overflow: hidden;}
	.swiper-box swiper-item image{width: 100%;height: 100%;box-sizing: border-box;}
	
	
	
</style>
