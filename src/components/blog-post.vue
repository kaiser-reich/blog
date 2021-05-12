<!--
    文字块组件
-->
<template>
  <!--  文章  -->
  <div class="single-post post-panel">
    <!--    文章图片    -->
    <div class="post-image-box">
      <a href="#">
        <div class="post-image" v-bind:style="getImage(image)"></div>
      </a>
    </div>
    <!--    文章   -->
    <div class="post-meta">
      <!--    文章标题    -->
      <h2 class="post-title text-ellipsis">
        <a href="#">{{title}}</a>
      </h2>
      <!--    文章内容简介   -->
      <p class="post-content">{{value}}</p>
      <!--     分割线    -->
      <div class="line line-lg"></div>
      <!--    文章信息   -->
      <div class="post-info">
        <!--    文章作者    -->
        <li class="post-info-item">
          <svg xmlns="http://www.w3.org/2000/svg" width="14px" height="14px" viewBox="0 0 24 24" fill="none"
               stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
               class="post-info-icon">
            <path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"></path>
            <circle cx="12" cy="7" r="4"></circle>
          </svg>
          <span class="post-info-value">Kaiserreich</span>
        </li>
        <!--    文章发布时间    -->
        <li class="post-info-item">
          <svg xmlns="http://www.w3.org/2000/svg" width="14px" height="14px" viewBox="0 0 24 24" fill="none"
               stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
               class="post-info-icon">
            <circle cx="12" cy="12" r="10"></circle>
            <polyline points="12 6 12 12 16 14"></polyline>
          </svg>
          <span class="post-info-value">2021 年 03 月 14 日</span>
        </li>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'blog-post',
    props: ['title', 'value', 'image'],
    data () {
      return {}
    },
    return: {},
    created () {
      console.log(this.getImage('asd'))
    },
    methods: {
      getImage: function (image) {
        return image ? 'background-image: url("' + image + '")' : ''
      }
    }
  }
</script>

<style scoped>
  /*  文章  */
  .post-panel {
    background: #ffffff;
    border-radius: 6px !important;
    box-shadow: 0 20px 40px -15px rgba(0, 0, 0, .05) !important;
    -webkit-box-shadow: 0 20px 40px -15px rgba(0, 0, 0, .05) !important;

    margin-bottom: 20px;
  }

  /*  文章图片  */
  .post-image {
    background-image: url('../assets/image/blog-post.jpg');
    min-height: 350px;
    position: relative;
    display: block;
    background-position: 50% 50%;
    background-size: cover;
    border-top-left-radius: 6px;
    border-top-right-radius: 6px;
  }

  /*  文章简介  */
  .post-meta {
    padding: 30px;
  }

  .post-title {
    margin-top: 0;
  }

  .post-content {
    color: #a0a0a0;
    line-height: 24px;
  }

  /*  文章信息  */
  .post-info-item {
    color: #777;
    font-size: 14px;
  }

  .post-info > li {
    display: inline-block;
    padding-right: 10px;
  }

  .post-info-icon {
    vertical-align: -2px;
  }

  .line {
    width: 100%;
    height: 1px;
    margin: 15px 0;
    overflow: hidden;
  }

  .line-lg {
    background: rgba(222, 222, 222, .5);
  }
</style>


