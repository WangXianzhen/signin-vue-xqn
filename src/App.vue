<template>
  <div id="app">
    <ViewRule @showtip="ishow"/>
    <TotalDays :day="person.running_days"/>
    <SignIn :person="person" @signin="postSignMessage"/>
    <SignDate :signdata="person.sign_data"/>
    <MyGolds :person="person"/>
    <NoticeMsg/>
    <!-- <NoticeMsg2/> -->
    <selling v-bind:headtitle="headtitle[0]"/>
    <TaskForGolds/>
    <selling v-bind:headtitle="headtitle[1]"/>
    <RuleTips :ishow="show" @showtip="ishow"/>
    <GoodsList :goods="items"/>
  </div>
</template>

<script>
import ViewRule from './components/ViewRule'
import TotalDays from './components/TotalDays'
import SignIn from './components/SignIn'
import SignDate from './components/SignDate'
import MyGolds from './components/MyGolds'
import NoticeMsg from './components/NoticeMsg'
import NoticeMsg2 from './components/NoticeMsg2'
import TaskForGolds from './components/TaskForGolds'
import selling from './components/selling'
import RuleTips from './components/RuleTips'
import GoodsList from './GoodsList'

export default {
  name: 'App',
  data(){
    return{
      items: [],
      person: {
        "user": {
          "nick": "徐启能",
          "icon": "https://thirdwx.qlogo.cn/mmopen/vi_32/Q0j4TwGTfTKBQibGn2dNyI7RI2kwAjkCZGTwhd57RoFBbDMcWECpFXazq20KS62icKdlVN4ia4micv6vK7Cxpfw6zQ/132"
        },
        "signed": false,
        "coin": 0,
        "running_days": 0,
        "sign_data": [{
          "coin": 1,
        }],
      },
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
          'token': '570694 d85864c7322962a87e34f24c87f7d31073e34740',
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
          'token': '570694 d85864c7322962a87e34f24c87f7d31073e34740',
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
    //       'token': '570694 bd0e23fa55c3641639e631d647a8701054453feb',
    //       'request-id': Math.random()
    //     }
    //   }).then((response)=>{
    //         this.person = response.data
    //   })        
    // }
  },
  created() {
    this.personalInfomation();
    this.getGoods();
  },
  components: {
    ViewRule,
    TotalDays,
    SignIn,
    SignDate,
    MyGolds,
    NoticeMsg,
    NoticeMsg2,
    TaskForGolds,
    selling,
    RuleTips,
    GoodsList 
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