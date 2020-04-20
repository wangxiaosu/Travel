<template>
    <div>
        <router-link to="/" tag="div" class="detail-back" v-show="showBack">
           <div class="detail-back-left">
            <span class="iconfont">&#xe654;</span>
          </div>
        </router-link>
        <div class="detail-header" v-show="showHeader" :style="headStyle">
          <router-link to="/" tag="div" class="header-back">
              <span class="iconfont">&#xe654;</span>
          </router-link>
          <div class="header-title">城市选择</div>
       </div>
    </div>
</template>

<script>
import Vue from 'vue'
Vue.prototype.bus = new Vue()
export default {
  name: 'DetailHeader',
  data () {
    return {
      showHeader: false,
      headStyle: {
        opacity: 0
      },
      showBack: true
    }
  },
  mounted () {
    window.addEventListener('scroll', this.scrollMove)
  },
  destroyed () {
    window.removeEventListener('scroll', this.scrollMove)
  },
  methods: {
    scrollMove () {
      const top = document.documentElement.scrollTop || document.body.scrollTop || window.pageYOffset
      if (top > 60) {
        let opacity = top / 140
        opacity = opacity > 1 ? 1 : opacity
        this.headStyle.opacity = opacity
        this.showHeader = true
      } else {
        this.showHeader = false
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
@import '~@styles/variblies.styl';
  .detail-back
    z-index 1
    position absolute
    top .1rem
    left .1rem
    background rgba(0,0,0,.7)
    border-radius .4rem
    height .6rem
    width .6rem
    text-align center
    .detail-back-left
      color #fff
      line-height .7rem
      font-size .45rem
  .detail-header
    width 100%
    z-index 1
    position fixed
    overflow hidden
    height $HeaderHight
    line-height $HeaderHight
    background $bgColor
    color #fff
    .header-back
      position absolute
      left 0
      top 0
    .header-title
      margin-left -.3rem
      text-align center
</style>
