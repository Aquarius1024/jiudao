<template>
	<view class="epsoide-wrap">
		<view class="epsoide-index">
      NO.<text class="index">{{tempIndex}}</text>
    </view>
    <view class="epsoide-date">
      <view class="month">{{month}}</view>
      <view class="year">{{year}}</view>
    </view>
	</view>
</template>

<script>
	export default {
    name: 'epsoide',
    
		data() {
			return {
        month: '三月',
        year: '2018',
        months:[
          '一月','二月','三月','四月','五月','六月','七月','八月','九月','十月','十一月',
          '十二月'
        ],
			};
		},
    
    props: {
      index: {
        type: Number,
        default: 2
      }
    },
    
    computed: {
      tempIndex() {
        if(this.index < 10) {
          return `0${this.index}`
        } else {
          return this.index
        }
      },
    }
	}
</script>

<style lang="less">
  .epsoide-wrap {
    // width: 220rpx;
    display: flex; 
    align-items: flex-end;
    line-height: 1;
    padding: 24rpx;
    
    .epsoide-index {
      font-size: 34rpx;
      box-sizing: border-box;
      // border-right: 4rpx solid #333333;
      
      .index {
        font-size: 64rpx;
        font-weight: 600;
      }
      
      &::after {
        content: '';
        display: inline-block;
        height: 48rpx;
        width: 0;
        border: 2rpx solid #333;
        margin: 0 12rpx;
      }
    }
    
    .epsoide-date {
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      padding-bottom: 4rpx;
      
      .month {
        font-size: 30rpx;
      }
      
      .year {
        font-size: 28rpx;
      }
    }
  }
</style>
