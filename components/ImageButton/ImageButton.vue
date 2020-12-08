<template>
  <button class="image-btn" :open-type="openType" @getuserinfo="handleGetUserInfo" type="default">
    <image :src="imageSrc" mode="aspectFit"></image>
  </button>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		},
    
    props: {
      openType: {
        type: String,
        default: ''
      },
      
      imageSrc: {
        type: String,
        default: ''
      }
    },
    
    methods: {
      handleGetUserInfo(e) {
        // console.log('userInfo', e)
        if(this.openType) {
          this.$emit('userInfo', e.detail.userInfo)
        }
      }
    }
	}
</script>

<style lang="less">
  .image-btn {
    background-color: #FFFFFF;
    // border: 1px solid red;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 10rpx;
    
    image {
      width: 56rpx;
      height: 56rpx;
    }
    
    &::after {
      border: 0;
    }
  }
</style>
