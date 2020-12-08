<template>
	<view class="like-wrap">
    <view class="img-wrap" @click="handleChange">
      <image v-if="isLike" src="../../static/images/icon/like-filled@2x.png" mode="aspectFit"></image>
      <image v-else src="../../static/images/icon/like@2x.png" mode="aspectFit"></image>
    </view>
    <view class="like-text">{{tempLike}}</view>
	</view>
</template>

<script>
	export default {
    props: {
      isLike: {
        type: Boolean,
        default: false
      },
      likeCount: {
        type: Number,
        default: 0
      }
    },
    
    methods: {
      handleChange() {
        if(this.isLike) {
          // this.likeCount --
          this.$emit('likeChange', 'minus')
        } else {
          // this.likeCount ++
          this.$emit('likeChange', 'plus')
        }
        // this.isLike = !this.isLike
      }
    },
    
    computed: {
      tempLike() {
        if(this.likeCount < 10) {
          return `${this.likeCount}`
        } else if (this.likeCount < 100) {
          return `0${this.likeCount}`
        } else if (this.likeCount < 1000) {
          return this.likeCount
        } else if (this.likeCount < 10000) {
          let str = this.likeCount / 1000
          return `${str.toFixed(1)}k`
        } else {
          let str = this.likeCount / 10000
          return `${str.toFixed(1)}w`
        }
      }
    }
	}
</script>

<style lang="less">
  .like-wrap {
    display: flex;
    align-items: center;
    justify-content: center;
    // border: 1px solid red;
    box-sizing: border-box;
    height: 64rpx;
    
    .img-wrap {
      width: 40rpx;
      flex-shrink: 0;
      // border: 1px solid green;
      
      image {
        width: 36rpx;
        height: 32rpx;
      }
    }
    
    .like-text {
      top: -8rpx;
      color: #999;
      font-size: 28rpx;
      position: relative;
      align-self: flex-start;
    }
  }
</style>
