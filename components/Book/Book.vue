<template>
	<view class="book-wrap">
		<view class="book-cover">
      <image :src="cover" mode="widthFix"></image>
    </view>
    <view class="book-content">
      <view class="book-title">{{title}}</view>
      <view class="book-author">{{author}}</view>
      <view class="book-info">
        <text class="book-like">{{like}}喜欢</text>·
        <text class="book-comment">{{comment}}短评</text>
      </view>
    </view>
	</view>
</template>

<script>
	export default {
    props: {
      title: String,
      author: String,
      like: [String, Number],
      comment: [String, Number],
      cover: String
    }
	}
</script>

<style lang="less">
  .book-wrap {
    height: 400rpx;
    width: 280rpx;
    // border: 1px solid green;
    background-color: #fff;
    box-sizing: border-box;
    padding: 8rpx;
    border-radius: 8rpx;
    
    .book-cover {
      height: 240rpx;
      box-sizing: border-box;
      overflow: hidden;
      
      image {
        width: 100%;
        height: 100%;
      }
    }
    
    .book-content {
      color: #aaa;
      height: 160rpx;
      padding: 16rpx 8rpx;
      position: relative;
      box-sizing: border-box;
      
      .book-title {
        width: 100%;
        color: #666;
        font-size: 32rpx;
        overflow: hidden;
        white-space: nowrap;
        text-overflow: ellipsis;
      }
      
      .book-author {
        font-size: 24rpx;
      }
      
      .book-info {
        position: absolute;
        right: 8rpx;
        bottom: 16rpx;
        display: flex;
        justify-content: flex-end;
        align-items: center;
        font-size: 26rpx;
        
        .book-like {
          margin-right: 8rpx;
        }
        
        .book-comment {
          margin-left: 8rpx;
        }
      }
    }
  }
</style>
