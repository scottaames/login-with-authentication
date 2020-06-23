<template>
  <div id="app">
    <AppBar />
    <router-view class="page" />
  </div>
</template>
<script>
import AppBar from '@/components/AppBar'
export default {
  components: {
    AppBar
  }
}
</script>
<style lang="scss">
.page {
  min-height: calc(100vh - 56px);
}
</style>
