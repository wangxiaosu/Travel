<template>
    <div>
        <p class="recommend-title">热门推荐</p>
        <router-link :to="'/detail/' + item.id" tag="div" class="item border-bottom" v-for="item of recommendList" :key="item.id">
            <img class="item-img" :src="item.imgUrl" alt="">
            <div class="item-info">
                <p class="item-title">{{item.title}}</p>
                <p class="item-address">{{item.address}}</p>
                <button class="item-detail">查看详情</button>
            </div>
        </router-link>
    </div>
</template>

<script>

export default {
  name: 'HomeRecommend',
  props: {
    recommendList: Array
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
    display flex
    height 3rem
    .item-img
      margin .2rem
      height 80%
    .item-info
      margin-top .3rem
      flex 1
      min-width 0
      .item-title
        font-size .4rem
        ellipsis()
      .item-address
        margin .2rem 0
        ellipsis()
      .item-detail
        height .5rem
        line-height .5rem
        background $bgColor
        color #fff
</style>
