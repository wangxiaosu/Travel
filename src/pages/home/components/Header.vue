<template>
    <div class="header">
        <!-- <div class="header-left">
            <span class="iconfont">&#xe654;</span>
        </div> -->
        <div class="header-input">
            <span class="iconfont iconfont-search">&#xe612;</span>
            输入城市/景点/游玩主题
        </div>
        <router-link to="/city" tag="div">
          <div class="header-right">
              {{this.city}}
            <span class="iconfont iconfont-down">&#xe736;</span>
          </div>
        </router-link>
    </div>
</template>

<script>
import { mapState } from 'vuex'
export default {
  name: 'HomeHeader',
  computed: {
    ...mapState(['city'])
  }
}
</script>

<style lang="stylus" scoped>
@import '~@styles/variblies.styl';
    .header
        display flex
        line-height $HeaderHight
        background-color $bgColor
        color white
        .header-left
            float left
            width .64rem
            text-align center
        .header-input
            flex 1
            height .64rem
            line-height .64rem
            margin-top .11rem
            margin-left .2rem
            background-color #fff
            color #ccc
            border-radius .1rem
            .iconfont-search
                margin-left .1rem
        .header-right
            float right
            min-width 1.04rem
            padding 0 .1rem
            text-align center
            .iconfont-down
                margin-left -.05rem
                font-size .2rem
</style>
