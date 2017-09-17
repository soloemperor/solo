<template>
	<div class="myphone">
		<h3 class="header"><span class="back" @click="back"></span>绑定手机号</h3>
		<div class="main">
			<ul class="binding">
				<li class="phonenum">
					<input type="text" name="" class="valNum" placeholder="请输入手机号" v-model="valNum"/>
					<button class="getcode" @click="getcode(valNum)">获取验证码</button>
				</li>
				<li class="phonecode">
					<input type="text" name="" class="codeNum" placeholder="请输入验证码"/>
				</li>
			</ul>
			<button class="determine">确定</button>
		</div>
	</div>
</template>

<script>
	export default{
		data(){
			return{
				valNum:''
			}
		},
		mounted(){
			
		},
		methods:{
			back(){
				this.$router.push({path:'/mycenter'})
			},
			getcode(valNum){
				console.log(valNum);
			}
		}
	}
</script>

<style scoped>
	.myphone{
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
    .main .binding{
		width:100%;
		margin:0.1rem 0 1.2rem;
	}
	.main .binding li{
		height:0.88rem;
		background:#2e2e32;
		margin-bottom: 2px;
		text-align: left;
	}
	.main .binding li .valNum{
		height:0.88rem;
		background:#2e2e32;
		padding-left:0.3rem;
		font-size:0.26rem;
		color:#999;
	}
	.main .binding li .getcode{
		width:1.8rem;
		height:0.6rem;
		border:0;
		outline: none;
		border-radius: 0.06rem;
		background:#fd4331;
		font-size:0.28rem;
		color:#fff;
		float: right;
		margin:0.15rem 0.3rem 0 0;
	}
	.main .binding li .codeNum{
		width:100%;
		height:100%;
		background:#2e2e32;
		padding-left:0.3rem;
		font-size:0.26rem;
		color:#999;
	}
	.main .determine{
		width:5.4rem;
		height:0.88rem;
		font-size:0.3rem;
		color:#fff;
		background:#fd4331;
		border:0;
		border-radius: 0.06rem;
	}
</style>