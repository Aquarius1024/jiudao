<template>
	<view class="like-wrap">
    <view class="img-wrap" @click="handleChange">
      <image v-if="isLike" src="../../static/images/icon/like-filled@2x.png" mode="aspectFit"></image>
      <image v-else src="../../static/images/icon/like@2x.png" mode="aspectFit"></image>
    </view>
    <text class="like-text">{{likeCount}}</text>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				isLike: false,
        likeCount: 99
			};
		},
    
    methods: {
      handleChange() {
        if(this.isLike) {
          this.likeCount --
        } else {
          this.likeCount ++
        }
        this.isLike = !this.isLike
      }
    }
	}
</script>

<style lang="less">
  .like-wrap {
    display: flex;
    align-items: center;
    justify-content: center;
    border: 1px solid red;
    box-sizing: border-box;
    height: 64rpx;
    
    .img-wrap {
      width: 40rpx;
      flex-shrink: 0;
      border: 1px solid green;
      
      image {
        width: 36rpx;
        height: 32rpx;
        }
    }
    
    .like-text {
      font-size: 28rpx;
      color: #999;
      position: relative;
      top: -16rpx;
    }
    
  }
</style>
