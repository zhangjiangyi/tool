<template>
  <div>
    <div class="menus">
      <div
        class="item"
        v-for="(item, index) in menus"
        :key="index"
        @click="navigaToFunc(item.page)"
      >
        <div class="circle">
          <i class="icon" :class="item.icon" />
        </div>
        <span>{{item.name}}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      menus: [
        {
          icon: "menu-guzhang",
          name: "故障代码",
          page: "/pages/guzhang/main"
        },
        {
          icon: "menu-zhichi",
          name: "技术支持",
          page: "pages/guzhang/main"
        },
        {
          icon: "menu-ziliao",
          name: "技术资料",
          page: "pages/guzhang/main"
        },
        {
          icon: "menu-fanyi",
          name: "在线翻译",
          page: "pages/guzhang/main"
        },
        {
          icon: "menu-zhuanhuan",
          name: "进制转换",
          page: "pages/guzhang/main"
        },
        {
          icon: "menu-xiazai",
          name: "已下载资料",
          page: "/pages/guzhang/main"
        }
      ]
    };
  },
  methods: {
    navigaToFunc(page) {
      console.log(page);
      wx.navigateTo({ url: page });
    }
  }
};
</script>

<style lang="scss" scoped>
.menus {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  margin-top: 30rpx;
  .item {
    width: 30%;
    display: flex;
    align-items: center;
    flex-direction: column;
    box-sizing: border-box;
    .circle {
      width: 150rpx;
      height: 150rpx;
      border-radius: 4em;
      text-align: center;
      line-height: 75px;
      background: #e6e6e6;
    }
    .icon {
      font-size: 80rpx;
      color: #1296db;
    }
    span {
      font-size: 30rpx;
    }
  }
}
</style>