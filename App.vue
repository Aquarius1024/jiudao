<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
  page {
    height: 100%;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }
  
  .page-wrap {
    height: 100%;
    box-sizing: border-box;
    /* border: 1px solid #007AFF; */
    flex-direction: column;
    display: flex;
    background-color: #fff;
  }
  
  .page-wrap .page-head {
    height: 128rpx;
    /* line-height: 128rpx; */
    box-sizing: border-box;
    /* border-bottom: 1px solid #ddd; */
    box-shadow: 0 2rpx 16rpx #ddd;
    flex-shrink: 0;
  }
  
  .page-wrap .page-content {
    flex: 1;
    /* border: 1px solid #333333; */
    box-sizing: border-box;
    overflow: hidden;
  }
  
  /* flex布局 */
  .flex-ajc, .flex-ac, .flex-jc {
    display: flex;
  }
  
  .flex-ajc, .flex-ac {
    align-items: center;
  }
  
  .flex-ajc, .flex-jc {
    justify-content: center;
  }
</style>
