<template>
	<div class="guide" @click="tip">
	   <span class="rule">{{msg}}</span>
	   <div class="circle">?</div>
	 </div>
</template>

<script>
export default {
  name: 'guide',
  data () {
    return {
		msg :"规则"
    }
  },
  methods: {
  	tip: function(){
  		this.$emit("showtip",true)
  	}
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.guide{
	text-align: right;
	color: white;
	font-size: .2rem;
	margin-top: .38rem;
}
.circle{
	height:.25rem;
	width:.25rem;
	border-radius:50%;
	border:1px solid #fff;
	display: inline-block;
	text-align: center;
	line-height: .25rem;
}
</style>