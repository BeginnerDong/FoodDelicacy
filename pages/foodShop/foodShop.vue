<template>
	<view>
		
		<view class="detailTBj pr">
			<view class="bj" >
				<image src="../../static/images/detailsl-img.png" mode=""></image>
			</view>
		</view>
		
		<view class="mglr4 detail-name pdlr4 pdt10 pdb10 whiteBj radius10 boxShaow" style="height: 270rpx;">
			<view class="flexRowBetween">
				<view class="name fs15 ll ">小吊梨汤(高新大都荟店)</view>
				<view class="rrBtn fs12 color6 flexEnd">
					<view class="btn" style="color: #FCC401;border: 1px solid #FCC401;" @click="Router.navigateTo({route:{path:'/pages/couponTake/couponTake'}})">优惠券</view>
				</view>
			</view>
			<view class="flex mgt5">
				<view class="starBox flex">
					<image src="../../static/images/home-icon5.png" mode=""></image>
					<image src="../../static/images/home-icon5.png" mode=""></image>
					<image src="../../static/images/home-icon5.png" mode=""></image>
					<image src="../../static/images/home-icon5.png" mode=""></image>
					<image src="../../static/images/home-icon6.png" mode=""></image>
				</view>
				<view class="mgl5 fs10 color9">月售615</view>
			</view>
			<view class="flexRowBetween mgt5 pdb10 borderB1">
				<view class="flex fs12 color9">
					<image class="shopIcon mgr5" src="../../static/images/home-icon3.png" mode=""></image>
					<view style="width: 480rpx;">雁塔区高新大都荟A座2007</view>
				</view>
				<view class="flexEnd fs11  color9">2.4km</view>
			</view>
			<view class="pdt10 flexRowBetween">
				<view class="flex">卡余额:<span class="red mgl10">25</span></view>
				<view class="flexEnd"><view class="changeBtn"  @click="Router.navigateTo({route:{path:'/pages/chargeMoney/chargeMoney'}})">充值</view></view>
			</view>
		</view>
		
		<view class="orderNav pdt5 pdb10 borderB1">
			<scroll-view class="snavScroll" scroll-x>
				<view class="tt" :class="snavCurr==index?'on':''" @click="snavChange(index)" v-for="(item,index) in snavData" :key="index">{{item}}</view>
			</scroll-view>
		</view>
		
		<view class="pdlr4 mgt15 foodList" v-show="selCurr==1">
			<view class="item" v-for="(item,index) in mainData" :key="index">
				<view class="pic" @click="albumsShow"><image src="../../static/images/detailsl-img1.png" mode=""></image></view>
				<view class="flexRowBetween mgt10">
					<view class="name fs12 avoidOverflow">咖喱鸡肉</view>
					<view class="likeIcon">
						<image src="../../static/images/home-icon8.png" v-if="item.isSelect" @click="choose(index)" mode=""></image>
						<image src="../../static/images/home-icon9.png" v-if="!item.isSelect" @click="choose(index)"></image>
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
		
		<view class="mglr4 mgt15" v-show="selCurr==2">
			<view class="boxShaow radius10 stallsBox mgb15" v-for="(item,index) in stallsData" :key="index">
				<view class="pdtb10 flexRowBetween">
					<view class="">外婆水饺</view>
					<view class="flexEnd color6 fs12"><image class="phoneIcon mgr5" src="../../static/images/detailsl-icon2.png" mode=""></image>15626352356</view>
				</view>
				<view class=" foodList">
					<view class="item" v-for="(item,index) in mainData" :key="index">
						<view class="pic" @click="albumsShow"><image src="../../static/images/detailsl-img1.png" mode=""></image></view>
						<view class="flexRowBetween mgt10">
							<view class="name fs12 avoidOverflow">咖喱鸡肉</view>
							<view class="likeIcon">
								<image src="../../static/images/home-icon8.png" v-if="item.isSelect" @click="choose(index)" mode=""></image>
								<image src="../../static/images/home-icon9.png" v-if="!item.isSelect" @click="choose(index)"></image>
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
		
		
		<!-- 图集弹框显示 -->
		<view class="black-bj" v-show="is_show"></view>
		<view class="albumsShow whiteBj radius10" v-show="is_albumsShow">
			<view class="pdb15">咖喱鸡肉饭</view>
			<view>
				<swiper class="swiper-box" indicator-dots="true" autoplay="true" interval="3000" duration="1000" indicator-active-color="#fcc401">
					<block v-for="(item,index) in labelData" :key="index">
						<swiper-item class="swiper-item">
							<image :src="item" class="slide-image" />
						</swiper-item>
					</block>
				</swiper>
			</view>
			<view class="fs12 mgt5">美式三文治/脆皮烤肠/奥尔良鸡肉</view>
			<view class="mgt5 flexRowBetween">
				<view class="flex">
					<view class="price ftw fs14">88</view>
					<view class="mgl10 fs10 color9">月售2365</view>
				</view>
				<view class="flexEnd">
					<view class="addCarBtn">加入购物车</view>
					<view class="addCarBtn mgl15"  @click="specsShow">选规格</view>
				</view>
			</view>
			<view class="closeBtn" @click="albumsShow">×</view>
		</view>
		
		<!-- 规格显示 -->
		<view class="albumsShow whiteBj radius10 fs14" style="padding: 0;" v-show="is_specsShow">
			<view class="closeBtn"@click="specsClose">×</view>
			<view class="box">
				<view class="center fs15 mgb15">咖喱鸡肉饭</view>
				<view class="">规格：</view>
				<view class="specsLis flex">
					<view class="btn" v-for="(item,index) in seltOneData" :key="index" :class="seltOne==index?'on':''" @click="seltOneChange(index)">{{item}}</view>
				</view>
				<view class="fs15">口味：</view>
				<view class="specsLis flex">
					<view class="btn" v-for="(item,index) in seltTwoData" :key="index" :class="seltTwo==index?'on':''" @click="seltTwoChange(index)">{{item}}</view>
				</view>
				<view class="fs15">种类：</view>
				<view class="specsLis flex">
					<view class="btn" v-for="(item,index) in seltThreeData" :key="index" :class="seltThree==index?'on':''" @click="seltThreeChange(index)">{{item}}</view>
				</view>
			</view>
			<view class="f5bj pdlr4 flexRowBetween" style="height: 100rpx;">
				<view class="price fs16">88</view>
				<view class="addCarBtn">加入购物车</view>
			</view>
		</view>
		
		<!-- 右侧固定按钮 -->
		<view class="R-fixIcon flexCenter fs13" @click="Router.navigateTo({route:{path:'/pages/orderConfim/orderConfim'}})"><view class="num">1</view><view>结算</view></view>
		
		<!--底部tab键-->
		<view class="navbar">
			<view class="navbar_item" @click="Router.redirectTo({route:{path:'/pages/foodShop/foodShop'}})">
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
			<view class="navbar_item" @click="Router.redirectTo({route:{path:'/pages/foodShop-user/foodShop-user'}})" >
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
				selCurr:1,
				storeData:[{},{},{},{},{}],
				foodShopData:[{},{},{},{},{}],
				labelData:[
					'../../static/images/detailsl-img2.png',
					'../../static/images/detailsl-img2.png'
				],
				is_albumsShow:false,
				snavCurr:0,
				snavData:['全部','面食','米饭','小吃','早餐','饮料','面食','米饭'],
				mainData:[
					{isSelect:true,price:'59.00',count:'1',isLable:false,isSeltbtn:false},
					{isSelect:false,price:'59.00',count:'1',isLable:true,isSeltbtn:false},
					{isSelect:false,price:'59.00',count:'1',isLable:true,isSeltbtn:true},
					{isSelect:false,price:'59.00',count:'1',isLable:true,isSeltbtn:false},
					{isSelect:false,price:'59.00',count:'1',isLable:true,isSeltbtn:false},
					{isSelect:true,price:'59.00',count:'1',isLable:false,isSeltbtn:true}
				],
				seltOne:0,
				seltOneData:['大份','小份'],
				seltTwo:0,
				seltTwoData:['麻辣','微辣','三鲜'],
				seltThree:0,
				seltThreeData:['杂酱','剁椒','油泼','西红柿鸡蛋','肉嗓子干饭'],
				is_specsShow:false,
				stallsData:[{},{}]
			}
		},
		onLoad() {
			const self = this;
			// self.$Utils.loadAll(['getMainData'], self);
		},
		methods: {
			back(){
				const self = this;
				self.$router.go(-1)
			},
			selCurrChange(selCurr){
				const self = this;
				if(selCurr!= self.selCurr){
					self.selCurr = selCurr
				}
			},
			snavChange(index){
				const self = this;
				self.snavCurr = index
			},
			albumsShow(){
				const self = this;
				self.is_show = !self.is_show
				self.is_albumsShow = !self.is_albumsShow
			},
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
			seltOneChange(index){
				const self = this;
				self.seltOne = index
			},
			seltTwoChange(index){
				const self = this;
				self.seltTwo = index
			},
			seltThreeChange(index){
				const self = this;
				self.seltThree = index
			},
			specsShow(){
				const self = this;
				self.is_show = true
				self.is_specsShow = !self.is_specsShow
				self.is_albumsShow = false
			},
			specsClose(){
				const self = this;
				self.is_show = false
				self.is_specsShow = false
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
	
	.changeBtn{width: 100rpx;height: 44rpx;line-height: 44rpx;text-align: center;border-radius: 30rpx;background: #222;color: #fff;font-size: 24rpx;box-shadow: 0 4rpx 6rpx rgba(0,0,0,0.2);}
	
</style>
