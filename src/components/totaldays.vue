<template>
  <div class="">
    <p> 您已连续签到 <span>{{day}}</span> 天</p>
  </div>
</template>

<script>
export default {
  name: 'totaldays',
  props: ['day']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
div{
  margin-top: .1rem;
}
p{
  font-size: .3rem; 
  color: white;
  text-align: center;
  margin: 0px;
}
span{
  font-size: .4rem;
}
</style>