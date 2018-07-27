<template>
  <div class="sell">
	<header>{{headtitle.ch}}</header>
	<p>{{headtitle.en}}</p>
  </div>
</template>

<script>
export default {
  name: 'selling',
  props:['headtitle']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.sell{
	margin: auto;	
}
header{
	font-size: .32rem;
}
p{
	font-size: .10rem;
	color: #f9d6d6;
	margin: auto;
}
</style>
