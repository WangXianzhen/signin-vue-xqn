<template>
  <div class="signdate">
  	
  	<ul class="gold">
		<li v-bind:class="{done: day.signed}"
			v-for="day in signdata"
			:key="day.serial"
			>+{{day.coin}}<img v-show="day.signed" src="../assets/gou_03.png"></li>
  	</ul>

  	<ul class="day">
		<li>第一天</li><li>第二天</li><li>第三天</li><li>第四天</li><li>第五天</li><li>第六天</li><li>第七天</li>
  	</ul>

  </div>
</template>

<script>
export default {
  name: 'signDate',
  props: ['signdata'],
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
div{
	font-size: .12rem;
}
ul{
	margin: 0px;
	padding: 0px;
	text-align: center;
}
ul li{
	list-style: none;
	display: inline-block;
	color: white;
}
.gold li{
	height: .5rem;
	width: .5rem;	
	margin: .15rem;
	border-radius: 50%;
	border: 1px solid white;
	line-height: .5rem;
	font-size: .25rem;
	position: relative;
}
.day{
	margin-top: -.15rem;
}
.day li{
	width: .82rem;
	font-size: .12rem;
	transform: scale(.6);
}
img{
	width: .36rem;
	height: .29rem;
	position: absolute;
	top: .31rem;
	right: .04rem;
}
.done{
	color: red;
	background-color: white;
}
</style>
