<template>
	<view>
		<view class="center myHead flexColumn whiteBj">
			<view class="mny ftw">20.0</view>
			<view class="flex fs13 mgt10"><image style="width: 28rpx; height: 30rpx;margin-right: 10rpx;" src="../../static/images/top-upl-icon.png" mode=""></image>余额(元)</view>
		</view>
		<view class="f5H10"></view>
		
		<view class="pdlr4 whiteBj">
			<view class="fs14 ftw pdt15">充值金额</view>
			<view class="input-money pdtb10"><input type="number" value="100" placeholder="请输入金额" /></view>
			
			<view class="specsList flexRowBetween center fs16 color6 pdt15 ftw" >
				<view class="item" :class="curr==index?'on':''" @click="changeCurr(index)" v-for="(item,index) in specsList" :key="index">{{item}}</view>
			</view>
		</view>
		
		<view class="submitbtn" style="margin-top: 160rpx;">
			<button class="btn" type="button">立即充值</button>
		</view>
		
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
				specsList:['100元','200元','500元','800元','1000元','其他金额'],
				curr:0,
			}
		},
		
		onLoad(options) {
			const self = this;
			// self.$Utils.loadAll(['getMainData'], self);
		},
		methods: {
			changeCurr(index){
				const self = this;
				self.curr = index;
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
	/* @import "../../assets/style/xieyiAlert.css"; */
page{padding-bottom: 60rpx;}	

.myHead{height: 300rpx;}
.myHead .mny{padding-top: 80rpx;font-size: 72rpx;line-height: 72rpx;}
.myRowBetween .item{padding: 20rpx 4%; border-bottom: 1px solid #eee;}

.input-money input{width: 30%;font-size: 30rpx;font-weight: bold;color: #FF2121; height: 60rpx;line-height: 60rpx;border-bottom: 1px solid #f6af15; display: block;}

.specsList{flex-wrap: wrap;}
.specsList .item{width: 210rpx;height: 100rpx; line-height: 100rpx;background: #f1f1f1;border-radius: 10rpx; margin-bottom: 30rpx;}
.specsList .item.on{color: #fff; background: #FCC401;}
.specsList .item:last-child{font-weight: normal;}


</style>

