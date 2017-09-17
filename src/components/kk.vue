<template>
	<div class="kk">
		<h3 class="header"><span class="back" @click="back"></span>{{stockName}}</h3>
		<div class="main">
			<h5 class="enkim">权利金费率：1.03%</h5>
			<div class="details">
				<div class="details_l">
					<p :class="{'red':differ > 0}">{{stockNow}}</p>
					<span :class="{'red':differ > 0}">{{differ}}</span>&nbsp;
					<span :class="{'red':differ > 0}">{{differRange}}</span>
				</div>
				<div class="details_r">
					<p>&nbsp;高&nbsp;
						<span :class="{'red':differ > 0}">{{height}}</span>&nbsp;开&nbsp;
						<span :class="{'red':differ > 0}">{{open}}</span>&nbsp;换手&nbsp;
						<span class="s1">0.75%</span>
					</p>
					<p>&nbsp;低&nbsp;
						<span :class="{'red':differ > 0}">{{low}}</span>&nbsp;额&nbsp;
						<span class="s2">{{amount}}</span>&nbsp;量比&nbsp;
						<span :class="{'red':differ > 0}">{{quantity}}</span>
					</p>
				</div>
			</div>
			<!--<div ref="line" style="height: 400px;"></div>-->
		</div>
		<div class="footerbtn">
			<div><button class="purchase">买入</button></div>
			<div><button class="addoptional" ref="addoptional" @click="addoptional">加入自选</button></div>
			<div><button class="guadan">挂单</button></div>
		</div>
	</div>
</template>

<script>
// 引入 ECharts 主模块
import echarts from 'echarts/lib/echarts'
// 引入柱状图
import 'echarts/lib/chart/bar'
// 引入提示框和标题组件
import 'echarts/lib/component/tooltip'
import 'echarts/lib/component/title'
	export default {
		data() {
			return {
				stockName:'',
				stockNow:'',
				differ:'',
				differRange:'',
				height:'',
				open:'',
				low:'',
				amount:'',
				quantity:''
			}
		},
		mounted() {
//			this.inItEChart()
			const that = this
			ajax({
				url:''+host+'/stock/detail',
				type:'POST',
				data:JSON.stringify({
				    "stockId" : "000001"
				}),
				success:function(res){
					console.log(res)
					console.log(res.flag);
					if(res.flag == false){
						that.$refs.addoptional.style.display = "block"
					}
					that.stockName = res.stock.stockName
					that.stockNow = res.stock.now
					that.differ = res.stock.differ
					that.differRange = res.stock.differRange
					that.height = res.stockDetail.height
					that.open = res.stockDetail.open
					that.low = res.stockDetail.low
					that.amount = res.stockDetail.amount
					that.quantity = res.stockDetail.quantity
				}
			})
		},
		methods:{
//			inItEChart () {
//				let data = [10, 20, 36, 10, 10, 20]
//				this.option.series[0].data = data
//				let myChart = echarts.init(this.$refs.line);
//				myChart.setOption(this.option)
//			},
			back(){
				this.$router.push({path:'/market'})
			},
			addoptional:function(stockid){
//				console.log(stockid);
				var that = this
				ajax({
					url:''+host+'/userStock/addUserStock',
					type:"POST",
					data:JSON.stringify({
					    "sessionKey": "15c0c5a35bb6cc672ee29cd4fe363786",
					    "stockId":"000001"
					}),
					contentType: "application/json;charset=UTF-8",
					success:function(res){
						console.log(res);
						that.$refs.addoptional.style.display = "none"						
					}
				});
			}
		}
		
	}
</script>

<style scoped>
	.kk{
		width:100%;
		height:100%;
		background:#252528;
		position: relative;
	}
	.header{
		width:100%;
		height:0.87rem;
		background:#1b1b20;
		font:0.35rem/0.87rem "";
		color:#fff;
		position: relative;
	}
	.header .back{
		width:0.22rem;
		height:0.37rem;
		background:url(../assets/left.png) no-repeat left center;
		background-size:0.22rem 0.37rem;
		position: absolute;
		top:0.26rem;
		left:0.38rem;
	}
	.main{
		width:100%;
		height:100%;
		background:#252528;
	}
	.main .enkim{
		height:0.77rem;
		font:0.28rem/0.77rem "";
		color:#fff;
		text-align: left;
		margin-left:0.3rem;
	}
	.main .details{
		width:100%;
		height:1rem;
		background: #1b1b20;
		display: flex;
		flex-wrap: nowrap;
		justify-content: space-around;
	}
	.kk .main .details .red{
		color:#FD4331;
	}
	/*.kk .main .details .red span{
		color:#FD4331;
	}*/
	.main .details .details_l{
		width:35%;
	}
	.main .details .details_l p{
		font:600 0.34rem ""; 
		color:#090;
		margin-top:0.1rem;
	}
	.main .details span{
		font-size:0.2rem;
		color:#090;
	}
	.main .details .details_r{
		width:65%;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
	}
	.main .details .details_r p{
		font:0.26rem/0.5rem "";
		color:#999;
		text-align: left;
	}
	.main .details .details_r .s1{
		color:#999;
	}
	.main .details .details_r .s2{
		color:#999;
	}
	.kk .footerbtn{
		width:100%;
		height:1.2rem;
		position: fixed;
		bottom:0;
		left:0;
		display: flex;
		flex-wrap: nowrap;
		justify-content: space-around;
	}
	.kk .footerbtn div{
		flex: 1;
	}
	.kk .footerbtn button{
		width:1.8rem;
		height:0.66rem;
		font-size:0.34rem;
		color:#fff;
		margin:0 auto;
		outline: none;
		border:0;
		border-radius: 0.06rem;
	}
	.kk .footerbtn .purchase{
		background:#e93030;
	}
	.kk .footerbtn .addoptional{
		background:#4691ee;
		display: none;
	}
	.kk .footerbtn .guadan{
		background:#646464;
	}
</style>