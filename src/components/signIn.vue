<template>
  <div v-on:click.once="sign" v-bind:class="{done: isDone}">
    <span class="gold">签到领</span>
    <span class="num">{{msg}}</span>
    <span class="gold">金币</span>
  </div>
</template>

<script>
export default {
  name: 'signIn',
  props: ['person'],
  data () {
    return {
      isDone : this.person.signed
    }
  },
  computed:{
    msg:function(){
      if (this.isDone) {
        return "今日已签到"
      } else {
        return "5"
      }
    }
  },
  methods: {
    sign: function(){
      if (isDone == false) {
      this.$emit("signin",true)
      return this.isDone = true        
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
div{   
  text-align: center;
  background: -webkit-linear-gradient(top,#ffef90,#fac047);
  border-radius: .3rem;
  font-size: .25rem;
  width: 2.2rem;
  height: .6rem;
  line-height: .6rem;
  margin: .20rem auto;
  color: white;
  box-shadow: 0 0 .1rem #200000;
}
.num{
  font-size: .4rem;
}
.done{
  background: gray;
}
.done span{
  font-size: .25rem;
}
.done .gold{
  display: none;
}
</style>