<template>
	  <view class="card-block">
	    <view class="card-title">{{title}}</view>
	    <view class="card-content">
        <slot>
          <block v-for="item in tags">
            <view class="tags" @click="$emit('selectTag', item)">{{item}}</view>
          </block>
        </slot>
	    </view>
	  </view>
</template>

<script>
	export default {
    props: {
      title: String,
      tags: Array
    }
    
	}
</script>

<style lang="less">
  .card-block {
  
    .card-title {
      border-left: 16rpx solid #333;
      padding-left: 32rpx;
      margin: 32rpx 16rpx 0;
      font-size: 32rpx;
    }
    
    .card-content {
      display: flex;
      justify-content: flex-start;
      flex-wrap: wrap;
      padding: 16rpx 0;
      
      .tags {
        background-color: #eee;
        font-size: 28rpx;
        padding: 8rpx 24rpx;
        margin: 16rpx;
        color: #999;
      }
    }
  }
</style>
