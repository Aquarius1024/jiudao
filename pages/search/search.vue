<template>
  <view class="page-wrap">
    <view class="page-head search-head flex-ac">
      <view class="search-input flex-ajc">
        <image style="width: 28rpx; height: 28rpx; margin-right: 12rpx; position: relative; top: 2rpx;" src="../../static/images/icon/search.png" mode="aspectFit"></image>
        <input style="font-size: 32rpx;" v-model="keyword" @input="handleInput" placeholder="搜索图书名称" type="text">
      </view>
      <view class="search-cancel" @click="$emit('cancel')">取消</view>
    </view>
    <view class="page-content search-wrap">
      <scroll-view scroll-y class="result-wrap" :class="{visible: keyword.length > 0}">
        <view v-for="item in 100" @click="gotoDetail(item)">{{item}}</view>
      </scroll-view>
      <view class="static-wrap" :class="{visible: keyword.length === 0}">
        <card-block
          title="历史搜索"
          :tags="searchHistory"
          @selectTag="handleSelectTag">
        </card-block>
        <card-block
          title="热门搜索"
          :tags="searchHistory"
          @selectTag="handleSelectTag">
        </card-block>
      </view>
    </view>
  </view>
</template>

<script>
  import CardBlock from '@/components/CardBlock/CardBlock.vue'
  let timer = null
  
  export default {
    components: {
      CardBlock
    },
    
    data() {
      return {
        keyword: '',
        searchHistory: ['假如真有时光机', '格林童话', '大家都有病', '送你一颗子弹', '听说', '雷雨'],
        resultArray: [],
      }
    },
    
    methods: {
      // 关键字输入
      handleInput(e) {
        timer = setTimeout(() => {
          console.log('搜索', this.keyword)
        }, 500)
      },
      
      // 选择历史标签
      handleSelectTag(e) {
        this.keyword = e
        console.log('搜索', this.keyword)
      },
      
      // 跳转到详情
      gotoDetail(e) {
        console.log(e)
      }
    }
  }
</script>

<style lang="less">
  .search-wrap {
    // border: 1px solid green;
    position: relative;
  }
  
  .search-head {
    background-color: #fff;
    justify-content: space-between;
    padding: 0 40rpx;
    
    .search-input {
      width: 540rpx;
      height: 80rpx;
      border-radius: 40rpx;
      background-color: #eee;
      padding: 20rpx 24rpx;
      box-sizing: border-box;
      
      input {
        flex: 1;
        color: #333;
      }
    }
    
    .search-cancel {
      color: #888;
      font-size: 32rpx;
      padding: 16rpx 20rpx;
      border-radius: 64rpx;
      border: 2rpx solid #888;
    }
  }
  
  .result-wrap, .static-wrap {
    position: absolute;
    bottom: 0;
    top: 0;
    display: none;
    border: 1px solid blue;
    overflow: hidden;
    box-sizing: border-box;
    
    &.visible {
      display: block;
    }
  }
  
  .static-wrap {
    padding: 24rpx;
  }
</style>
