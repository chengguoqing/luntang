<template>
	<view>
		<view class="red fz34 cen  pt20">
			[{{subject}}]
		</view>
		<view class="mt20 pt20">
			<view class="" v-for="sd in useer">
				<view class="pt20 pm20 btm pr row" v-if="sd.type == 'textarea'">
					<label class="fz30 z3 lanhgsdert">
						<text class="red fz28">*</text>
						{{sd.label}}：
					</label>
					<view class="col">
						 <textarea class="fz30 w100" :placeholder="sd.placeholder"/>
					</view>
				</view>
				<view class="pt20 pm20 btm pr row" v-if="sd.type == 'text'">
					<label class="fz30 z3 lanhgsdert">
						<text class="red fz28">*</text>
						{{sd.label}}：
					</label>
					<view class="col">
						<input type="text" value="" :placeholder="sd.placeholder" class="fz30" />
					</view>
				</view>
				<view class="btm pm20" v-if="sd.type == 'checkbox-pay'">
					<view class="sdfdfsderr mt20 ab" v-for="sf in sd.xzssd" >
						<label>
							<checkbox /><text class="fz28">{{sf.name}}</text>
						</label>
					
					</view>
					
					<view class="qc">
						
					</view>
				</view>
				<view class="pt20 pm20 btm pr row" v-if="sd.type == 'select-pay-num'||sd.type == 'select'">
					<label class="fz30 z3 lanhgsdert">
						<text class="red fz28">*</text>
						{{sd.label}}：
					</label>
					<view class="col">
						<picker mode="selector" :range="sd.xzssd" >
							<view class="fz30 z3">{{sd.xzssd[sd.xiabia]}}</view>
						</picker>
					</view>
					<image src="../../static/img/right.png" class="rightxeert" mode="widthFix"></image>
				</view>
			</view>
		</view>
		<view class="btm pt40">
			<view class="sdfdfsderr pr10">
				<button class="fz30">重置</button>
			</view>
			<view class="sdfdfsderr pl10">
				<button type="primary" class="fz30">提交</button>
			</view>
			<view class="qc"></view>
		</view>
	</view>
</template>
<script>
	export default {
		props: ['tid'],
		data() {
			return {
				useer:[],
				subject:'',
				ixer: 0,
				ixsan: 0,
				rangeseer: [
					'请选择', '可一次性付款', '我最多首付5万', '最多8万', '最多12万', '最多15万', '40万以上'
				],
				rangesesan: [
					'请选择', '最多1000', '1500', '2000', '3000', '3500', '4500', '4500以上', '我不用贷款'
				]
			}
		},
		components: {},
		methods: {
			ssdfdrtt(e) {
				this.ixer = e.detail.value
			},
			ssdfdrttsan(e) {
				this.ixsan = e.detail.value
			},
			async getformsd (){
				const cahse = {}
				cahse.a = 'readput'
				cahse.tid = this.tid
				let sderrt = await this.get(cahse,'comaction.php')
				this.subject = sderrt.subject
				sderrt.inputa.map(a=>{
					if(a.value){
						a.xzssd = []
						let sdeer = a.value.split(",")
						sdeer.map(b=>{
							if(a.type =="checkbox-pay"){
								let xddrt = {}
								xddrt.name = b
								xddrt.value = ''
								a.xzssd.push(xddrt)
							}
							if(a.type =="select-pay-num" || a.type =="select"){
								a.xzssd.push(b)
							}
						})
						if(a.type =="select-pay-num" || a.type =="select"){
							a.xiabia = 0
						}
					}
				})
				this.useer= sderrt.inputa
				this.$emit('gettitle',this.subject)
			}
		},
		mounted() {
			this.getformsd()
		}
	}
</script>
<style scoped>
	.sdfdfsderr.ab{
		width: 100% !important;
	}
</style>
