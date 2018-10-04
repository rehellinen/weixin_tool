<template>
  <div class="icon-container">
    <div @click="checkToken">
      <p>test Token</p>
    </div>
  </div>
</template>

<script>
  const baseUrl = `https://20298479.rehellinen.cn/dingdang/public/api/v1`
  export default {
    methods: {
      checkToken () {
        wx.login({
          success (res) {
            wx.request({
              url: `${baseUrl}/token`,
              data: {
                code: res.code
              },
              success (res) {
                console.log(res)
              }
            })
          }
        })
      }
    }
  }
</script>

<style scoped>
  .icon-container{
    display: flex;
    flex-direction: column;
    align-items: center;
    min-height: 100vh;
    padding-top: 50rpx;
  }

  .icon-container div{
    display: flex;
    align-items: center;
    justify-content: center;
    width: 85%;
    background-color: aqua;
    border-radius: 10rpx;
    height: 80rpx;
    color: white;
  }
</style>
