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
  }
  
  .page-wrap .page-content {
    flex: 1;
  }
</style>
