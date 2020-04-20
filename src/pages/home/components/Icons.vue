<template>
    <div class="icons">
        <swiper :options="swiperOptions" v-if="showSwiper">
            <swiper-slide v-for="(page,index) of pages" :key="index">
                <div class="icon" v-for="item of page" :key="item.id">
                    <div class="icon-img"><img class="icon-content" :src="item.imgUrl" alt=""></div>
                    <p class="icon-p">{{item.desc}}</p>
                </div>
            </swiper-slide>
        </swiper>
    </div>
</template>

<script>
export default {
  name: 'HomeIcons',
  props: {
    iconList: Array
  },
  data () {
    return {
      swiperOptions: {
        loop: true
      }
    }
  },
  computed: {
    pages () {
      const pages = []
      this.iconList.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    },
    showSwiper () {
      return this.iconList.length
    }

  }
}
</script>

<style lang="stylus" scoped>
    @import '~@styles/ellipsis.styl';
    .icons >>> .swiper-container
      height 0
      padding-bottom 50%
      overflow hidden
      margin-top .2rem
      .icon
        height 0
        position relative
        width 25%
        padding-bottom 25%
        float left
        .icon-img
          position absolute
          .icon-content
            display block
            width 80%
            margin 0 auto
        .icon-p
            width 100%
            position absolute
            bottom 0
            text-align center
            ellipsis()
</style>
