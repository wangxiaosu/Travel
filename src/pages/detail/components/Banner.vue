<template>
    <div>
        <div class="banner" @click="handleGallaryClick">
            <img  class="banner-img" :src="this.bannerImg" alt="">
            <div class="banner-info">
                <div class="banner-title">{{this.sightName}}</div>
                <div class="banner-number"><span class="iconfont iconfont-down">&#xe7b3;</span>{{this.gallaryImgs.length}}</div>
            </div>
        </div>
        <div class="banner-address border-bottom">
          <span class="iconfont iconfont-down">&#xe6a6;</span>
          广东省广州市海珠区阅江西路222号
        </div>
        <fade-animation>
          <common-gallary :imgs="gallaryImgs" v-show="ShowGallary" @change="handleGallaryClickF"></common-gallary>
        </fade-animation>
    </div>
</template>

<script>
import Vue from 'vue'
import CommonGallary from '@/common/gallary/Gallary'
import FadeAnimation from '@/common/fade/FadeAnimation'

Vue.prototype.bus = new Vue()
export default {
  props: {
    sightName: String,
    bannerImg: String,
    gallaryImgs: Array
  },
  name: 'DetailBanner',
  data () {
    return {
      ShowGallary: false
    }
  },
  methods: {
    handleGallaryClick () {
      this.ShowGallary = true
    },
    handleGallaryClickF () {
      this.ShowGallary = false
    }
  },
  components: {
    CommonGallary,
    FadeAnimation
  }
}
</script>

<style lang="stylus" scoped>
  .border-bottom
    &:before
      border-color #ccc
  .banner
    position relative
    height 0
    padding-bottom 56%
    .banner-img
      width 100%
    .banner-info
      display flex
      position absolute
      left 0
      right 0
      bottom .4rem
      height .4rem
      color #fff
      background-image linear-gradient(top,rbga(0,0,0,0),rbga(0,0,0,.8))
      .banner-title
        padding-left .2rem
        font-size .36rem
        flex 1
      .banner-number
       height .3rem
       line-height .3rem
       margin-top .05rem
       padding-right .2rem
  .banner-address
    height .7rem
    margin-bottom .1rem
    .iconfont-down
      line-height .7rem
      padding 0 .1rem
</style>
