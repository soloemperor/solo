<template>
	<div class="stocksearch">
		<h3 class="header"><span class="back" @click="back"></span>股票搜索</h3>
		<div class="main">
			<input type="text" class="search" v-model="searchVal" @input="change"/>
			<ul class="search_main">
				<li v-for="item in test" @click="getstockid(item.stockId)">
					<p><span>{{item.stockName}}</span><span>{{item.stockId}}</span></p><span class="add" @click="add(item.stockId)"></span>
			   </li>
			</ul>
		</div>
	</div>
</template>

<script>
	export default{
		data(){
			return{
				searchVal: '',
				test:[]
			}
		},
		created:function(){
			
		},
		mounted:function(){
		},
		methods:{
			back:function(){
				this.$router.push({path:'/'})
			},
			add:function(stockid){
//				console.log(stockid);
				ajax({
					url:''+host+'/userStock/addUserStock',
					type:"POST",
					data:JSON.stringify({
					    "sessionKey": "15c0c5a35bb6cc672ee29cd4fe363786",
					    "stockId":stockid
					}),
					contentType: "application/json;charset=UTF-8",
					success:function(res){
						console.log(res);
					}
				});
			},
			change () {
				var _this = this.searchVal;
				var that = this;
//				console.log(_this);
				ajax({
					url:''+host+'/stock/searchStock',
					type:"POST",
					data:JSON.stringify({
						'param':_this,
						'currentPage':1,
						'pageSize':10
					}),
					contentType: "application/json;charset=UTF-8",
					success:function(res){
//						console.log(res);
					    that.test = res.resultList;
					}
				});
			},
			getstockid(getId){
				console.log(getId)
			}
		}
	}
</script>

<style scoped>
	.stocksearch{
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
	.main .search{
		width:4.6rem;
		height:0.66rem;
		border:0;
		border:2px solid #fff;
		border-radius: 6px;
		background:#252528 url(../assets/search.png) no-repeat 0.2rem center;
		background-size:0.4rem 0.38rem;
		margin:0.3rem 0;
		font:0.28rem/0.66rem "";
		color:#fff;
		padding-left:0.8rem;
	}
	.search_main{
		width:100%;
	}
	.search_main li{
		height:0.88rem;
		background:#2e2e32;
		margin-bottom:2px;
		text-align: left;
	}
	.search_main li p{
		font:0.26rem/0.88rem "";
		color:#fff;
		margin-left:0.3rem;
		display: inline;
	}
	.search_main li .add{
		width: 0.34rem;
		height:0.34rem;
		background:url(../assets/add.png) no-repeat center center;
		background-size:0.34rem 0.34rem;
		float: right;
		margin:0.3rem 0.3rem 0 0;
	}
</style>