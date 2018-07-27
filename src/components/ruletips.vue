<template>
  <div class="tips" v-show="ishow" @click="tip">
  	<div class="show">
		<div class="signtip">
			<h2>{{signtip}}</h2>
			<ul>
				<li>1.每日签到获得一定的金币，7天为一个签到周期，7天内连续签到获得的金币会相应增加；</li>
				<li>2.断签则从第一天开始重新计算</li>
				<li>3.金币数额达到500个以上，即可以在平台消费抵现。</li>
			</ul>
		</div>
		<div class="jobtip">
			<h2>{{jobtip}}</h2>
			<ul>
				<li>
					<strong>分享下单</strong>
					<p>分享商品给好友，奖励金币数值为好友下单金额的50%，最低25金币起，2000金币封顶(除1分赢、神价爆款、拼团等活动商品)</p>
				</li>
				<li>
					<strong>邀请新用户</strong>
					<p>邀请新用户并成功下单，可得1000金币(除1分赢、神价爆款、拼团等活动商品)</p>
				</li>
			</ul>
		</div>
  	</div>	
  </div>
</template>

<script>
export default {
  name: 'ruletips',
  data () {
    return {
    	signtip: '签到说明',
		jobtip: '任务说明'
    }
  },
  props: ['ishow'],
  methods :{
  	tip:function(){
  		this.$emit("showtip",false)
  	}
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h2{
	font-size: .3rem;
	color: red;
	text-align: center;
}
.tips{
	position: fixed;
	left: 0px;
	top: 0px;
	width: 100%;
	height: 100%;
	background-color: rgba(12,12,12,.65);
	z-index: 1;
}
.show{
	position: absolute;
	left: 0px;
	top: 0px;
	right: 0px;
	bottom: 0px;
	margin:auto;
	background-color: white;
	border-radius: .15rem;
	width: 5.7rem;
	height: 8.6rem;
}
.signtip,.jobtip{
	width: 5rem;
	margin: .6rem auto .5rem auto;
}
.jobtip{
	margin-top: .5rem;
}
ul{
	font-size: .26rem;
	padding: 0px;
}
.signtip li{
	list-style: none;
}
.jobtip strong{
	margin-left: -.2rem;
}
.jobtip p{
	margin: 0px;
}
.jobtip li{
	margin-top: .25rem;
	list-style: square inside;
}
</style>