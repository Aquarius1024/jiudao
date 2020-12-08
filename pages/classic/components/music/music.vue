<template>
	<view class="music-wrap">
    <view class="image-wrap">
      <view class="music-btn">
        <image :class="{animation: start}" class="image-content" :src="cover" mode="aspectFit"></image>
        <view class="btn" @click="handleStart" >
          <image :style="{opacity: start? 0: 1}" src="../../../../static/resource/music/暂停中.png" mode="aspectFit"></image>
          <image :style="{opacity: start? 1: 0}"  src="../../../../static/resource/music/播放中.png" mode="aspectFit"></image>
        </view>
      </view>
      <image class="image-tag" src="/static/resource/music/音乐。@2x.png" mode="heightFix"></image>
    </view>
    <view class="music-content" :style="{textAlign: content.length>15 ? 'left' : 'center'}">
      {{content}}
    </view>
	</view>
</template>

<script>
	export default {
    data() {
      return {
        start: false
      }
    },
    
    props: {
      cover: {
        type: String,
        default: '',
      },
      content: {
        type: String,
        default: ''
      }
    },
    
    methods: {
      handleStart() {
        this.start = !this.start
      }
    }
	}
</script>

<style lang="less">
  @keyframes loop {
    0% {
      transform: rotate(0deg);
    }
    25% {
      transform: rotate(90deg);
    }
    50% {
      transform: rotate(180deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }
  
  .music-wrap {
    width: 100%;
    
    .image-wrap {
      position: relative;
      height: 500rpx;
      display: flex;
      align-items: center;
      justify-content: center;
      
      .image-tag {
        position: absolute;
        left: 40rpx;
        bottom: -80rpx;
        width: 48rpx;
        height: 140rpx;
        z-index: 100;
      }
        
      .music-btn {
        width: 400rpx;
        height: 400rpx;
        border-radius: 100%;
        overflow: hidden;
        display: flex;
        align-items: center;
        justify-content: center;
        position: relative;
        
          
        .image-content {
          width: 100%;
          height: 100%;
          box-sizing: border-box;
          
          &.animation {
            animation: loop 8s linear infinite;
          }
        }
        
        .btn {
          position: absolute;
          width: 200rpx;
          height: 200rpx;
          z-index: 99;
          
          image {
            position: absolute;
            width: 100%;
            height: 100%;
          }
        }
      }
    }
    
    .music-content {
      margin-top: 140rpx;
      box-sizing: border-box;
      padding: 0 80rpx;
      line-height: 1.5;
      color: #333;
    }
  }
</style>
