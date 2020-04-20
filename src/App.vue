<template>
  <div id="app">
    <keep-alive exclude="Detail">
       <router-view/>    <!-- 显示当前地址所对应的内容（组件） -->
    </keep-alive>
  </div>
</template>

<script>
export default {
  name: 'App',
  watch: {
    '$route': function (to, from) {
      document.body.scrollTop = 0
      document.documentElement.scrollTop = 0
    }
  }
}
</script>

<style>

</style>
