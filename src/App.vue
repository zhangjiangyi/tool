<script>
/* 这部分相当于原生小程序的 app.js */
export default {
  create() {
    console.log("miniapp created!!!");
  }
};
</script>

<style lang="scss">
// @import "assets/iconfont.less";
@import "../lib/iconfont.less";
/* 这部分相当于原生小程序的 app.wxss */
.container {
  background-color: #cccccc;
}
</style>