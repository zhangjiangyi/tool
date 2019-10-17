<template>
  <div>
    <ul class="list" v-for="(item, index) in converts" :key="index">
      <li class="item">
        <i>{{item.prompt}}</i>
        <input type="text" :value="item.value" @input="on_change($event, item)" />
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      converts: [
        {
          prompt: "十进制:",
          binary: 10,
          value: 0
        },
        {
          prompt: "二进制:",
          binary: 2,
          value: 0
        },
        {
          prompt: "八进制:",
          binary: 8,
          value: 0
        },
        {
          prompt: "十六进制:",
          binary: 16,
          value: 0
        }
      ]
    };
  },

  methods: {
    on_change(event, item) {
      let value = parseInt(event.target.value, item.binary) || 0;    // 先转化成10进制的
      this.converts.forEach(element => {
        let as = value.toString(element.binary);
        console.log(as);
        element.value = as;
      });
    }
  }
};
</script>

<style lang="scss" scoped>
.list {
  margin-top: 50rpx;
  .item {
    display: flex;
    justify-content: space-between;
    padding-left: 100rpx;
    padding-right: 100rpx;
    margin-bottom: 30rpx;
    input {
      border: 1px solid #cccccc;
      margin-right: 100prx;
    }
  }
}
</style>