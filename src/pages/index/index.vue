<template>
<div style="height:500px">
  <h1>学生首页</h1>
  <tab-bar :selectNavIndex='0' />
</div>
</template>

<script>
import tabBar from '@/components/tabBar'

export default {
  data () {
    return {
    }
  },

  components: {
    tabBar
  },

  methods: {
  },

  created () {
    // let app = getApp()
  }
}
</script>

<style scoped>
</style>
