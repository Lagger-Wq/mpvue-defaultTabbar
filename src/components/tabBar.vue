<template>
  <div class="tabbar-wrap">
    <ul class="tabbar">
      <li class="tabbar-item" v-for="(item, index) in navList" 
          :key="index" 
          @click="selectNavItem(index, item.pagePath)"
          :class="item.isSpecial ? 'wrapSpecial':''">
              <p class="tabbar-icon" >
                  <img alt="tabbar-icon" 
                  :src="selectNavIndex == index? item.selectedIconPath : item.iconPath" 
                  :class="item.isSpecial ? 'imgSpecial':''"
                  >
              </p>
              <p class="tabbar-text" :class="selectNavIndex == index? 'active':''">
                  {{item.text}}
              </p>
          </li>
    </ul>
  </div>
</template>
<script>
export default {
  props: ["selectNavIndex"],
  data() {
    return {
      color: "#979795",
      selectedColor: "#45b7af",
      navList: []
    };
  },
  methods: {
    /**
     * 点击导航栏
     */
    selectNavItem(index, pagePath) {
      // console.log(this.index);
      // console.log(pagePath);

      if (index === this.selectNavIndex) {
        return false;
      }
this.bindNavigateTo(pagePath)
    },

    /**
     * 路由跳转
     */
    bindNavigateTo(url) {
      wx.reLaunch({
        url
      });
    }
  },
  created (){
    console.log(wx.getStorageSync('type'),'created')
   this.navList= wx.getStorageSync('type') == 'teacher' ? 
      [
        {
          text: "首页",
          pagePath: "/pages/teacherIndex/main",
          iconPath: "../../static/tabs/home.png",
          selectedIconPath: "../../static/tabs/home-active.png"
        },
        {
          text: "订单",
          pagePath: "/pages/logs/main",
          iconPath: "../../static/tabs/orders.png",
          selectedIconPath: "../../static/tabs/orders-active.png"
        },
        {
          text: "我的",
          pagePath: "/pages/counter/main",
          iconPath: "../../static/tabs/home.png",
          selectedIconPath: "../../static/tabs/home-active.png"
        },
        {
          text: "教师",
          pagePath: "/pages/teacher/main",
          iconPath: "../../static/tabs/home.png",
          selectedIconPath: "../../static/tabs/home-active.png"
        }
      ] : [
        {
          text: "首页",
          pagePath: "/pages/index/main",
          iconPath: "../../static/tabs/home.png",
          selectedIconPath: "../../static/tabs/home-active.png"
        },
        {
          text: "订单",
          pagePath: "/pages/logs/main",
          iconPath: "../../static/tabs/orders.png",
          selectedIconPath: "../../static/tabs/orders-active.png"
        },
        {
          text: "我的",
          pagePath: "/pages/counter/main",
          iconPath: "../../static/tabs/home.png",
          selectedIconPath: "../../static/tabs/home-active.png"
        },
        {
          text: "学生",
          pagePath: "/pages/sdudent/main",
          iconPath: "../../static/tabs/home.png",
          selectedIconPath: "../../static/tabs/home-active.png"
        }
      ]
      
  },
  onShow(){
    console.log(wx.getStorageSync('type'),'onShow')
   this.navList= wx.getStorageSync('type') == 'teacher' ? 
      [
        {
          text: "首页",
          pagePath: "/pages/teacherIndex/main",
          iconPath: "../../static/tabs/home.png",
          selectedIconPath: "../../static/tabs/home-active.png"
        },
        {
          text: "订单",
          pagePath: "/pages/logs/main",
          iconPath: "../../static/tabs/orders.png",
          selectedIconPath: "../../static/tabs/orders-active.png"
        },
        {
          text: "我的",
          pagePath: "/pages/counter/main",
          iconPath: "../../static/tabs/home.png",
          selectedIconPath: "../../static/tabs/home-active.png"
        },
        {
          text: "教师",
          pagePath: "/pages/teacher/main",
          iconPath: "../../static/tabs/home.png",
          selectedIconPath: "../../static/tabs/home-active.png"
        }
      ] : [
        {
          text: "首页",
          pagePath: "/pages/index/main",
          iconPath: "../../static/tabs/home.png",
          selectedIconPath: "../../static/tabs/home-active.png"
        },
        {
          text: "订单",
          pagePath: "/pages/logs/main",
          iconPath: "../../static/tabs/orders.png",
          selectedIconPath: "../../static/tabs/orders-active.png"
        },
        {
          text: "我的",
          pagePath: "/pages/counter/main",
          iconPath: "../../static/tabs/home.png",
          selectedIconPath: "../../static/tabs/home-active.png"
        },
        {
          text: "学生",
          pagePath: "/pages/sdudent/main",
          iconPath: "../../static/tabs/home.png",
          selectedIconPath: "../../static/tabs/home-active.png"
        }
      ]
      
  },
  // mounted (){
  //   console.log('mounted')
  // },
  computed: {
    isIphoneX() {
      //   return this.$store.getters.isIphoneX;
    }
  }
};
</script>
<style lang="less" scoped>
.tabbar-wrap {
  position: fixed;
  bottom: 0;
  left: 0;
  height: 92rpx;
  width: 100%;
  padding-top: 6rpx;
  box-shadow: 0 0 2px #c4c4c4;
}

.isIphoneX {
  padding-bottom: 66rpx;
}

.tabbar {
  display: flex;
}

.tabbar-item {
  flex: 1;
}

.tabbar-icon {
  height: 56rpx;
  text-align: center;
  position: relative;
img {
  width: 56rpx;
  height: 56rpx;
}
}


.imgSpecial {
  width: 84px;
  height: 84px;
}

.tabbar-text {
  text-align: center;
  line-height: 36rpx;
  color: #979795;
  font-size: 11px;
}

.active {
  color: #45b7af;
}

.wrapSpecial {
}

// .tabbar-icon {
//   position: absolute;
//   top: -36px;
//   width: 84px;
//   height: 84px;
//   padding: 6px;
//   top: -36px;
//   left: 50%;
//   // margin-left:-((@width + @padding * 2 ) / 2);
//   border-radius: 50%;
//   border-top: 2px solid #c4c4c4;
//   text-align: center;
// }

.tabbar-text {
  position: relative;
  bottom: 0;
}
</style>