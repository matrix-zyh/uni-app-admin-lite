<template>
  <view>
    <u-navbar :is-back="false" :title="headerTitle" :background="background" title-color="#fff" />

    <view class="page-content">
      <view class="u-page">
        <!-- 所有内容的容器 -->
        <hello-world title="开发者，您好！点我试一试" router-name="home-index" />
      </view>
    </view>

    <!-- 与包裹页面所有内容的元素u-page同级，且在它的下方 -->
    <u-tabbar :list="useRoutes" />
  </view>
</template>

<script>
  import HelloWorld from '@/components/HelloWorld.vue'
  import { mapGetters } from 'vuex'

  export default {
    components: { HelloWorld },
    data() {
      return {
        // 标题
        headerTitle: '',
        // 自定义 navBar 导航样式
        background: {
          'background-image': 'linear-gradient(45deg, rgb(90, 132, 244), rgb(137,111,236))'
        }
      }
    },
    computed: {
      ...mapGetters('user', ['useRoutes'])
    },
    onLoad() {
      this.headerTitle = this.$Route.meta.title
    }
  }
</script>

<style scoped>
  .page-content {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
</style>
