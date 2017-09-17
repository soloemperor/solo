<template>
	<div class="todaynew">
		<h3 class="header"><span class="back" @click="back"></span>今日要闻</h3>
		<div class="main">
			<div class="main_t" v-for="item in todaynew">
				<h4 class="title">{{item.title}}</h4>
				<p class="newtime">{{item.newtime}}</p>
				<div class="newcontent">{{item.newcontent}}</div>
			</div>
			
		</div>
	</div>
</template>

<script>
	export default{
		data(){
			return{
				todaynew:[
					{title:'中国版原油期货呼之欲出'},
					{newtime:'2017-08-21-09:49'},
					{newcontent:'美国油品数据延续了8月以来的供不应求局面。美国能源信息署最新数据显示，美国上周EIA原油库存减少894.5万桶至4.665亿桶，降幅1.9%，连续7周陆续下滑，语气减少300.29万桶。而且，埃克森美孚位于德克萨斯州的贝城炼油厂的一个部门已被关闭，这是美国第二大炼油厂，日产量达58.4万桶。这座炼油厂的停产可能会缓解市场对供应过剩的担忧。'}
				]
			}
		},
		created:function(){
			
		},
		mounted:function(){
			
		},
		methods:{
			back:function(){
				this.$router.push({path:'/'})
//				console.log(this.$router.params)
			}
		}
	}
</script>

<style scoped>
	.todaynew{
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
	.main .title{
		font-size:0.3rem;
		color:#fd4331;
		margin-top:0.2rem;
	}
	.main .newtime{
		font-size:0.22rem;
		color:#b3b3b3;
		margin-top:0.14rem;
	}
	.main .newcontent{
		font:0.26rem/0.5rem "";
		color:#e6e6e6;
		padding:0 0.5rem;
		text-align: left;
		text-indent: 2em;
	}
</style>