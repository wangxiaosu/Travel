<template>
    <div class="header">
        <router-link to="/" tag="div">
          <div class="header-back">
            <span class="iconfont">&#xe654;</span>
          </div>
        </router-link>
        <div class="header-title">城市选择</div>
    </div>
</template>

<script>
import '@/assets/styles/iconfont.css'
export default {
  name: 'CityHeader'
}
</script>

<style lang="stylus" scoped>
@import '~@styles/variblies.styl';
  .header
    position relative
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
