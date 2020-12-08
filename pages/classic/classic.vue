<template>
	<view class="page-wrap">
    <view class="page-content classic-wrap">
      <view class="content-head">
        <epsoide></epsoide>
        <view class="head-right">
          <like 
            :isLike="list[current].isLike" 
            :likeCount="list[current].likeCount"
            @likeChange="handleLikeChange">
          </like>
          <!-- #ifdef MP-WEIXIN -->
          <view style="margin-left: 40rpx;">
            <image-button imageSrc="/static/images/icon/share.png" ></image-button>
          </view>
          <!-- #endif -->
        </view>
      </view>
      <view class="content-main">
        <music 
          v-if="list[current].type === 'music'"
          :cover="list[current].cover"
          :music="list[current].music"
          :content="list[current].content">
        </music>
        <movie
          v-else
          :type="list[current].type"
          :cover="list[current].cover" 
          :content="list[current].content">
        </movie>
      </view>
      <view class="content-footer">
        <navi 
          :title="list[current].title"
          :isFirst="current === 0"
          :isLast="current === list.length-1"
          @change="handleNaviChange">
        </navi>
      </view>
    </view>
	</view>
</template>

<script>
  import Epsoide from '@/components/Epsoide/Epsoide.vue'
  import Like from '@/components/Like/Like.vue'
  import Navi from '@/components/Navi/Navi.vue'
  // #ifdef MP-WEIXIN
  import ImageButton from '@/components/ImageButton/ImageButton.vue'
  // #endif
  
  import Movie from './components/movie/movie.vue'
  import Music from './components/music/music.vue'
  
	export default {
    components: {
      // #ifdef MP-WEIXIN 
      ImageButton,
      // #endif
      Epsoide,
      Like,
      Movie,
      Navi,
      Music
    },
    
		data() {
			return {
				list: [
          {
            type: 'movie',
            cover: '/static/resource/movie/《饮食男女》@2x.png',
            title: '李安 《饮食男女》',
            content: '人生不能像做菜，把所有的料准备好才下锅。',
            likeCount: 30,
            isLike: false
          },{
            type: 'article',
            cover: '/static/resource/article/诗句.jpg',
            title: '北岛 《城门开》',
            content: '心上无垢，林间有风',
            likeCount: 21,
            isLike: true
          },{
            type: 'music',
            cover: '/static/resource/music/参商.png',
            title: '不才 《参商》',
            content: '谁念过 千字文章 秋收已冬藏',
            music: '',
            likeCount: 300,
            isLike: false
          }
        ],
        
        current: 0
			}
		},
		methods: {
			handleLikeChange(e) {
        
      },
      
      handleNaviChange(e) {
        // console.log(e)
        // console.log(this.current)
        if(e === 'next' && this.current < this.list.length - 1) {
          this.current ++
        } 
        if(e === 'prev' && this.current > 0) {
          this.current --
        }
      }
		}
	}
</script>

<style lang="less">
  .content-head {
    border-bottom: 1px solid #ddd;
    box-shadow: 0 2rpx 16rpx #ddd;
    flex-shrink: 0;
    display: flex;
    align-items: center;
    justify-content: space-between;
    box-sizing: border-box;
    padding-right: 20rpx;
    
    .head-right {
      display: flex;
      align-items: center;
    }
  }
  
  .classic-wrap {
    position: relative;
    // border: 1px solid red;
    
    .content-footer {
      position: absolute;
      left: 50%;
      bottom: 80rpx;
      transform: translateX(-50%);
      
      width: 80%;
      // border: 1px solid green;
      display: flex;
      align-items: center;
      justify-content: center;
    }
  }
  
  
</style>
