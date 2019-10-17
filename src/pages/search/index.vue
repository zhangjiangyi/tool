<template>
  <div>
    <div class="search">
      <div class="header-r" @click="searchClick">
        <i class="icon icon-search" />
        <input v-model="search" placeholder="请输入故障内容" />
      </div>
      <button class="search-b" @click="on_search_click">搜索</button>
    </div>
    <div class="search-content" v-if="searchData.length>0">
      <ul v-for="(item, index) in searchData" :key="index">
        <li class="item">
          <span class="title">{{item.title}}</span>
          <span class="content">{{item.content}}</span>
          <span class="time">{{item.time}}</span>
          <div class="link"></div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchData: [
        {
          title: "故障1 10086",
          content:
            "一大堆奇奇怪怪的错误正在来袭,一大堆奇奇怪怪的错误正在来袭,一大堆奇奇怪怪的错误正在来袭一大堆奇奇怪怪的错误正在来袭.",
          time: "2019.09.10"
        },
        {
          title: "故障1 10010",
          content:
            "一大堆奇奇怪怪的错误正在来袭,一大堆奇奇怪怪的错误正在来袭,一大堆奇奇怪怪的错误正在来袭一大堆奇奇怪怪的错误正在来袭.",
          time: "2019.09.10"
        },
        {
          title: "故障1 10000",
          content:
            "一大堆奇奇怪怪的错误正在来袭,一大堆奇奇怪怪的错误正在来袭,一大堆奇奇怪怪的错误正在来袭一大堆奇奇怪怪的错误正在来袭.",
          time: "2019.09.10"
        }
      ]
    };
  },
  computed: {},
  methods: {
    // 搜索
    on_search_click() {}
  }
};
</script>

<style lang="scss" scoped>
.search {
  display: flex;
  background-color: #ffffff;
  align-items: center;
  .header-r {
    display: flex;
    align-items: center;
    flex: 1;
    background-color: #f4f4f4;
    height: 60rpx;
    border-radius: 30rpx;
    align-items: center;
    margin-left: 30rpx;
    margin-right: 10rpx;
    i {
      color: #666;
      font-size: 32rpx;
      margin-left: 20rpx;
    }
    input {
      color: #666;
      font-size: 24rpx;
      margin-left: 30rpx;
    }
  }
  .search-b {
    width: 100rpx;
    height: 50rpx;
    margin-right: 30rpx;
    font-size: 20rpx;
  }
}

.search-content {
  margin-top: 10rpx;
  margin-left: 30rpx;
  margin-right: 30rpx;
  .item {
    display: flex;
    flex-direction: column;
    .title {
      font-size: 40rpx;
      margin-top: 20rpx;
    }
    .content {
      color: #AAA;
      font-size: 30rpx;
      margin-top: 20rpx;
    }
    .time {
      color: #AAA;
      font-size: 30rpx;
      margin-top: 20rpx;
    }
    .link {
      width: 100%;
      height: 1px;
      border-top: solid #DDD 1px;
      margin-top: 30rpx;
    }
  }
}
</style>