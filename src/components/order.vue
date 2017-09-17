<template>
	<div class="order">
		<h3 class="header">订单</h3>
		<div class="operation">
			<h4 class="all">全部<img src="../assets/down.png" alt="" /></h4>
			<h4 class="sort">排序<img src="../assets/sort.png" alt="" /></h4>
		</div>
		<ul class="main">
			<li>
				<div class="li_l"><p class="ordernum">订单号：{{ordernum}}</p><p class="needpay">需支付：<span>{{needpay}}</span>元</p></div>
				<div class="li_m"><p class="paoDate">下单日期：<span>{{paoDate}}</span></p><p class="eifDate">生效日期：<span>{{eifDate}}</span></p><p class="exerciseDate">行权日期：<span>{{exerciseDate}}</span></p></div>
				<div class="li_r"><p class="state" @click="orderdetails">已挂单</p></div>
			</li>
			<li>
				<div class="li_l"><p class="ordernum">订单号：{{ordernum}}</p><p class="needpay">需支付：<span>{{needpay}}</span>元</p></div>
				<div class="li_m"><p class="paoDate">下单日期：<span>{{paoDate}}</span></p><p class="eifDate">生效日期：<span>{{eifDate}}</span></p><p class="exerciseDate">行权日期：<span>{{exerciseDate}}</span></p></div>
				<div class="li_r"><p class="state" @click="orderdetails">已完成</p></div>
			</li>
			<li>
				<div class="li_l"><p class="ordernum">订单号：{{ordernum}}</p><p class="needpay">需支付：<span>{{needpay}}</span>元</p></div>
				<div class="li_m"><p class="paoDate">下单日期：<span>{{paoDate}}</span></p><p class="eifDate">生效日期：<span>{{eifDate}}</span></p><p class="exerciseDate">行权日期：<span>{{exerciseDate}}</span></p></div>
				<div class="li_r"><p class="state" @click="orderdetails">已生效</p></div>
			</li>
			<li>
				<div class="li_l"><p class="ordernum">订单号：{{ordernum}}</p><p class="needpay">需支付：<span>{{needpay}}</span>元</p></div>
				<div class="li_m"><p class="paoDate">下单日期：<span>{{paoDate}}</span></p><p class="eifDate">生效日期：<span>{{eifDate}}</span></p><p class="exerciseDate">行权日期：<span>{{exerciseDate}}</span></p></div>
				<div class="li_r"><p class="state" @click="orderdetails">挂单失败</p></div>
			</li>
		</ul>
		<v-footer></v-footer>
	</div>
</template>

<script>
	import vFooter from '@/components/footer_or'
	export default{
		data(){
			return{
				ordernum:'PC10340',
				needpay:'274',
				paoDate:'2017-08-16',
				eifDate:'2017-08-16',
				exerciseDate:'2017-08-16'
			}
		},
		components:{
			vFooter
		},
		created:function(){
			
		},
		mounted:function(){
			
		},
		methods:{
			orderdetails(){
				this.$router.push({path:'/orderdetails'})
			}
		}
	}
</script>

<style scoped>
	.order{
		width:100%;
		height:100%;
		background:#252528;
	}
	.header{
		width:100%;
		height:0.87rem;
		background:#1b1b20;
		font:0.38rem/0.87rem "";
		color:#fff;
		position: relative;
	}
	.operation{
		width: 100%;
		height:0.88rem;
		display: flex;
		flex-wrap: nowrap;
		justify-content:space-between;
		border-bottom: 2px solid #252528;
	}
	.operation h4{
		font:0.28rem/0.88rem "";
		color:#fff;
	}
	.operation .all{
		margin-left:0.3rem;
	}
	.operation .sort{
		margin-right:0.3rem;
	}
	.operation .all img{
		width:0.2rem;
		height:0.12rem;
		margin-left:0.12rem;
	}
	.operation .sort img{
		width:0.18rem;
		height:0.22rem;
		margin-left:0.12rem;
	}
	.main{
		width:100%;
		background:#1b1b20;
	}
	.main li{
		height:1.6rem;
		border-bottom: 2px solid #252528;
		display: flex;
		flex-wrap: nowrap;
		justify-content: space-around;
	}
	.main li div.li_l{
		width:38%
	}
	.main li div.li_m{
		width:37%;
		display: flex;
		flex-direction: column;
		justify-content: space-around;
	}
	.main li div.li_r{
		width:25%;
		position: relative;
	}
	.main li div p.ordernum{
		font-size:0.26rem;
		color:#e6e6e6;
		text-align: left;
		margin:0.4rem 0 0 0.3rem;
	}
	.main li div p.needpay{
		font-size:0.24rem;
		color:#e6e6e6;
		text-align: left;
		margin:0.2rem 0 0 0.3rem;
	}
	.main li div p.needpay span{
		font-size: 0.3rem;
		color:#fd4330;
	}
	.main li div.li_m p{
		font-size:0.24rem;
		color:#e6e6e6;
	}
	.main li div.li_m p span{
		font-size: 0.22rem;
		color:#b3b3b3;
	}
	.main li div.li_r p{
		width:1.2rem;
		height:0.54rem;
		border:1px solid #fd4331;
		border-radius: 6px;
		font-size:0.28rem;
		color:#fd4331;
		line-height: 0.5rem;
		text-align: center;
		position: absolute;
		top:0;
		left:0;
		right:0;
		bottom:0;
		margin: auto;
	}
</style>