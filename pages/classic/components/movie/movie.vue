<template>
	<view class="movie-wrap">
    <view class="image-wrap">
      <image class="image-content" :src="cover" mode="widthFix"></image>
      <image v-if="type === 'movie'" class="image-tag" src="/static/resource/movie/电影。@2x.png" mode="heightFix"></image>
      <image v-if="type === 'article'" class="image-tag" src="/static/resource/movie/诗句.png" mode="heightFix"></image>
    </view>
    <view class="movie-content">
      {{content}}
    </view>
	</view>
</template>

<script>
	export default {
    props: {
      cover: {
        type: String,
        default: '',
      },
      content: {
        type: String,
        default: ''
      },
      type: {
        type: String,
        required: true
      }
    }
	}
</script>

<style lang="less">
  .movie-wrap {
    width: 100%;
    
    .image-wrap {
      position: relative;
      
      .image-content {
        width: 100%;
        box-sizing: border-box;
        height: 500rpx;
      }
      
      .image-tag {
        position: absolute;
        left: 40rpx;
        bottom: -72rpx;
        width: 48rpx;
        height: 140rpx;
        z-index: 100;
      }
    }
    
    .movie-content {
      margin-top: 140rpx;
      box-sizing: border-box;
      padding: 0 80rpx;
      line-height: 1.5;
      color: #333;
      display: flex;
      align-items: center;
      justify-content: center;
    }
  }
</style>
