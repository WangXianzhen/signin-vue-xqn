<template>
  <div id="app">
    <guide @showtip="ishow"/>
    <signInDays :day="person.running_days"/>
    <signIn :person="person" @signin="postSignMessage"/>
    <signDate :signdata="person.sign_data"/>
    <myGolds :person="person"/>
    <notice/>
    <notice2/>
    <hotsell v-bind:headtitle="headtitle[0]"/>
    <job/>
    <hotsell v-bind:headtitle="headtitle[1]"/>
    <tips :ishow="show" @showtip="ishow"/>
    <goods :goods="items"/>
  </div>
</template>

<script>
import guide from './components/guide'
import signInDays from './components/signInDays'
import signIn from './components/signIn'
import signDate from './components/signDate'
import myGolds from './components/myGolds'
import notice from './components/notice'
import notice2 from './components/notice2'
import job from './components/job'
import hotsell from './components/hotsell'
import tips from './components/tips'
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
    getGoods: async function(){
      let resp = await this.$http.get('https://www.xiaohongchun.com.cn/lsj/v1/home/rec?page_mark=0&page_size=20&is_sign=1')
      this.items = resp.data.data
    },
    personalInfomation: async function(){
      let resp = await this.$http({
        method: 'get',
        url: 'https://www.xiaohongchun.com.cn/lsj/v3/daily_sign',
        headers: {
          'token': '570694 80105118882222a9f90c1161fd88018ce392ae45',
          'request-id': Math.random()
        }
      })
      this.person = resp.data      
    },

    
    postSignMessage: async function(){
      let resp = await this.$http({
        method: 'post',
        url: 'https://www.xiaohongchun.com.cn/lsj/v3/daily_sign',
        headers: {
          'token': '570694 80105118882222a9f90c1161fd88018ce392ae45',
          'request-id': Math.random()
        },
        data: {
          "formId": "1532611036745"
        }
      })
    },

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
  // beforeCreate(){},
  components: {
    guide,
    signInDays,
    signIn,
    signDate,
    myGolds,
    notice,
    notice2,
    job,
    hotsell,
    tips,
    goods 
  },
}
</script>

<style>
body{
  background: url(assets/head-backgroundcolor.jpg) no-repeat;
  background-size: contain;
  background-position: top center;
  margin:.35rem;
}
#app{
}
</style>
