<template>
  <view class="my-container">
      <!-- 用户未登录时，显示登录组件 -->
      <my-login v-if="!token"></my-login>
      <!-- <my-userinfo></my-userinfo> -->
      <!-- 用户登录后，显示用户信息组件 -->
      <my-userinfo v-else></my-userinfo>
      <!-- <my-login v-else></my-login> -->
  </view>
</template>

<script>
  // 导入自己封装的 mixin 模块
  import badgeMix from '@/mixins/tabbar-badge.js'
  // 从 vuex 中按需导入 mapState 辅助函数
  import { mapState } from 'vuex'
  
  export default {
    // 将 badgeMix 混入到当前的页面中进行使用
    mixins: [badgeMix],
    computed: {
      // 2. 从 m_user 模块中导入需要的 token 字符串
      ...mapState('m_user', ['token']),
    },
    data() {
      return {

      };
    }
  }
</script>

<style lang="scss">
  .login-container {
    // 登录盒子的样式
    height: 750rpx;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background-color: #f8f8f8;
    position: relative;
    overflow: hidden;
  
    // 绘制登录盒子底部的半椭圆造型
    &::after {
      content: ' ';
      display: block;
      position: absolute;
      width: 100%;
      height: 40px;
      left: 0;
      bottom: 0;
      background-color: white;
      border-radius: 100%;
      transform: translateY(50%);
    }
  
    // 登录按钮的样式
    .btn-login {
      width: 90%;
      border-radius: 100px;
      margin: 15px 0;
      background-color: #c00000;
    }
  
    // 按钮下方提示消息的样式
    .tips-text {
      font-size: 12px;
      color: gray;
    }
  }

page,
.my-container {
  height: 100%;
}

</style>
