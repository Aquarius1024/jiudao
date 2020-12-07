<template>
	<view class="page-wrap">
    <view class="page-content">
      <view class="content-head">
        <epsoide></epsoide>
        <view>
          <like></like>
        </view>
      </view>
    </view>
	</view>
</template>

<script>
  import Epsoide from '@/components/Epsoide/Epsoide.vue'
  import Like from '@/components/like/like.vue'
  
	export default {
    components: {
      Epsoide,
      Like
    },
    
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style>
  .content-head {
    border-bottom: 1px solid #ddd;
    flex-shrink: 0;
    display: flex;
    align-items: center;
    justify-content: space-between;
    box-sizing: border-box;
    padding-right: 20rpx;
  }
</style>
