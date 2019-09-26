<template>
  <div class="header">
    <div class="header-left">
      <span class="iconfont">返回</span>
    </div>
    <div class="header-input">输入城市/景点/游玩主题</div>
    <router-link to="/city">
      <div class="header-right">{{this.city}}</div>      
    </router-link>
  </div>
  
</template>

<script>
import { mapState } from 'vuex'
export default {
  name: 'HomeHeader',
  computed: {
    ...mapState(['city'])
  },
}
</script>

// stylus的功能还不清楚
<style lang='stylus' scoped>
  .header
  //外部box定义flex,里面的input定义flex为1,使得input自动撑开
    display: flex
    line-height: $headerHeight
    background: #00bcd4
    color: #fff
    .header-left
      width: .64rem
      float: left
    .header-input
      flex-grow: 1
      height: .64rem
      margin-top: .12rem
      margin-left: .2rem
      background: #fff
      border-radius: .1rem
      color #333
    .header-right
      min-width: 1.24rem
      padding .1rem
      float: right
      text-align: center
      color #fff
</style>>
