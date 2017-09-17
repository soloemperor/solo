<template>
	<div class="addbank">
		<h3 class="header"><span class="back" @click="back"></span>添加银行卡</h3>
		<div class="main"></div>
	</div>
</template>

<script>
	export default{
		data(){
			return{
				
			}
		},
		mounted:function(){
			
		},
		methods:{
			back:function(){
				this.$router.push({path:'/mybank'})
			}
		}
	}
</script>

<style scoped>
	.addbank{
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
</style>