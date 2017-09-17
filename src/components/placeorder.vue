<template>
	<div id="placeorder">
		<h3 class="header"><span class="back" @click="back"></span>下单</h3>
		<Form ref="form" :model="orders" class="formAll">
			<FormItem class="label" label="股票名称或代码：" prop="a" :rules="[
              { required: true, message: '股票名称或代码不能为空', trigger: 'change' }
            ]">
	            <Input class="form_inp" v-model="orders.a" placeholder=""></Input>
	        </FormItem>
	        
	        <FormItem class="label" label="买入手数：" prop="b" :rules="[
              { required: true, message: '买入手数不能为空', trigger: 'change' }
            ]">
	            <Input class="form_inp" v-model="orders.b" placeholder=""></Input>
	        </FormItem>
	        
	        <FormItem class="label">
                <FormItem prop="date" label="行权时间：" class="form_inp" :rules="[
              { required: true,type: 'date', message: '行权时间不能为空', trigger: 'change' }
            ]"> 
                    <DatePicker type="date" placeholder="" v-model="orders.date"></DatePicker>
                </FormItem>
	        </FormItem>
	        
	        <FormItem class="label" label="权利金费率：" prop="c" :rules="[
              { required: true, message: '权利金费率不能为空', trigger: 'change' }
            ]">
	            <Input class="form_inp" v-model="orders.c" placeholder=""></Input>
	            <p class="quanlijin">权利金费率*加权倍数=实际权利金费率</p>
	        </FormItem> 
	        
	        <FormItem class="label" label="下单方式：" prop="d" :rules="[
               { required: true, message: '请选择城市', trigger: 'change' }
            ]">
	             <Select v-model="orders.d" placeholder="请选择" class="form_inp">
			        <Option v-for="item in cityList" :value="item.value" :key="item.value">{{ item.label }}</Option>
			    </Select>
	        </FormItem>
	        
	        <FormItem class="label" label="下单价格：" prop="e" :rules="[
              { required: true, message: '下单价格不能为空', trigger: 'change' }
            ]">
	            <Input class="form_inp placeorderpay" v-model="orders.e" placeholder=""></Input>
	        </FormItem>
	        
	        <FormItem class="label" label="加权：" prop="f" :rules="[
              { required: true, message: '请输入至少为1的整数', trigger: 'blur' }]">
	             <!--<Select v-model="orders.f" placeholder="请输入至少为1的整数" class="form_inp">
			        <Option v-for="(item, index) in cityList" :value="item.value" :key="item.index">
			        	{{ item.label }}
			        </Option>
			    </Select>-->
			    <Input class="form_inp" v-model="orders.f" placeholder="" ></Input>
	        </FormItem> 
	        
	        <!--<FormItem class="label" label="备注：" prop="f">
	          <Input class="form_inp textarea" v-model="orders.f" type="textarea" placeholder=""></Input>
	        </FormItem>-->
	   </Form>
	   <div class="Kim">
	   		<p class="inKim">投资金额：<span>{{inKim}}</span>元</p><p class="enKim">权利金：<span>{{enKim}}</span>元</p>
	   </div>
       <Button type="success" @click="handleSubmit" class="success">确认</Button>
	</div>
</template>

<script>
    export default {
        data () {
            return {
                orders: {
                },
                cityList: [
                	{label: '加权1', value: '1'},
                	{label: '加权2', value: '2'},
                	{label: '加权3', value: '3'},
                	{label: '加权4', value: '4'}
                ],
                enKim:'2714',
                inKim:'2714'
            }
        },
        methods: {
        	back:function(){
				this.$router.push({path:'/'})
			},
            handleSubmit () {
            	console.log(this.$refs.form)
                this.$refs.form.validate((valid) => {
                    if (valid) {               	
                    	console.log(this.orders)
                    	let val = Number(this.orders.f)
                    	console.log(val)
                    	if (val <1 || val % 1 !== 0 ) {
                    		this.$Message.error('加权至少为1的整数');
                    		return false
                    	}
                    	console.log(this.orders)
                    	
                        this.$Message.success('提交成功!');
                    } else {
                        this.$Message.error('表单验证失败!');
                    }
                })
            },
            handleReset () {
//              this.$refs.form.resetFields()
                console.log(111)
				this.orders = {}
            }
        }
    }
</script>

<style scoped>
	
</style>
<style>
	#placeorder{
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
	#placeorder .formAll{
		margin-top:0.4rem;
	}
	#placeorder .formAll .label{
		height:0.66rem;
	}
	#placeorder .formAll .label .textarea{
		width:6.3rem;
		height:1.8rem;
		margin-left:0.3rem;
		display: block;
		font-size:0.24rem;
		color:#666;
	}
	#placeorder .ivu-form{
		text-align: left;
	}
	.ivu-form-item .ivu-form-item .ivu-form-item-content{
		width:0;
	}
	.ivu-form-item .ivu-form-item .ivu-form-item-content .ivu-date-picker{
		width:3.6rem;
	}
	#placeorder .ivu-form .ivu-form-item-label{
		text-align: left;
		font-size:0.28rem;
		color:#fff;
		width:2.7rem;
		margin-left:0.3rem;
	}
	#placeorder .ivu-form-item-error-tip{
		width:2.7rem;
		margin-left:0.3rem;
		padding-top:0;
	}
	#placeorder .form_inp{
		width:3.6rem;
		height:0.66rem;
		font-size:0.24rem;
		color:#666;
	}
	#placeorder .placeorderpay .ivu-input{
		color:#fd4331;
	}
	#placeorder .ivu-input{
		background:#252528;
		border:2px solid #fff;
		font-size:0.24rem;
		color:#666;
	}
	#placeorder .ivu-select-single .ivu-select-selection{
		background:#252528;
		border:2px solid #fff;
	}
	#placeorder .ivu-icon-ios-calendar-outline:before {
		/*background: red;*/
	}
	#placeorder .Kim{
		height:0.88rem;
		display: flex;
		flex-wrap: nowrap;
		justify-content:space-between;
	}
	#placeorder .inKim,.enKim{
		font-size:0.28rem;
		color:#fff;
		text-align: left;
	}
	#placeorder .inKim{
		margin-left:0.3rem;
	}
	#placeorder .enKim{
		margin-right:0.3rem;
	}
	#placeorder .inKim span,.enKim span{
		color:#fd4331;
	}
	#placeorder .success{
		width:4.5rem;
		height:0.88rem;
		font-size:0.3rem;
		color:#fff;
		background:#fd4331;
		border:0;
		margin-top:0.7rem;
	}
	#placeorder .formAll .label .quanlijin{
		height:0.3rem;
		font-size:0.22rem;
		color:#bbbec4;
	}
</style>