<template>
  <div>
    <h1>我的</h1>
    <button @click="goOtherModal">{{type == 'teacher' ? '切换至学生端' : '切换至老师端'}}</button>
    <tab-bar :selectNavIndex="2"/>
  </div>
</template>

<script>
// Use Vuex
import store from "./store";
import tabBar from "@/components/tabBar";

export default {
  data() {
    return {
      type: ""
    };
  },
  components: {
    tabBar
  },
  computed: {
    count() {
      return store.state.count;
    }
  },
  created() {
    this.type = wx.getStorageSync("type");
  },
  onShow() {
    this.type = wx.getStorageSync("type");
  },
  methods: {
    goOtherModal() {
      console.log(this.type,'type1')
      wx.setStorage({
        key: "type",
        data: this.type == "teacher" ? "student" : "teacher",
        success: () => {
          console.log(this.type,'type1')
          this.type == "student" ? wx.reLaunch({url: "/pages/teacherIndex/main"}) :  wx.reLaunch({url: "/pages/index/main"})
        }
      });
    }
  }
};
</script>

<style>
.counter-warp {
  text-align: center;
  margin-top: 100px;
}
.home {
  display: inline-block;
  margin: 100px auto;
  padding: 5px 10px;
  color: blue;
  border: 1px solid blue;
}
</style>
