<template>
	<div class="breakdownassets">
		<h3 class="header"><span class="back" @click="back"></span>资产明细</h3>
		<div class="main">
			<ul class="eachgp">
				<li>
					<div class="li_l">
						<p class="gpcode p1">股票代码：{{gpcode}}</p>
						<p class="gptime p2">{{gptime}}</p>
					</div>
					<div class="li_r" :class="{'green':gpNum < 0}">
						<p class="gpNum">{{gpNum}}</p>
					</div>
				</li>
				<li>
					<div class="li_l">
						<p class="withdrawals p1">提现</p>
						<p class="gptime p2">{{gptime}}</p>
					</div>
					<div class="li_r" :class="{'green':gpNum < 0}">
						<p class="gpNum">{{gpNum}}</p>
					</div>
				</li>
				<li>
					<div class="li_l">
						<p class="top_ups p1">充值</p>
						<p class="gptime p2">{{gptime}}</p>
					</div>
					<div class="li_r" :class="{'green':gpNum < 0}">
						<p class="gpNum">{{gpNum}}</p>
					</div>
				</li>
			</ul>
		</div>
	</div>
</template>

<script>
	export default{
		data(){
			return{
				gpcode:'12546664414',
				gptime:'2017-08-16-15:36',
				gpNum:'+1300.00'
			}
		},
		mounted(){
			
		},
		methods:{
			back(){
				this.$router.push({path:'/myassets'})
			}
		}
	}
</script>

<style scoped>
	.breakdownassets{
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
	.main .eachgp{
		width:100%
	}
	.main .eachgp li{
		height:1rem;
		background:#252528;
		border-bottom: 2px solid #2e2e32;;
		display: flex;
		flex-wrap: nowrap;
		justify-content: space-around;
	}
	.main .eachgp li .li_l{
		width:70%;
		text-align: left;
	}
	.main .eachgp li .li_l p{
		margin-left:0.3rem;
	}
	.main .eachgp li .li_l .p1{
		font-size:0.26rem;
		color:#e6e6e6;
		margin-top:0.2rem;
	}
	.main .eachgp li .li_l .p2{
		font-size:0.2rem;
		color:#999;
	}
    .eachgp li .li_r{
		width:30%;
		font-size: 0.3rem;
		color:#D52424;
	}
	.eachgp li .gpNum{
		text-align: right;
		margin:0.3rem 0.3rem 0 0;
	}
	.breakdownassets .main .eachgp li .green{
		width:30%;
		font-size: 0.3rem;
		color: #090;
	}
</style>