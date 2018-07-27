<template>
  <div class="job">
		<div class="job1"><p>{{msg1}}<br>
			<span class="add">{{add}}</span>
			<span class="goldnum">{{num1}}</span>
			<img src="../assets/gold_03.png"></p>
		</div>
		<div class="job2"><p>{{msg2}}<br>
			<span class="add">{{add}}</span>
			<span class="goldnum">{{num2}}</span>
			<img src="../assets/gold_03.png"></p>
		</div>
  </div>
</template>

<script>
export default {
  name: 'job',
  data () {
    return {
      msg1: '分享下单',
      msg2: '邀请新用户下单',
      num1: '25',
      num2: '1500',
      add: '+ '
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.job{
	margin-left: auto;
	margin-right: auto;
	font-size: 0;
}
.job div {
	display: inline-block;
	width: 49%;
	font-size: .26rem;
	text-align: center;	
	height: 1.56rem;
	margin: .5%;
}
.add{
	font-size: .5rem;
	display: inline-block;
}
.goldnum{
	font-size: .6rem;
	font-family: DIN Condensed;
	display: inline-block;
	vertical-align: middle;
}
.job1{
	background-color: #fef9f8;
}
.job2{
 	background-color: #fffdee;
}
img{
	height: .36rem;
	width: .41rem;
	margin-bottom: -.1rem;
}
</style>