<template>
    <div>
        <p class="recommend-title">周末去哪了</p>
        <div class="item border-bottom" v-for="item of weekendList" :key="item.id">
            <div class="item-img-wrapper">
                <img class="item-img" :src="item.imgUrl" alt="">
            </div>
            <div class="item-info">
                <p class="item-title">{{item.title}}</p>
                <p class="item-address">{{item.desc}}</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'HomeWeekend',
  props: {
    weekendList: Array
  }
}
</script>

<style lang="stylus" scoped>
@import '~@styles/variblies.styl';
@import '~@styles/ellipsis.styl';
  .recommend-title
    line-height .6rem
    background #ccc
    text-indent .2rem
    margin-top .2rem
 .item
    margin-top .2rem
    .item-img-wrapper
      height 0
      padding-bottom 37%
      overflow hidden
      .item-img
        width 100%
    .item-info
      margin-top .3rem
      flex 1
      min-width 0
      .item-title
        color #000
        font-size .3rem
      .item-address
        margin .2rem 0
        color #bbb
        ellipsis()
</style>
