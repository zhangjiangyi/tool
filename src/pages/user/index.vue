<template>
  <div class="container">
    <div class="header-c">
      <img
        src="https://wx.qlogo.cn/mmopen/vi_32/Q0j4TwGTfTJvoc0l3Oe4lWTMtUvLd7UYm9IvSWNjM6S5ibZBu3OE5XbCEqgPw9llpibmkyqEX9GbLKOCfTIe6wWQ/132"
        alt
      />
      <div class="info-c">
        <span class="name">光强</span>
        <span class="phone">15214313256</span>
      </div>
    </div>
    <div class="list-c">
      <div
        class="item"
        v-for="(item, index) in itemList"
        :key="index"
        :data-index="index"
        @click="itemClick(item)"
      >
        <div class="item-l">
          <i class="icon" :class="item.icon"></i>
          <span class="title">{{item.title}}</span>
          <span class="amount" v-if="item.amount">{{item.amount}}</span>
        </div>
        <i class="icon mt-arrow-right-o"></i>
      </div>
    </div>
    <div class="btn" @click="logoutClick">退出账号</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      itemList: [
        {
          title: "个人中心",
          icon: "mt-red-packet-o",
          path: "/pages/redPacket/main",
          amount: 4
        },
        {
          title: "发帖",
          icon: "mt-coupon-o",
          path: "/pages/couponList/main",
          amount: 10
        },
        {
          title: "评论",
          icon: "mt-my-location-o",
          path: "/pages/addressList/main"
        },
        {
          title: "邀请有奖",
          icon: "mt-gift-o"
        },
        {
          title: "客服中心",
          icon: "mt-customer-service-o"
        },
        {
          title: "帮助和反馈",
          icon: "mt-help-o",
          path: "/pages/feedback/main"
        },
        {
          title: "协议和说明",
          icon: "mt-protocol-o",
          path: "/pages/protocol/main"
        }
      ]
    };
  },
  computed: {},
  methods: {
    itemClick(e) {
      wx.navigateTo({ url: e.path });
    },
    logoutClick() {
      wx.showModal({
        title: "确认退出？",
        content: "是否退出账号？",
        confirmColor: "#FFC24A",
        success: function(res) {
          if (res.confirm) {
            resolve("ok");
          } else if (res.cancel) {
            resolve("cancle");
          }
        }
      });
    }
  }
};
</script>

<style lang="scss" scoped>
.container {
  .header-c {
    display: flex;
    align-items: center;
    height: 200rpx;
    background-color: #1296db;
    img {
      width: 120rpx;
      height: 120rpx;
      border-radius: 60rpx;
      margin-left: 30rpx;
    }
    .info-c {
      display: flex;
      flex-direction: column;
      margin-left: 30rpx;
      .name {
        font-size: 32rpx;
        font-weight: bold;
      }
      .phone {
        font-size: 28rpx;
      }
    }
  }
  .list-c {
    display: flex;
    flex-direction: column;
    margin-top: 0rpx;
    background-color: white;
    .item {
      display: flex;
      align-items: center;
      height: 88rpx;
      padding: 10rpx;
      .item-l {
        display: flex;
        flex: 1;
        i {
          font-size: 38rpx;
        }
        .title {
          font-size: 28rpx;
          margin-left: 30rpx;
          margin-top: 6rpx;
        }
        .amount {
          font-size: 24rpx;
          margin: 0 10rpx;
          display: flex;
          margin-right: 10rpx;
          align-items: center;
        }
      }
      i {
        font-size: 24rpx;
      }
    }
  }
  .btn {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 88rpx;
    background-color: white;
    font-size: 28rpx;
  }
}
</style>
