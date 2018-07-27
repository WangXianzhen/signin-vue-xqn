<template>
  <div class="notice">
  	<img src="../assets/notice_03.png">
  	<span>{{msg}}</span>
  </div>
</template>

<script>
export default {
  name: 'notice',
  data () {
    return {
      msg: '通知：积分改名金币了，原有积分不清零，可在个人中心查看！'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.notice{
  text-align: left;
  font-size: .12rem;
	color: red;	
	margin:.3rem auto;
}
img{
  height: .26rem;
  width: .27rem;
  vertical-align: bottom;
}
</style>