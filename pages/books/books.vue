<template>
	<view class="page-wrap">
    <view class="page-head flex-ajc">
      <view class="search-bar" @tap="showSearchPage">
        <image style="width: 28rpx; height: 28rpx; margin-right: 8rpx; position: relative; top: 2rpx;" src="../../static/images/icon/search.png" mode="aspectFit"></image>
        搜索图书名称
      </view>
    </view>
    <scroll-view scroll-y class="page-content book-list">
      <view class="content-head">
        <image src="../../static/images/book/quality.png" mode="aspectFit"></image>
      </view>
      <view class="content-main">
        <block v-for="item in books">
          <view class="book-item">
            <book
              :title="item.title"
              :author="item.author"
              :cover="item.cover"
              :like="item.like"
              :comment="item.comment">
            </book>
          </view>
        </block>
      </view>
    </scroll-view>
    <uni-popup type="bottom" ref="search">
      <view :style="{height: winHeight, width: winWidth, paddingBottom: winBottom, boxSizing: 'border-box'}">
        <search @cancel="hideSearchPage"></search>
      </view>
    </uni-popup>
	</view>
</template>

<script>
  import Book from '@/components/Book/Book.vue'
  import Search from '../search/search.vue'
  
	export default {
    components: {
      Book,
      Search
    },
    
		data() {
			return {
				books: [{
          id: '1',
          title: '程序员的数学之线性代数',
          cover: '/static/resource/books/book.jpg',
          author: '李李',
          like: 23,
          comment: 12
        }, {
          id: '2',
          title: '爱你就像爱生命',
          cover: '/static/resource/books/book1.jpg',
          author: '李银河',
          like: 68,
          comment: 23
        }],
        
        winWidth: 0,
        winHeight: 0,
        winBottom: 0
			}
		},
    
    onReady() {
      let res = uni.getSystemInfoSync()
      // console.log(res)
      // #ifdef MP-WEIXIN
      this.winHeight = res.windowHeight + 'px'
      // #endif
      // #ifdef H5
      this.winHeight = res.screenHeight + 'px'
      this.winBottom = res.windowBottom + 'px'
      // #endif
      this.winWidth = res.windowWidth + 'px'
    },
    
    onHide() {
      this.$refs.search.close()
    },
    
		methods: {
			showSearchPage() {
        // console.log('search', this.$refs.search)
        this.$refs.search.open()
      },
      
      hideSearchPage() {
        this.$refs.search.close()
      }
		}
	}
</script>

<style lang="less">
  .search-bar {
    width: 80%;
    height: 80rpx;
    line-height: 80rpx;
    text-align: center;
    border-radius: 40rpx;
    background-color: #eee;
    font-size: 32rpx;
    color: #999;
    letter-spacing: 4rpx;
  }
  
  .book-list {
    background-color: #eee;
  
    .content-head {
      margin: 40rpx;
      height: 40rpx;
      
      image {
        width: 100%;
        height: 100%;
      }
    }
    
    .content-main {
      display: flex;
      align-items: center;
      justify-content: space-evenly;
      flex-wrap: wrap;
      // padding: 0 40rpx;
      
      .book-item {
        margin-bottom: 64rpx;
      }
    }
  }
</style>
