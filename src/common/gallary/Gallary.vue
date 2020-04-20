<template>
    <div class="container" @click="handleTrans">
      <div class="wrapper">
        <swiper :options="swiperOptions" v-if="imgsLength">
          <swiper-slide v-for="(item,index) of imgs" :key="index">
              <img class="img-wrapper" :src="item">
          </swiper-slide>
        <div class="swiper-pagination"  slot="pagination"></div>
        </swiper>
      </div>
    </div>
</template>

<script>
import Vue from 'vue'
Vue.prototype.bus = new Vue()
export default {
  name: 'CommonGallary',
  props: {
    imgs: {
      type: Array,
      default () {
        return []
      }
    }
  },
  computed: {
    imgsLength () {
      return this.imgs.length
    }
  },
  methods: {
    handleTrans () {
      this.$emit('change')
    }
  },
  data () {
    return {
      swiperOptions: {
        pagination: '.swiper-pagination',
        paginationType: 'fraction',
        loop: true,
        observer: true,
        observeParents: true
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
  .container >>> .swiper-container
    overflow inherit
  .container
    z-index 99
    display flex
    flex-direction column
    justify-content center
    position fixed
    left 0
    top 0
    right 0
    bottom 0
    background #000
    .wrapper
      width 100%
      height 0
      padding-bottom 66%
      .img-wrapper
        width 100%
      .swiper-pagination
        color #fff
        bottom -1.5rem
</style>
