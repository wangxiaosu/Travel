<template>
    <div>
      <div  class="list" v-for="item of list" :key="item.id">
        <div class="list-ticket border-bottom">
          <span class="list-ticket-icon iconfont">&#xe760;</span>
          {{item.title}}
          <span class="ticket-price"></span>
        </div>
        <div v-if="item.children">
          <detail-list :list="item.children" class="list-children"></detail-list>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: 'DetailList',
  props: {
    list: Array
  }
}
</script>

<style lang="stylus" scoped>
  .list-children
    padding-left .3rem
  .list-ticket
    padding-left .1rem
    line-height .6rem
    .list-ticket-icon
      padding-right .1rem
      color skyblue
    .ticket-price
      float right
</style>
