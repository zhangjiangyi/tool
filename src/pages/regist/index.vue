<template>
  <div>
    <div class="item">
      <input @input="getPhone" type="number" focus="true" maxlength="11" placeholder="请输入手机号" />
    </div>
    <i class="error-prompt" v-if="isShowPhoneError">请输入正确的手机号</i>
    <div class="item">
      <input @input="getCode" type="text" maxlength="6" placeholder="验证码" />
      <button @click="on_registcode_b">{{codeLabel}}</button>
    </div>
    <button class="regist-b" @click="on_regist_b">注册</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isShowPhoneError: false,
      phone: "",
      code: "",
      timer: -1,
      codeLabel: "验证码"
    };
  },

  methods: {
    /**获取验证码 */
    on_registcode_b(event) {
      if (this.time == -1) {
        return;
      }
      let isPhone = this.chencPhone(); // 验证手机号是否正确
      this.isShowPhoneError = !isPhone;
      if (isPhone) {
        //说明正确 发送验证码 18244295300
        let time = 60;
        this.timer = setInterval(() => {
          this.codeLabel = `${--time}后重新发送`;
          if (time <= 0) {
            this.codeLabel = "验证码";
            clearInterval(this.timer);
            this.timer = -1;
          }
        }, 1000);
      }
    },

    /**点击注册 */
    on_regist_b() {
      if (!this.chencPhone()) {
        return;
      }
      if (!this.code) {
        return wx.showToast({
          title: "输入验证码"
        });
      }

      // 注册逻辑
      wx.showToast({
        title: "注册成功"
      });
    },

    getPhone(e) {
      this.phone = e.target.value;
    },

    getCode(e) {
      this.code = e.target.value;
    },

    chencPhone() {
      return /^1[3|4|5|8][0-9]\d{4,8}$/.test(this.phone);
    }
  }
};
</script>

<style lang="scss" scoped>
.item {
  display: flex;
  height: 80rpx;
  width: 90%;
  margin: 5% 10rpx 0rpx 5%;
  align-items: center;
  padding-left: 10rpx;
  border-radius: 10rpx;
  border-style: solid;
  border-width: 1rpx;
  border-color: #aaa;
  button {
    font-size: 33rpx;
    height: 80rpx;
    margin-right: 0rpx;
    color: #fff;
    background-color: rgb(24, 185, 77);
  }
}

.error-prompt {
  font-size: 25rpx;
  margin-left: 5%;
  color: rgb(255, 48, 49);
}

.regist-b {
  color: #fff;
  width: 90%;
  font-size: 35rpx;
  background-color: rgb(24, 185, 77);
  margin-top: 40rpx;
}
</style>