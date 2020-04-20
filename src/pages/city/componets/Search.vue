<template>
    <div class="wrapper">
        <input class="input-wrapper" type="text" placeholder="请输入城市或拼音" v-model="keyword">
        <div class="search-list" ref="search" v-show="keyword">
          <ul>
            <li class="search-item border-bottom" v-for="item of list" :key="item.id" @click="handleChangeCity(item.name)">{{item.name}}</li>
            <li class="search-item border-bottom" v-show="!list.length">没有匹配城市</li>
          </ul>
        </div>
    </div>
</template>

<script>
import BetterScroll from 'better-scroll'
export default {
  name: 'CitySearch',
  props: {
    cities: Object
  },
  data () {
    return {
      keyword: '',
      list: []
    }
  },
  methods: {
    handleChangeCity (city) {
      this.$store.commit('changeCity', city)
      this.$router.push('/')
    }
  },
  watch: {
    keyword () {
      const result = []
      for (let i in this.cities) {
        this.cities[i].forEach(value => {
          if (value.spell.startsWith(this.keyword) || value.name.startsWith(this.keyword)) {
            result.push(value)
          }
        })
        this.list = result
      }
    }
  },
  mounted () {
    this.scroll = new BetterScroll(this.$refs.search, {click: true})
  }
}
</script>

<style lang="stylus" scoped>
@import '~@styles/variblies.styl';
.border-bottom
  &:before
    border-color #ccc
.wrapper
  margin-bottom .05rem
  background $bgColor
  height .72rem
  text-align center
  .input-wrapper
    box-sizing border-box
    padding 0 .2rem
    border-radius .05rem
    text-align center
    height .55rem
    width 90%
  .search-list
    z-index 1
    position absolute
    top 1.6rem
    left 0
    right 0
    bottom 0
    background-color #ffffff
    overflow hidden
    .search-item
      text-align left
      line-height .72rem
      padding-left .3rem
      color #666
      font-size 16px
</style>
