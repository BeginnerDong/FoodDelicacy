<template>
	<view>
		
		<view class="mglr4">
			<view class=" pdtb15 flexRowBetween">
				<view>全部宝贝(3)</view>
				<view class="fs13"  v-show="!is_allDelt" @click="allDeltShow">管理</view>
				<view class="fs13"  v-show="is_allDelt" @click="allDeltShow">完成</view>
			</view>
			
			 <view class="proRow whiteBj radius10 oh mgb15">
				 <view class="flex pdlr4 pdt15">
					<view class="mgr10">
						 <image class="seltIcon mgr5" src="../../static/images/shopping-icon1.png" ></image>
					</view>
					<view class="flex fs13">
						<image class="shopIcon mgr5" src="../../static/images/shopping-icon.png" mode=""></image>
						<view>美食城名称</view>
					</view>
				 </view>
			 	<view class="item flexRowBetween borderB1" v-for="(item,index) in mainData" :key="index">
					<view class="item_selBtn flex">
						<image class="seltIcon" src="../../static/images/shopping-icon1.png" v-if="!item.isSelect" @click="choose(index)"></image>
						<image class="seltIcon" src="../../static/images/shopping-icon2.png" v-if="item.isSelect" @click="choose(index)"></image>
					</view>
					<view class="R_cont flexRowBetween">
						<view class="pic"><image src="../../static/images/the-orderl-img.png" mode=""></image></view>
						<view class="infor">
			 			<view class="tit fs13">咖喱鸡肉饭</view>
						<view class="flexRowBetween">
							<view class="fs12 color6">小份+微辣+杂酱</view>
							<view class="selBtn" @click="specsShow">选规格</view>
						</view>
							<view class="flexRowBetween B-price">
								<view class="price ftw">{{item.price}}</view>
								<view class="flexEnd">
									<view class="numBox flex">
										<view class="btn" @click="counter(index,'-')">-</view>
										<view class="num">{{item.count}}</view>
										<view class="btn pubBj white add" @click="counter(index,'+')">+</view>
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
		
		
		<!-- 底部结算 -->
		<view class="xqbotomBar flexRowBetween borderB1 pdl15"  style="bottom: 110rpx;">
			<view class="left flex fs13">
				<view class="">
					<image class="seltIcon mgr5" @click="chooseAll" v-show="!isChooseAll" src="../../static/images/shopping-icon1.png" ></image>
					<image class="seltIcon mgr5" @click="chooseAll" v-show="isChooseAll" src="../../static/images/shopping-icon2.png" ></image>
				</view>
				<view>全选</view>
			</view>
			<view class="flexEnd" v-show="!is_allDelt">
				<view class="fs12 mgr15 flexEnd">合计<view class="price fs14">{{totalPrice}}</view></view>
				<view class="payBtn fs16 white" style="width: 260rpx; color: #222;"  @click="Router.navigateTo({route:{path:'/pages/orderConfim/orderConfim'}})">结算</view>
			</view>
			<view class="pubColor flexEnd mgr15" style="width: 34%;" v-show="is_allDelt"><view class="alldeltBtn" @click="deleteAll()">删除</view></view>
		</view>
		
		<view class="black-bj" v-show="is_show"></view>
		<!-- 规格显示 -->
		<view class="albumsShow whiteBj radius10 fs14" style="padding: 0;" v-show="is_specsShow">
			<view class="closeBtn" @click="specsShow">×</view>
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
					<image src="../../static/images/nabar3-a.png" />
				</view>
				<view class="text this-text">购物车</view>
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
				showView: false,
				wx_info:{},
				is_show:false,
				count:1,
				mainData:[
					{isSelect:true,price:'59.00',count:'1'},
					{isSelect:false,price:'59.00',count:'1'}
				],
				is_allDelt:false,
				isChooseAll:false,
				totalPrice:"59",
				seltOne:0,
				seltOneData:['大份','小份'],
				seltTwo:0,
				seltTwoData:['麻辣','微辣','三鲜'],
				seltThree:0,
				seltThreeData:['杂酱','剁椒','油泼','西红柿鸡蛋','肉嗓子干饭'],
				is_specsShow:false,
			}
		},
		
		onLoad(options) {
			const self = this;
			// self.$Utils.loadAll(['getMainData'], self);
		},
		methods: {
			allDeltShow(){
				const self = this;
				self.is_allDelt = !self.is_allDelt
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
				self.is_show = !self.is_show
				self.is_specsShow = !self.is_specsShow
			},
			deleteAll() {
				const self = this;
				uni.showModal({
					title: '提示',
					content: '确认要删除选中商品吗？',
					showCancel: true,
					cancelText: '取消',
					confirmText: '确认',
					success: res => {
						if (res.confirm) {
							for (var i = 0; i < self.mainData.length; i++) {
								if(self.mainData[i].isSelect){
									self.$Utils.delStorageArray('cartData', self.mainData[i], 'id');
								}
							};
							self.mainData = self.$Utils.getStorageArray('cartData');
						} else if (res.cancel) {
							console.log('用户点击取消');
						}
					},
				});
			},
			checkChooseAll() {
				const self = this;
				var isChooseAll = true;
				for (var i = 0; i < self.mainData.length; i++) {
					if (!self.mainData[i].isSelect) {
						isChooseAll = false;
					};
				};
				self.isChooseAll = isChooseAll;
			},
			
			chooseAll() {
				const self = this;
				self.isChooseAll = !self.isChooseAll;
				for (var i = 0; i < self.mainData.length; i++) {
					self.mainData[i].isSelect = self.isChooseAll;
					self.$Utils.setStorageArray('cartData', self.mainData[i], 'id', 999);
				};
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
			
			countTotalPrice() {
				const self = this;
				self.totalPrice = 0;
				
				for (var i = 0; i < self.mainData.length; i++) {
					if (self.mainData[i].isSelect) {
						self.totalPrice += self.mainData[i].price * self.mainData[i].count;
					};
				};
				console.log(self.totalPrice)
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
	@import "../../assets/style/proList.css";
	
	page{padding-bottom: 240rpx;background: #F5F5F5;}
	
	
	.proRow .item{align-items: center;border-radius: 0;}
	.proRow .item:last-child{border-bottom: 0;}
	.proRow .item .pic{width: 140rpx; height: 140rpx;}
	.proRow .item .infor{height: 140rpx;width: 73%;}
	
	.proRow .item .R_cont{width: 90%; align-items: flex-start;}
	
	/* 商城商品列表 */
	.item_selBtn{width: 10%;}
	.seltIcon{width:36rpx; height: 36rpx; display: block;}
	.shopIcon{width: 30rpx; height: 30rpx; display: block;}
	.alldeltBtn{width: 150rpx;height: 50rpx;line-height: 50rpx;border-radius: 30rpx;text-align: center;border:1px solid #FCC401;}
	
	.xqbotomBar{height: 100rpx; z-index: 40;}
</style>
