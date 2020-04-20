<template>
    <div class="list wrapper" ref="wrapper">
        <div class="content">
            <div class="area">
                <div class="title border-topbottom">当前城市</div>
                <div class="list-button">
                    <div class="button-wrapper">
                        <div class="button" @click="handleChangeCity(currentCity)">{{this.currentCity}}</div>
                    </div>
                </div>
            </div>
            <div class="area">
                <div class="title border-topbottom">热门城市</div>
                <div class="list-button">
                    <div class="button-wrapper" v-for="item of hotCities" :key="item.id">
                        <div class="button" @click="handleChangeCity(item.name)">{{item.name}}</div>
                    </div>
                </div>
            </div>
            <div class="area" v-for="(item,key) of cities" :key="key" :ref="key">
                <div class="title border-topbottom">{{key}}</div>
                <div class="city-wrapper">
                    <div class="city border-bottom" v-for="data of item" :key="data.id" @click="handleChangeCity(data.name)">{{data.name}}</div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import BetterScroll from 'better-scroll'
import { mapState, mapMutations } from 'vuex'
export default {
  computed: {
    ...mapState({
      currentCity: 'city'
    })
  },
  methods: {
    handleChangeCity (city) {
      this.changeCity(city)
      this.$router.push('/')
    },
    ...mapMutations(['changeCity'])
  },
  name: 'CityList',
  props: {
    hotCities: Array,
    cities: Object,
    letter: String
  },
  mounted () {
    this.scroll = new BetterScroll(this.$refs.wrapper, {click: true})
  },
  watch: {
    letter () {
      const element = this.$refs[this.letter][0]
      if (this.letter) {
        this.scroll.scrollToElement(element)
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
  .border-topbottom
    &:before
      border-color #ccc
    &:after
      border-color #ccc
  .border-bottom
    &:before
      border-color #ccc
 .list
   position absolute
   left 0
   top 1.6rem
   right 0
   bottom 0
   overflow hidden
   .title
      height .40rem
      background-color #eee
      padding .15rem
      color #666
   .list-button
      padding-bottom .2rem
      padding-right .5rem
      overflow hidden
      .button-wrapper
        margin-left .2rem
        margin-top .2rem
        float left
        width 30%
        .button
          line-height .5rem
          border .02rem solid #ccc
          text-align center
          border-radius .1rem
    .city-wrapper
       .city
         line-height .72rem
         padding-left .3rem
         color #666
         font-size 16px
</style>
