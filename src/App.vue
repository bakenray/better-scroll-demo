<template>
  <div id="app" ref="app">
    <div class="content">
        <div class="item"  v-for="(list) in nav" :key="list.id" :ref="'item'+list.id">
          <h3>{{list.title}}</h3>
          <p v-for="(p,index) in list.content" :key="index">{{p}}</p>
        </div>
    </div>
    <div class="nav">
      <ul>
        <li v-for="(text,index) in nav" :key="index" @click="scrollTo(text.id)">{{text.name}}</li>
      </ul>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
import { setTimeout } from 'timers';
export default{
  name:'app',
  data(){
    return{
      scroll:{},
      nav:[
        {
          id:1,
          name:'第1个',
          title:'title的文字内容11',
          content:['文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容','文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容']
        },
        {
          id:2,
          name:'第2个',
          title:'title的文字内容22',
          content:['文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容','文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容']
        },
        {
          id:3,
           name:'第3个',
          title:'title的文字内容33',
          content:['文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容','文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容']
        },
        {
          id:4,
          name:'第4个',
          title:'title的文字内容44',
          content:['文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容','文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容']
        },
        {
          id:5,
          name:'第5个',
          title:'title的文字内容55',
          content:['文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容','文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容文章的文字内容']
        }
      ]
    }
  },
  methods:{
    scrollTo(id){
      let names = 'item'+ id
      this.$nextTick(()=>{
          this.scroll.scrollToElement(this.$refs[names][0],1000,0,-70)
      })
    }
  },
  mounted(){
    this.$nextTick(()=>{
      this.scroll = new BScroll(this.$refs.app,{
        scrollY: true,
        click: true,
        bounce:true,
        momentum:true
      })
    })
  }
}
</script>

<style>
*{
  margin:0;padding:0;list-style: none;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height:100vh;
}
.nav{
  width:100%;
  height:60px;
  line-height: 60px;
  text-align: center;
  position: fixed;
  top:0;
  left:0;
  background: #fff;
  border-bottom: 1px solid #ccc;
}
.nav>ul{
  display: flex;
  align-items: center;
  justify-content: space-around;
  width:100%;
  height:100%;
}
.nav>ul>li{
  cursor: pointer;
  border:1px solid #ccc;
  border-radius: 10px;
  padding:0 16px;
  font-size: 12px;
  height:40px;
  line-height: 40px;
}
.content{
  padding:70px 20px 20px 20px;
}
.item{
  margin-top:30px;
}
</style>
