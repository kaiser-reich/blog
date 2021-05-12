<!--
    侧边栏组件
-->
<template>
  <aside class="sidebar">
    <div class="sidebar-panel">
      <div class="sidebar-info">
        <!--    作者头像     -->
        <a class="author-avatar">
          <img src="../assets/image/head.jpg" alt="布拉格的玻璃">
        </a>
        <!--    作者名字    -->
        <a class="author-name">布拉格的玻璃</a>
        <!--    站点名字    -->
        <a class="site-name">布拉格的玻璃的小站</a>
        <!--     个性签名   -->
        <sub class="author-subtitle">No Game No Life!</sub>
        <!--     个人简介   -->
        <div class="author-description">我们赢得了一代人的和平</div>
      </div>
      <navigation></navigation>
    </div>
  </aside>
</template>

<script>
  import navigation from './navigation'

  export default {
    name: 'sidebar',
    components: {
      'navigation': navigation
    },
  }
</script>

<style scoped>
  .sidebar {
    width: 320px;
    height: 100%;
    position: fixed;
    z-index: 9;
    top: 0;
    left: 0;
    box-shadow: 0 0 3px rgba(0, 0, 0, .2);
    transition: .2s all ease-in-out;
    background-color: #ffffff;
    background-image: url("../assets/image/bg-sidebar.jpg");
    background-position: bottom -60px center;
    background-size: contain;
    background-repeat: no-repeat;
  }

  .sidebar-panel {
    text-align: center;
    padding: 30px 10px;
  }

  .sidebar:hover {
    box-shadow: 0 0 15px rgba(0, 0, 0, .2);
  }

  /*  站长信息  */
  .sidebar-info {

  }

  /*  头像  */
  .author-avatar {
    width: 100px;
    height: 100px;
    display: inline-block;
  }

  .author-avatar > img {
    width: 92px;
    height: 92px;
    border-radius: 50%;
    padding: 4px;
    background: #ffffff;
    box-shadow: 0 0 10px rgba(0, 0, 0, .2);
    transition: .4s;
  }

  .author-avatar > img:hover {
    box-shadow: 0 0 30px rgba(0, 120, 231, .2);
  }

  /*  作者名字  */
  .author-name {
    display: block;
    margin-top: 10px;
    color: #2f3342;
    transition: .1s color;
  }

  .author-name:hover {
    color: #1f4f89;
  }

  .site-name {
    display: block;
    font-weight: bold;
    margin-top: 20px;
    transition: .1s color;
  }

  .site-name:hover {
    color: #C21F39;
  }

  .author-subtitle {
    display: block;
    margin-top: 10px;
    color: #7f7f7f;
  }

  .author-description {
    margin-top: 10px;
  }
</style>
