<template>
  <div class="mygold">
  	<div class="headphoto">
  		<img v-bind:src="person.user.icon">
  	</div>
  	<span class="name">{{person.user.nick}}</span>
  	<span class="goldnum">{{person.coin}}</span><img src="../assets/gold_03.png">
  </div>
</template>

<script>
export default {
  name: 'mygolds',
  props: ['person']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.mygold{
	margin-top: .2rem;
	height: 1.2rem;
	background-color: white;
	border-radius: 0.15rem;
	box-shadow: 0 0 .25rem #f39a9a;
	line-height: 1.2rem;
}
.headphoto{
	width: .7rem;
	height: .7rem;
	margin-left: .3rem;
	/* border: 1px solid black; */
	border-radius: 50%;
/* 	background: url(../assets/logo.png);
	background-size: contain; */
	overflow:hidden;
	display: inline-block;
}
.name{
	font-size: .24rem;
	vertical-align: top;
}
.goldnum{
	font-family: DIN Condensed;
	font-size: .6rem;
	color: #4c4c4c;	
	vertical-align: middle;
	margin-left: 3.2rem;
}
img{
	width: .41rem;
	height: .36rem;
	vertical-align: middle;
}
.headphoto img{
	width: .7rem;
	height: .7rem;
	vertical-align: top;
}
</style>