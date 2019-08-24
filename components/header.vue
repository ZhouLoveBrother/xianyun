<template>
  <div class="container">
    <el-row type="flex" class="main" justify="space-between">
      <!-- logo -->
      <div class="logo">
        <nuxt-link to="/">
          <img src="http://157.122.54.189:9093/images/logo.jpg" alt />
        </nuxt-link>
      </div>
      <!-- 导航栏 -->
      <el-row type="flex" class="nav">
        <nuxt-link to="/">首页</nuxt-link>
        <nuxt-link to="/post">旅游攻略</nuxt-link>
        <nuxt-link to="/hotel">酒店</nuxt-link>
        <nuxt-link to="/air">国内机票</nuxt-link>
      </el-row>
      <!-- 登录注册 -->
      <div class="user">
        <span>消息</span>
        <nuxt-link to="/post">登录</nuxt-link>
        <i>/</i>
        <nuxt-link to="/post">注册</nuxt-link>
      </div>
    </el-row>
  </div>
</template>

<script>
export default {};
</script>

<style lang="less" scoped>
.container {
  height: 60px;
  box-shadow: 0 3px 3px #ccc;
  position: relative;
  .main {
    width: 1000px;
    margin: 0 auto;
    line-height: 60px;

    .logo {
      img {
        width: 165px;
        height: 42px;
        margin-top: 9px;
      }
    }
    .nav {
      flex: 1;
      a {
        padding: 0 20px;
        height: 60px;
        display: block;
        box-sizing: border-box;
        &:hover {
          border-bottom: 5px #409eff solid;
          color: #409eff;
        }
      }

      .nuxt-link-exact-active {
        background-color: #409eff;
        color: #fff;
        &:hover {
          color: #fff;
        }
      }
    }
  }
}
</style>
