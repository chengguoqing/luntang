<template>
	<view class="">
		<view class="bgls   pm20 sjhhsderty">
			<!-- #ifdef H5 || APP-PLUS -->
			<view class="pd mb20">
				<view class="row">
					<view class="col">
						<image src="../../static/img/logo.png" class="logoxerertx cz" mode="widthFix"></image>
						<view class="pr f_b">
							<picker mode="selector" :range="array">
								<image src="../../static/img/baise.png" mode="widthFix" class="xialderert cz"></image>
							</picker>
						</view>
					</view>
					<view class="col tr pt10">
						<image src="../../static/img/ss.png" mode="widthFix" class="souscdrtx cz"></image>
					</view>
				</view>
			</view>
			<!-- #endif -->
			<view class="ssdrt ">
				<view class="fz32 cf dfdsf_drtx" v-for="sd in topxee">
					{{sd.name}}
				</view>
				<view class="qc"></view>
			</view>
		</view>
		<view class="ov w100">
		<view class="pd pt20 pm20">
			<swiper class="jhhxddrrtt" :autoplay="true" :interval="3000" :duration="1000">
				<swiper-item v-for="(sd,idx) in bannere" :key="idx">
					<view class="swiper-item pr">
						<image :src="sd.image"></image>
						<view class="z3 fz26 jjhxddrt pd ">
							<view class="dian">
								<text class="cz">
									{{sd.title}}
								</text>
							</view>
							</text>
						</view>
					</view>
				</swiper-item>
			</swiper>


			<view class="btm pt20 pm 20 mt20 row" v-for="sd in lidata" @tap="hf('/pages/details/index')">
				<view class="col">
					<view class="fz30 z3 diansan dsfdxeer">
						{{sd.title}}
					</view>
					<view class=" z9 fz24">
						{{sd.author}}
						<text class="ml5">{{sd.postdate}}</text>
						<text class="ml5">回复{{sd.replies}}</text>
						<text class="ml5">查看{{sd.hits}}</text>
					</view>
				</view>
				<image :src="sd.image" class="jhjxhxeert ml10" v-if="sd.image"></image>
			</view>
		</view>
		<view class="cen fz26 z9 btm pt20 pm20 cen" v-if="isload">
			<image src="../../static/img/loading.gif" mode="widthFix" class="cz loaddertxe"></image>
			<text class="cz">加载中...</text>
		</view>
		<view class="" v-if="false">
			<view class="pd bgls pt20 pm20 mt20">
				<view class="pr">
					<icon type="search" size="16" class="fasseeet" />
					<input class="xdferttxe" v-model="ssserrt" confirm-type="search" />
				</view>
			</view>
			<view class="mt20 cen fz24 z3">
				1995-2014@百色视窗广告传媒有限公司
			</view>
			<view class="mt20 cen fz24 z3">
				广告合作：18007768899
			</view>
			<view class="mt20 cen fz24 z3">
				招聘发布：18007768882、18007768883
			</view>
			<view class="mt20 cen fz24 z3">
				业务总机：0776-2222228
			</view>
			<view class="mt20 cen fz24 z3">
				爆料及论坛管理：18007768880
			</view>
			<view class="mt20 cen fz24 z3">
				[退出] <text class="ml10">意见反馈</text>
				<text class="ml10">无图版</text>
				<text class="ml10">联系我们</text>
			</view>
		</view>
		<view class="shhsddrfr">
			<view class="dsfdsf_xeert">
				<image class="cz" src="../../static/img/8016_517015730076384e13a476b1bcc11.png" mode="widthFix"></image>
			</view>
			<view class="dsfdsf_xeert ab" v-if="scrollTop>200" @tap="goTop">
				<image class="cz" src="../../static/img/top_01.png" mode="widthFix"></image>
			</view>
		</view>

			
		</view>
	</view>
</template>
<script>
	export default {
		data() {
			return {
				array: ['右江区', '平果', '田东', '田阳', '德保', '靖西', '那坡', '田林', '隆林', '西林', '凌云', '乐业'],
				fenlei: ['八卦', '招聘', '房产', '二手房', '租房', '交易', '交友', '美食', '二手车', '农业', '装修', '风水', '服务', '教育', '信息', '老赖', '贷款',
					'法律', '宝妈', '宠物', '摄影'
				],
				ssserrt: '',
				scrollTop: '',
				topxee: [],
				bannere: '',
				lidata: [],
				isload: false,
				page: 0
			}
		},
		components: {

		},
		methods: {
			goTop: function() {
				uni.pageScrollTo({
					scrollTop: 0
				})
			},
			async getttop() {
				const cahse = {}
				cahse.a = 'wxModular'
				cahse.modname = 'wxnavw'
				cahse.version = 'a32'
				const xerrt = await this.get(cahse)
				this.topxee = xerrt.data
			},
			async getlist(ty) {
				let ssdr = {}
				ssdr.a = 'wxModular'
				ssdr.modname = 'xcxindex'
				ssdr.page = this.page
				ssdr.version = 'a32'
				ssdr.external = 'uni'
				const kjhxee = await this.get(ssdr)
				if (!this.bannere) {
					this.bannere = kjhxee.banner
				}
				if (!ty) {
					kjhxee.data.map(a => {
						this.lidata.push(a)
					})
				} else {
					setTimeout(a => {
						this.isload = false
						kjhxee.data.map(a => {
							this.lidata.push(a)
						})
					}, 1000)
				}


			}
		},
		onPageScroll(e) {
			this.scrollTop = e.scrollTop
		},
		onPullDownRefresh() {
			setTimeout(function() {
				uni.stopPullDownRefresh();
			}, 1000);
		},
		onReachBottom(e) {
			this.isload = true

			this.page++
			this.getlist(true)
		},
		onShareAppMessage: function(res) {
			return {
				title: "獨行工匠",
				path: "/pages/index/index"
			}
		},
		onLoad() {
			this.getttop()
			this.getlist()
		},
		mounted() {

		},
	}
</script>
<style scoped>
	.logoxerertx {
		width: 200upx;
	}

	.xialderert {
		width: 50upx;
	}

	.souscdrtx {
		width: 280upx;
	}

	.dfdsf_drtx {
		width: 20%;
		float: left;
		margin-top: 8upx;
		margin-bottom: 8upx;
		border-right: 1px solid #79BA15;
		text-align: center;
	}

	.dfdsf_drtx:nth-child(5N) {
		border: 0;
	}

	.jhhxddrrtt {
		height: 360upx;
	}

	.swiper-item,
	.swiper-item image {
		width: 100%;
		height: 100%;
	}

	.jjhxddrt {
		position: absolute;
		left: 0;
		bottom: 0;
		width: 100%;
		background: rgba(255, 255, 255, 0.8);
		padding-top: 10upx;
		padding-bottom: 10upx;
	}

	.dsfdxeer {
		height: 120upx;
	}

	.dsfdxeer.ba {
		height: 84upx;
	}

	.jhjxhxeert {
		width: 216upx;
		height: 160upx;
	}

	.xdferttxe {
		width: 100%;
		height: 65upx;
		background: #fff;
		border-radius: 40upx;
		color: #333;
		padding-left: 80upx;
	}

	.fasseeet {
		position: absolute;
		left: 20upx;
		top: 20upx;
	}

	.dsfsdf_dre {
		height: 90upx;
	}

	.sjhhsderty {
		position: sticky;
		left: 0;
		top: 0;
		z-index: 1000;
		/* #ifdef APP-PLUS */
		padding-top: 90upx;
		/* #endif */
	}

	.fgrtxeet {
		height: 170upx;
	}

	.loaddertxe {
		width: 70upx;
	}
</style>
