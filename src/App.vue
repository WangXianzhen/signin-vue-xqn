<template>
  <div id="app">
    <guide @showtip="ishow"/>
    <totaldays :day="person.running_days"/>
    <signIn :person="person" @signin="postSignMessage"/>
    <signdate :signdata="person.sign_data"/>
    <mygolds :person="person"/>
    <notice/>
    <notice2/>
    <selling v-bind:headtitle="headtitle[0]"/>
    <job/>
    <selling v-bind:headtitle="headtitle[1]"/>
    <ruletips :ishow="show" @showtip="ishow"/>
    <goods :goods="items"/>
  </div>
</template>

<script>
import guide from './components/guide'
import totaldays from './components/totaldays'
import signIn from './components/signIn'
import signdate from './components/signdate'
import mygolds from './components/mygolds'
import notice from './components/notice'
import notice2 from './components/notice2'
import job from './components/job'
import selling from './components/selling'
import ruletips from './components/ruletips'
import goods from './goods'

export default {
  name: 'App',
  data(){
    return{
      items: [],
      person: null,
      headtitle:[{
        "ch":'做任务 领金币',
        "en":'WELFARE'
      },{
        "ch":'这些商品正在热卖',
        "en":'HOT SELLING GOODS'
      }],
      show: false
    }
  },
  methods: {
    ishow: function(data){
      return this.show = data
    },
    // 获取商品列表
    getGoods: async function(){
      let resp = await this.$http.get('https://www.xiaohongchun.com.cn/lsj/v1/home/rec?page_mark=0&page_size=20&is_sign=1')
      this.items = resp.data.data
    },
    // 获取个人信息
    personalInfomation: async function(){
      let resp = await this.$http({
        method: 'get',
        url: 'https://www.xiaohongchun.com.cn/lsj/v3/daily_sign',
        headers: {
          'token': '570694 78df366e6b15320019cbdfd06e0d04d064d2fe3c',
          'request-id': Math.random()
        }
      })
      this.person = resp.data      
    },
    // post签到信息
    postSignMessage: async function(){
      let resp = await this.$http({
        method: 'post',
        url: 'https://www.xiaohongchun.com.cn/lsj/v3/daily_sign',
        headers: {
          'token': '570694 78df366e6b15320019cbdfd06e0d04d064d2fe3c',
          'request-id': Math.random()
        },
        data: {
          "formId": "1532611036745"
        }
      })
      this.personalInfomation()
    },
    // 原生写法
    // personalInfomation: function(){
    //   this.$http({
    //     method: 'get',
    //     url: 'https://www.xiaohongchun.com.cn/lsj/v3/daily_sign',
    //     headers: {
    //       'token': '570694 80105118882222a9f90c1161fd88018ce392ae45',
    //       'request-id': Math.random()
    //     }
    //   }).then((response)=>{
    //         this.person = response.data
    //   })        
    // }
  },
  created() {
    this.getGoods();
    this.personalInfomation();
  },
  components: {
    guide,
    totaldays,
    signIn,
    signdate,
    mygolds,
    notice,
    notice2,
    job,
    selling,
    ruletips,
    goods 
  }
}
</script>

<style>
body{
  background: url(assets/head-backgroundcolor.jpg) no-repeat;
  background-size: contain;
  background-position: top center;
  margin:.35rem;
}
</style>