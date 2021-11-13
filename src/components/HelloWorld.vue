<template>
  <view class="container">
    <image class="logo" :src="useUser.avatar" @click="pageRouter"></image>
    <text class="title text-gray">{{ title }}</text>
  </view>
</template>

<script>
  import { mapGetters } from 'vuex'
  export default {
    name: 'HelloWorld',
    props: {
      title: {
        type: String,
        required: false,
        default: 'Hello World'
      },
      // 跳转路由的 name
      routerName: {
        type: String,
        required: false,
        default: ''
      }
    },
    computed: {
      ...mapGetters('user', ['useUser'])
    },
    methods: {
      /**
       * 路由跳转
       * @author Matrix<matrix.zyh@gmail.com>
       */
      pageRouter() {
        if (!this.routerName) {
          this.$u.toast('请指定路由跳转 name ！')
          return
        }
        this.$Router.push({ name: this.routerName })
      }
    }
  }
</script>

<style scoped>
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  .title {
    font-size: 32rpx;
    margin-top: 50rpx;
  }

  .logo {
    height: 200rpx;
    width: 200rpx;
    margin-top: 200rpx;
  }
</style>
