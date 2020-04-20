<template>
    <div class="alphabet">
        <div class="item"
             @click="handleLetterCLick($event)"
             @touchstart.prevent="handleTouchStrat"
             @touchmove="handleTouchMove"
             @touchend="handleTouchEnd"
             v-for="item of letters"
             :key="item"
             :ref="item">
          {{item}}
        </div>
    </div>
</template>

<script>
export default {
  name: 'CityAlphabet',
  props: {
    cities: Object
  },
  updated () {
    this.startY = this.$refs['A'][0].offsetTop
  },
  data () {
    return {
      isTouch: false,
      startY: '',
      timer: null
    }
  },
  computed: {
    letters () {
      const letter = []
      for (let i in this.cities) {
        letter.push(i)
      }
      return letter
    }
  },
  methods: {
    handleLetterCLick (e) {
      this.$emit('change', e.target.innerText)
    },
    handleTouchStrat () {
      this.isTouch = true
    },
    handleTouchMove (e) {
      if (this.isTouch) {
        if (this.timer) {
          clearTimeout(this.timer)
        }
        this.timer = setTimeout(() => {
          const touchY = e.touches[0].clientY - 78
          const index = Math.floor((touchY - this.startY) / 17)
          if (index >= 0 && index < this.letters.length) {
            this.$emit('change', this.letters[index])
          }
        }, 1)
      }
    },
    handleTouchEnd () {
      this.isTouch = false
    }
  }
}
</script>

<style lang="stylus" scoped>
@import '~@styles/variblies.styl';
  .box::-webkit-scrollbar
    display none
  .alphabet
    width .4rem
    position absolute
    top 1.6rem
    right 0
    height 100%
    display flex
    flex-direction column
    justify-content center
    .item
      text-align center
      line-height .35rem
      color $bgColor
</style>
