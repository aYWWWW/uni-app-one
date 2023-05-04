<template>
	<view class="content">

		<view class="text-area">

			<view class="top1">{{title}}
				<uni-icons type="bottom" size="30" name="ayu"></uni-icons>
				<uni-section title="自定义样式" subTitle="使用 bgColor 属性自定义背景色" type="line">
					<uni-search-bar placeholder="自定义背景色" bgColor="#EEEEEE" @confirm="search" />
				</uni-section>
			</view>

		</view>
		<view class="nav">
			<u-swiper :list="list1" indicator indicatorMode="line" circular previousMargin="20" nextMargin="20" circular
				:autoplay="false" radius="5" height="280"></u-swiper>
		</view>
		<view class="software">
			<view class="inside">


				<view class="zp1" v-for="item,id in aab" :key="item.id">

					<image :src="item.zp" class="zp2">{{item.aname}}</image>
				</view>

			</view>
			<view class="bottom">
				<view class="zp4" v-for="item,id in bbb" :key="item.id">

					<image :src="item.im" class="zp3"><br>{{item.bname}}</image>
				</view>
			</view>
			<view class="bottoma">
				<view class="db" v-for="item,id in ccc" :key="item.id">

					<image :src="item.om" class="zp7"><br>{{item.cname}}</image>
				</view>
			</view>
			<view class="kb"></view>
		</view>

		<view class="fd">
			<u-subsection :list="list" :current="num" @change="sectionChange"></u-subsection>
			<view class="listitem">
				<view class="itemchilda" v-show="num==0" v-for="item in 5" :key="item.id">
					<br>
					<view class="tb" v-for="item,id in list2" :key="item.id">
						<h4>{{item.title}}</h4>
					</view>

					<u-button type="primary" shape="circle" text="帮TA回答 " size=mini class="an">帮TA回答</u-button>

					<image src="../../static/img/zha.png" class="zh1">流浪猫</image>

					<p class="nr">　爆料人当即跟经纪人反馈病情，经纪人拒绝和品牌方客户反映真实情况，执意要我第二天20日一早出席现场，说不去就不结工资，。</p>
					<view class="zt">
						2346 赞同 1234 浏览 <span class="sj">一小时前</span>

					</view>

				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {

		data() {
			return {
				list: ['最新问题', '提出问题', '待回答问题'],
				// 或者如下，也可以配置keyName参数修改对象键名
				// list: [{name: '未付款'}, {name: '待评价'}, {name: '已付款'}],
				current: 0,
				num: 0,
				title: '济南',
				list1: [
					'https://cdn.uviewui.com/uview/swiper/swiper1.png',
					'https://cdn.uviewui.com/uview/swiper/swiper2.png',
					'https://cdn.uviewui.com/uview/swiper/swiper3.png',
				],
				aab: [{
						id: 1,
						aname: "机票",
						zp: "../../static/img/fj.png",
					},
					{
						id: 2,
						aname: "火车票",
						zp: "../../static/img/hc.png",
					},
					{
						id: 3,
						aname: "酒店",
						zp: "../../static/img/jd.png",
					},
					{
						id: 4,
						aname: "景区门票",
						zp: "../../static/img/djq.png",
					}
				],
				bbb: [{
						id: 1,
						bname: "出国签证",
						im: "../../static/img1/qz.png",
					},
					{
						id: 2,
						bname: "旅行保险",
						im: "../../static/img1/bx.png",
					},
					{
						id: 3,
						bname: "翻译助手",
						im: "../../static/img1/fy.png",
					},
					{
						id: 4,
						bname: "学生专区",
						im: "../../static/img1/xs.png",
					},
				],

				ccc: [{
						id: 1,
						cname: "租车服务",
						om: "../../static/img2/zc.png",
					},
					{
						id: 2,
						cname: "国际导航",
						om: "../../static/img2/dh.png",
					},
					{
						id: 3,
						cname: "境外上网",
						om: "../../static/img2/sw.png",

					}, {
						id: 4,
						cname: "更多",
						om: "../../static/img2/gd.png",
					}
				],
				list2: [{
					id: 1,
					title: "从济南到浦东机场，需要核酸检测报告吗 ？",

				}],
			

			}
		},
		onLoad() {

		},
		onShareAppMessage(res) {
			if (res.from === 'menu') { // 来自页面内分享按钮
				  return {
				      title: '首页',
				      path: '/pages/index/index'
				    }
			}
		},
		methods: {


		
			input(res) {
				console.log('----input:', res)
			},
			clear(res) {
				uni.showToast({
					title: 'clear事件，清除值为：' + res.value,
					icon: 'none'
				})
			},
			blur(res) {
				uni.showToast({
					title: 'blur事件，输入值为：' + res.value,
					icon: 'none'
				})
			},
			focus(e) {
				uni.showToast({
					title: 'focus事件，输出值为：' + e.value,
					icon: 'none'
				})
			},
			cancel(res) {
				uni.showToast({
					title: '点击取消，输入值为：' + res.value,
					icon: 'none'
				})
			},
			onBackPress() {
				// #ifdef APP-PLUS
				plus.key.hideSoftKeybord();
				// #endif
			},

			sectionChange(res) {
				// console.log(res);
				this.num = res
			}

		},
	}
</script>

<style scoped lang="scss">
	.content {
		width: 100%;
		height: 100%;
		/* background-color: blue; */
	}

	.logo {
		width: 200rpx;
		height: 200rpx;
	}

	.text-area {
		width: 100%;
		heigh: 800rpx
	}

	.top1 {
		display: flex;
		align-items: center;
		width: 100%;
		height: 150rpx;
		background-color: aqua;
		padding: 0 10px;
	}

	.nav {
		width: 100%;
		height: 300rpx;
		padding: 10px;
		box-sizing: border-box;
	}

	.software {
		padding: 10px 5px;
		width: 100%;
		height: 500rpx;
		// display: flex;

		// background-color: blue;
	}

	.inside {
		width: 100%;
		height: 90px;
		display: flex;
		justify-content: space-around;
		padding: 10rpx 10rpx;
		box-sizing: border-box;
		// background-color: red;
		font-size: 18rpx;
		text-align: center;
	}

	.hc {
		width: 120rpx;
		height: 120rpx;
	}

	.zp1 {
		padding: 10rpx 10rpx;
		width: 110rpx;
		height: 100rpx;
		// background-color: pink;
	}

	.zp2 {
		width: 100rpx;
		height: 100rpx;
		// background-color: pink;
	}


	.bottom {

		width: 100%;
		height: 60px;
		display: flex;
		justify-content: space-around;
		padding: 10rpx 30rpx;
		box-sizing: border-box;
		// display: inline-block;
		font-size: 10rpx;
		text-align: center;
	}

	.zp3 {
		width: 60rpx;
		height: 60rpx;
		background-color: yellow;
	}

	.zp4 {
		width: 100rpx;
		height: 100rpx;
	}

	.bottoma {
		width: 100%;
		height: 70px;
		display: flex;
		justify-content: space-around;
		padding: 10rpx 30rpx;
		margin-right: 50px;
		box-sizing: border-box;
		font-size: 10rpx;
		text-align: center;
	}

	.zp7 {
		width: 60rpx;
		height: 60rpx;
		background-color: yellow;
	}

	.kb {
		width: 100%;
		height: 25rpx;
		border-radius: 8rpx;
		background-color: #DDDDDD;
	}

	.listitem {
		padding: 10rpx 20rpx;
		width: 100%;
		height: 200px;
		// background-color: aqua;


	}

	.itemchilda {
		color: black;
	}

	.an {
		width: 80px;
		height: 20px;
		border-radius: 8rpx;
		margin-right: 140rpx;
		margin-top: 20px;
		color: black;
		font-weight: 800;
		background-color: #FFE049;
	}

	.nr {
		font-size: 26rpx;
		margin-top: 10px;
	}

	.zh1 {
		width: 70rpx;
		height: 60rpx;
		// background-color: blue;
		// color: blue;
		margin-top: -20rpx;
		margin-bottom: -5px;
	}

	.sj {
		width: 100%;
		height: 100px;
		text-align: right;
		float: right;
		font-size: 10rpx;
		padding: 10rpx 30rpx;
	}

	.zt {
		color: blue;
	}
</style>