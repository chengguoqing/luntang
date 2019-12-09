<template>
	<view class="ssdr_dert">

		<view class="qiexertx  w100">
			<scroll-view scroll-x="true" class="dx_jz">
				<view v-for="sd in fenlei" class="qianuaserert">
					{{sd}}
				</view>
			</scroll-view>
			<view class="gjhgheert" @tap="onlsdd">
				<icon type="search" size="20" class="cz"></icon>
			</view>
		</view>
		<view class="pd bgff">
			<view class="fz34 b z3 mt10 titleser">
				bi碧桂园4房2厅2卫2阳台，147平，150万，10240元/平，精装修
			</view>
			<view class="z9 fz28 mt20 row">
				<view class="col dx_jz">
					右论房产中心
					<text class="ml10">2019-12-04 17:24</text>
				</view>
				<view class="col tr">
					阅读8864 回复0
				</view>
			</view>
			<view class="biagexe mt20">
				<view class="duywerow row" v-for="(sd,idx) in biaoge" :key="idx">
					<view class="lablexxe fz32 b">
						{{sd.name}}
					</view>
					<view class="col fz26">
						{{sd.value}}
					</view>
				</view>
			</view>
			<view class="fz30 sdf_deert">
				<view class="mt20  z3">
					房源编号：005561
				</view>
				<view class="z3">
					碧桂园4房2厅2卫2阳台，147平，150万，10204元/平，精装修
				</view>
				<image src="https://duxinggj-2018-1251133427.cos.ap-guangzhou.myqcloud.com/6ac6aed6-4da2-406b-920f-10518b8d0ba5.jpg"
				 class="w100 cz" mode="widthFix"></image>
				<image src="https://duxinggj-2018-1251133427.cos.ap-guangzhou.myqcloud.com/66e1c28e-d4aa-4763-b408-5f82023565b4.jpg"
				 class="w100 cz" mode="widthFix"></image>

			</view>
		</view>
		<view class="mt20 pd bgff pm20">
			<view class="red fz34 cen  pt20">
				[预约看房]
			</view>
			<yuyue></yuyue>
		</view>
		<view class="mt20 bgff pd">
			<view class="pt20 pm20 row" v-for="sd in 2">
				<image src="../../static/img/20191206094913.png" class="yj dertrtxer"></image>
				<view class="col pl20">
					<view class="z9 fz26">
						<view class="">
							才有ng[江边小灰层]
						</view>
						<view class="fz24">
							1楼 2019-07-30 08:54:27
						</view>
					</view>
					<view class="fz30 z3 mt20">
						胜多负少的鼎折覆餗胜多负少的鼎折覆餗胜多负少的鼎折覆餗胜多负少的鼎折覆餗
					</view>
				</view>
			</view>
		</view>
		<view class="mt20 pt20 bgff cen fz28 z3 pm20">
			<view class=" ">
				“关注右江论坛公众号可收到
			</view>
			<view class="">
				本版块最新信息”
			</view>
			<image src="../../static/img/erweima.png" mode="widthFix" class="mt30 dfdsfdeetrt"></image>
			<view class="mt20">
				“将二维码保存到手机，用微信扫一扫关注”
			</view>
		</view>

		<view class="row bhgsdertx bgff btm">
			<view class="col row cen">
				<view class="col" @tap="fengxiang">
					<view class="xddf_dert">
						<image src="../../static/img/fengxiang.png" mode="widthFix" class="cz fengdert"></image>
					</view>
					<view class="fz26 z9">
						分享
					</view>
				</view>
				<view class="col" @tap="hf('/pages/details/message')">
					<view class="xddf_dert">
						<image src="../../static/img/liuyan.png" mode="widthFix" class="cz fengdert ab"></image>
					</view>
					<view class="fz26 z9">
						留言
					</view>
				</view>
				<view class="col" @tap="boda">
					<view class="xddf_dert">
						<image src="../../static/img/phone.png" mode="widthFix" class="cz fengdert"></image>
					</view>
					<view class="fz26 z9">
						电话
					</view>
				</view>
			</view>
			<view class="yuyeertt" @tap="hf('/pages/details/yuyue')">
				预约看房
			</view>
		</view>

	</view>
</template>
<script>
	import yuyue from "../../components/yuyue.vue"
	export default {
		data() {
			return {
				fenlei: ['首页', '八卦', '招聘', '房产', '二手房', '租房', '交易', '交友', '美食', '二手车', '农业', '装修', '风水', '服务', '教育', '信息', '老赖',
					'贷款',
					'法律', '宝妈', '宠物', '摄影'
				],
				biaoge: [{
					name: '户型',
					value: '4房2厅'
				}, {
					name: '城区',
					value: '龙景区'
				}, {
					name: '学区',
					value: '紫薇小学'
				}, {
					name: '小区',
					value: '碧桂园'
				}, {
					name: '装修',
					value: '豪华装修'
				}, {
					name: '楼层',
					value: '低层'
				}, {
					name: '总楼层',
					value: '17层'
				}, {
					name: '朝向',
					value: '南北'
				}, {
					name: '不动产证',
					value: '已办理'
				}, {
					name: '契税',
					value: '已交满5年且唯一住房'
				}, {
					name: '总价',
					value: '150万'
				}, {
					name: '单价',
					value: '10204元/m2'
				}]
			}
		},
		components: {
			yuyue
		},
		onPullDownRefresh() {
			setTimeout(function() {
				uni.stopPullDownRefresh();
			}, 1000);
		},
		methods: {
			ssdfdrtt(e) {
				this.ixer = e.detail.value
			},
			ssdfdrttsan(e) {
				this.ixsan = e.detail.value
			},
			onlsdd() {
				// uni.login({
				// 	provider: 'weixin',
				// 	success: function(loginRes) {
				// 		uni.getUserInfo({
				// 			provider: 'weixin',
				// 			success: function(infoRes) {
				// 				uni.showToast({
				// 					icon: "none",
				// 					title: JSON.stringify(infoRes)
				// 				})
				// 			}
				// 		});
						
				// 	}
				// });
			},
			fengxiang() {
				uni.share({
					provider: "weixin",
					scene: "WXSceneSession",
					type: 0,
					href: "http://uniapp.dcloud.io/",
					title: "uni-app分享",
					summary: "我正在使用HBuilderX开发uni-app，赶紧跟我一起来体验！",
					imageUrl: "https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/uni@2x.png",
					success: function(res) {
						console.log("success:" + JSON.stringify(res));
					},
					fail: function(err) {
						console.log("fail:" + JSON.stringify(err));
					}
				});
			},
			boda() {
				uni.makePhoneCall({
					phoneNumber: '13538190372' //仅为示例
				});
			}
		},
		mounted() {

		}
	}
</script>
<style scoped>
	.qiexertx {
		position: sticky;
		left: 0;
		top: 0;
		/* #ifdef H5 */
		top: 88upx;
		/* #endif */
		z-index: 100;
		background: #fff;
		padding: 15upx 10upx;
		padding-right: 100upx;
	}

	.qianuaserert {
		display: inline-block;
		padding: 15upx 20upx;
		font-size: 30upx;
		color: #333;
		background: #EDEDEB;
		margin-right: 20upx;
	}

	.gjhgheert {
		background: #EDEDEB;
		width: 100upx;
		text-align: center;
		line-height: 1;
		height: 68upx;
		position: absolute;
		right: 0;
		line-height: 68upx;
		top: 15upx;
		z-index: 100;
	}

	.titleser {
		line-height: 1.6;
	}

	.duywerow {
		line-height: 60upx;
		border-bottom: 1px solid #ECECEA;
	}

	.biagexe {
		border: 1px solid #ECECEA;
		border-bottom: 0px;
		background: #F8F8F6;
	}

	.lablexxe {
		width: 200upx;
		padding-left: 10upx;
	}

	.sdf_deert {
		line-height: 1.8;
	}

	.sdfdfsderr {
		width: 50%;
		float: left;
	}

	.dfdsfdeetrt {
		width: 410upx;
	}

	.ssdr_dert {
		padding-bottom: 160upx;
	}

	.bhgsdertx {
		position: fixed;
		left: 0;
		bottom: 0;
		z-index: 100;
		width: 100%;
		height: 100upx;
	}

	.yuyeertt {
		width: 250upx;
		text-align: center;
		height: 100upx;
		line-height: 100upx;
		background: #F95832;
		font-size: 32upx;
		color: #fff;
	}

	.xddf_dert {
		height: 50upx;
		line-height: 50upx;
		margin-bottom: 8upx;
	}

	.fengdert {
		width: 40upx;
	}

	.fengdert.ab {
		width: 50upx;
	}

	.dertrtxer {
		width: 70upx;
		height: 70upx;
	}
</style>
