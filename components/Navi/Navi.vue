<template>
	<view class="navi-wrap">
		<image-button @click.native="handleClick('prev')" imageSrc="/static/images/icon/prev@2x.png"></image-button>
    <view class="navi-title">{{title}}</view>
		<image-button @click.native="handleClick('next')" imageSrc="/static/images/icon/next@2x.png"></image-button>
	</view>
</template>

<script>
  import ImageButton from '../ImageButton/ImageButton.vue'
	export default {
    components: {
      ImageButton
    },
    
    props: {
      isFirst: {
        type: Boolean,
        default: true
      }, 
      
      isLast: {
        type: Boolean,
        default: false
      },
      
      title: {
        type: String,
        default: ''
      }
    },
    
    methods: {
      handleClick(type) {
        // console.log(type)
        this.$emit('change', type)
      }
    }
	}
</script>

<style lang="less">
  .navi-wrap {
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    // border: 1px solid #ddd;
    border-radius: 8rpx;
    box-shadow: 0 0 8rpx #ccc;
    background-color: #fff;
    
    .navi-title {
      width: 80%;
      text-align: center;
      color: #333;
      font-size: 32rpx;
    }
  }
</style>
