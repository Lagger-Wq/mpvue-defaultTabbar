<template>
  <div>
     <h1>教师</h1>
     <tab-bar :selectNavIndex='3' />
  </div>
</template>

<script>
import tabBar from '@/components/tabBar'

export default {
  components: {
    tabBar
  },

  data () {
    return {
      teacher: [],
    }
  },

  created () {
  }
}
</script>

<style>
</style>
