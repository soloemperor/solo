<template>
	<div class="orderdetails">
		<h3 class="header"><span class="back" @click="back"></span>订单详情</h3>
		<div class="main">
			<ul class="identification">
				<li><p class="ordernum p1">业务订单号</p><p class="orderNum p2">PC10031</p></li>
				<li><p class="ordertime p1">下单日期</p><p class="orderTime p2">2017-08-16</p></li>
				<li><p class="orderstate p1">方案状态</p><p class="orderState p2">已生效</p></li>
			</ul>
			<div class="ordercard">
				<h5><span class="s1">方案编码：OP100030</span><span class="s2">权利金：800</span><span class="s3">客户盈利：<span class="s4">1000</span></span></h5>
				<span><p class="p1">股票代码</p><p class="p2">002588</p></span>
				<span><p class="p1">股票名称</p><p class="p2">史丹利</p></span>
				<span><p class="p1">投资金额</p><p class="p2">10000</p></span>
				<span><p class="p1">生效日期</p><p class="p2">002588</p></span>
				<span><p class="p1">到期日期</p><p class="p2">002588</p></span>
				<span><p class="p1">期初价格</p><p class="p2">7.7</p></span>
				<span><p class="p1">期末价格</p><p class="p2">7.68</p></span>
				<span><p class="p1">结算方式</p><p class="p2">市价</p></span>
				<button class="cardbtn" @click="cardbtn" ref="cardbtn">行权</button>
			</div>
			<div class="ordercard">
				<h5><span class="s1">方案编码：OP100030</span><span class="s2">权利金：800</span><span class="s3">客户盈利：<span class="s4">1000</span></span></h5>
				<span><p class="p1">股票代码</p><p class="p2">002588</p></span>
				<span><p class="p1">股票名称</p><p class="p2">史丹利</p></span>
				<span><p class="p1">投资金额</p><p class="p2">10000</p></span>
				<span><p class="p1">生效日期</p><p class="p2">002588</p></span>
				<span><p class="p1">到期日期</p><p class="p2">002588</p></span>
				<span><p class="p1">行权日期</p><p class="p2">2017-08-16</p></span>
				<span><p class="p1">期初价格</p><p class="p2">7.7</p></span>
				<span><p class="p1">期末价格</p><p class="p2">7.68</p></span>
				<span><p class="p1">结算方式</p><p class="p2">市价</p></span>
				<p class="p_show">行权中...</p>
			</div>
		</div>
	</div>
</template>

<script>
	export default{
		data(){
			return{
			}
		},
		created(){
		},
		mounted(){			
		},
		methods:{
			back(){
				this.$router.push({path:'/order'})
			},
			cardbtn(){
				console.log(this.$refs.cardbtn.innerHTML)
				this.$refs.cardbtn.innerHTML = '行权中...'
			}
		}
	}
</script>

<style scoped>
	.orderdetails{
		width:100%;
		height:100%;
		background:#252528;
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
	.main .identification{
		width:100%;
		display: flex;
		flex-wrap: wrap;
		justify-content: space-around;
		border-bottom: 2px solid #2e2e32;
	}
	.main .identification li{
		flex: 1;
		height:1.2rem;
		border-left:1px solid #2e2e32;
		border-right:1px solid #2e2e32;
	}
	.main .identification li .p1{
		font-size:0.26rem;
		color:#e6e6e6;
		margin-top:0.2rem;
	}
	.main .identification li .p2{
		font-size:0.2rem;
		color:#999;
		margin-top:0.1rem;
	}
	.orderdetails .main .identification li .orderState{
		color:#FD4331;
	}
	.orderdetails .main .ordercard{
		width:7.1rem;
		height:4.6rem;
		background:#2e2e32;
		border-top-left-radius: 0.2rem;
		border-top-right-radius: 0.2rem;
		margin:0.2rem auto 0;
		color:#fff;
		display: flex;
		flex-wrap: wrap;
		font-size:0.24rem;	
	}
	.orderdetails .main .ordercard h5{
		width:100%;
		display: flex;
		flex-wrap: nowrap;
		justify-content: space-around;
		text-align: center;
	}
	.orderdetails .main .ordercard h5 span.s1{
		width:35%;
		margin-left:0.1rem;
	}
	.orderdetails .main .ordercard h5 span.s4{
		color:#FD4331;
	}
	.orderdetails .main .ordercard h5 span{
		margin-top:0.3rem;
		border-bottom: 2px solid #39393d;
	}
	.orderdetails .main .ordercard span{
		width:33.3%;
		height:0.85rem;
		text-align: center;
	}
	.orderdetails .main .ordercard span .p2{
		color:#999;
	}
	.orderdetails .main .ordercard .cardbtn{
		width:1.6rem;
		height:0.66rem;
		border:0;
		border-radius: 0.06rem;
		background:#fd4331;
		font-size:0.3rem;
		color:#fff;
		margin:0.3rem 0 0 0.5rem;
		outline: none;
	}
	.orderdetails .main .ordercard .p_show{
		width:100%;
		font-size:0.3rem;
		color:#fd4331;
	}
</style>