<template>
  <div id="app">
    <!--    APP加载条  -->
    <div class="loading-app">
      <div class="loading-app-panel">
        <div class="square-move">
          <i class="move-item"></i>
          <i class="move-item"></i>
          <i class="move-item"></i>
        </div>
        <div class="loading-saying">我们赢得了一代人的和平 --- 内维尔`张伯伦</div>
      </div>
    </div>
    <!--    加载条    -->
    <div id="loading" class="loading">
      <div class="loading-bar"></div>
    </div>
    <!--    返回顶部按钮   -->
    <a class="button-go-up show" id="goUp" href="javascript:void (0)" v-on:click="goTop">
      <font-awesome-icon v-bind:icon="iconMap.arrowUp" class="icon-go-up"></font-awesome-icon>
    </a>

    <!--  头部导航  -->
    <header class="header header-transparent">S
      <!--    LOGO  -->
      <div class="header-logo" v-on:click="isOpenSideBar = !isOpenSideBar"></div>
      <!--    功能区   -->
      <div class="header-links">
        <div class="header-theme">
            <span class="theme-item theme-moon">
              <svg t="1617075060438" class="icon" viewBox="0 0 1024 1024" version="1.1"
                   xmlns="http://www.w3.org/2000/svg"
                   p-id="3722" width="20" height="20" fill="#888"><path
                d="M524.8 938.666667h-4.266667a439.893333 439.893333 0 0 1-313.173333-134.4 446.293333 446.293333 0 0 1-11.093333-597.333334 432.213333 432.213333 0 0 1 170.666666-116.906666 42.666667 42.666667 0 0 1 45.226667 9.386666 42.666667 42.666667 0 0 1 10.24 42.666667 358.4 358.4 0 0 0 82.773333 375.893333 361.386667 361.386667 0 0 0 376.746667 82.773334 42.666667 42.666667 0 0 1 54.186667 55.04A433.493333 433.493333 0 0 1 836.266667 810.666667a438.613333 438.613333 0 0 1-311.466667 128z"
                p-id="3723"></path></svg>
            </span>
          <span CLASS="theme-item theme-sun hide">
              <svg t="1617075132486" class="icon" viewBox="0 0 1024 1024" version="1.1"
                   xmlns="http://www.w3.org/2000/svg"
                   p-id="4537" width="20" height="20" fill="#999"><path
                d="M512 61.44c13.312 0 25.25184 7.63904 29.94176 19.16928l27.56608 67.97312c11.91936 29.34784-4.17792 62.07488-35.9424 73.09312A65.9456 65.9456 0 0 1 512 225.28c-33.93536 0-61.44-25.41568-61.44-56.77056 0-6.79936 1.3312-13.55776 3.91168-19.92704l27.58656-67.97312C486.72768 69.07904 498.64704 61.44 512 61.44z m0 901.12c-13.33248 0-25.27232-7.63904-29.94176-19.16928l-27.58656-67.97312a52.96128 52.96128 0 0 1-3.91168-19.92704C450.56 824.15616 478.06464 798.72 512 798.72c7.3728 0 14.66368 1.2288 21.56544 3.60448 31.76448 11.01824 47.86176 43.74528 35.9424 73.1136l-27.56608 67.95264c-4.68992 11.53024-16.62976 19.16928-29.94176 19.16928z m450.56-450.56c0 13.312-7.63904 25.25184-19.16928 29.94176l-67.97312 27.56608c-29.34784 11.91936-62.07488-4.17792-73.09312-35.9424A65.9456 65.9456 0 0 1 798.72 512c0-33.93536 25.41568-61.44 56.77056-61.44 6.79936 0 13.55776 1.3312 19.92704 3.91168l67.97312 27.58656c11.53024 4.66944 19.16928 16.5888 19.16928 29.94176zM61.44 512c0-13.33248 7.63904-25.27232 19.16928-29.94176l67.97312-27.58656c6.3488-2.58048 13.1072-3.91168 19.92704-3.91168C199.84384 450.56 225.28 478.06464 225.28 512c0 7.3728-1.2288 14.66368-3.60448 21.56544-11.01824 31.76448-43.74528 47.86176-73.1136 35.9424l-67.95264-27.56608C69.07904 537.25184 61.44 525.312 61.44 512zM193.39264 193.41312c9.4208-9.4208 23.26528-12.45184 34.73408-7.61856l67.56352 28.54912c29.184 12.34944 40.93952 46.85824 26.25536 77.1072a65.9456 65.9456 0 0 1-12.6976 17.8176c-23.98208 23.98208-61.39904 25.45664-83.5584 3.2768a52.96128 52.96128 0 0 1-11.34592-16.85504L185.79456 228.1472c-4.85376-11.4688-1.82272-25.31328 7.59808-34.73408z m637.19424 637.19424c-9.4208 9.4208-23.26528 12.45184-34.73408 7.59808l-67.54304-28.54912a52.96128 52.96128 0 0 1-16.87552-11.32544c-22.15936-22.17984-20.6848-59.5968 3.29728-83.57888a65.9456 65.9456 0 0 1 17.8176-12.6976c30.24896-14.68416 64.75776-2.92864 77.1072 26.25536l28.54912 67.56352c4.83328 11.4688 1.80224 25.2928-7.61856 34.73408z m0-637.21472c9.4208 9.4208 12.45184 23.26528 7.61856 34.73408l-28.54912 67.56352c-12.34944 29.184-46.85824 40.93952-77.1072 26.25536a65.9456 65.9456 0 0 1-17.8176-12.6976c-23.98208-23.98208-25.45664-61.39904-3.2768-83.5584 4.79232-4.83328 10.50624-8.66304 16.85504-11.34592l67.54304-28.54912c11.4688-4.85376 25.31328-1.82272 34.73408 7.59808zM193.39264 830.58688c-9.4208-9.4208-12.45184-23.26528-7.59808-34.73408l28.54912-67.54304c2.6624-6.3488 6.51264-12.06272 11.32544-16.87552 22.17984-22.15936 59.5968-20.6848 83.57888 3.29728 5.2224 5.2224 9.5232 11.264 12.6976 17.8176 14.68416 30.24896 2.92864 64.75776-26.25536 77.1072l-67.56352 28.54912c-11.4688 4.83328-25.2928 1.80224-34.73408-7.61856zM512 737.28c-124.416 0-225.28-100.864-225.28-225.28s100.864-225.28 225.28-225.28 225.28 100.864 225.28 225.28-100.864 225.28-225.28 225.28z"
                p-id="4538"></path></svg>
            </span>
        </div>
        <!--    搜索    -->
        <div class="header-search">
            <span class="icon-svg search-icon">
              <svg xmlns="http://www.w3.org/2000/svg" width="16px" height="16px" viewBox="0 0 24 24" fill="none"
                   stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                   class="feather feather-search"><circle cx="11" cy="11" r="8"></circle><line x1="21" y1="21"
                                                                                               x2="16.65"
                                                                                               y2="16.65"></line></svg>
            </span>
          <input class="search-input"/>
        </div>
        <!--    链接    -->
        <navigation v-bind:mode="'nav-header'"></navigation>
      </div>
    </header>

    <!--    侧边导航    -->
    <aside class="sidebar" v-bind:class="[isOpenSideBar ? 'active' : '']">
      <div class="sidebar-panel">
        <site-info></site-info>
        <navigation v-bind:mode="'nav-sidebar'"></navigation>
      </div>
    </aside>

    <!--    分类列表    -->
    <aside class="category-wrap">
      <category></category>
    </aside>

    <router-view/>
  </div>
</template>

<script>
  import SiteInfo from './components/site-info'
  import Navigation from './components/navigation'
  import Category from './components/category'

  let vm = null

  export default {
    components: {
      Category,
      Navigation,
      SiteInfo
    },
    data: function () {
      return {
        timer: null,
        isOpenSideBar: false,
        iconMap: {
          arrowUp: 'arrow-up'
        }
      }
    },
    created: function () {
      vm = this
    },
    methods: {
      //返回顶部
      goTop: function () {
        let v = 0 //速度
        let a = 10  //加速度

        vm.$data.timer = setInterval(function () {
          if (document.documentElement.scrollTop > 0) {
            v = document.documentElement.scrollTop / a
            document.documentElement.scrollTop = document.documentElement.scrollTop - v
          } else {
            clearInterval(vm.$data.timer)
          }
        }, 15)
      }
    },

    opensider: function () {

    }
  }
</script>

<style>
  /*
    全局样式
  */
  body, ul, li, a {
    margin: 0;
    padding: 0;
  }

  body {
    font-family: '幼圆', serif;
    scroll-behavior: smooth;
  }

  a {
    text-decoration: none;
    color: inherit;
    cursor: pointer;
    word-break: break-all;
  }

  li {
    list-style: none;
  }

  body .hide {
    display: none;
  }

  /*  字体溢出隐藏  */
  .text-ellipsis {
    display: block;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }

  .text-style {
    color: inherit;
    font-size: 14px;
  }

  .icon-svg {
    color: inherit;
    vertical-align: -2px;
    width: 14px;
    height: 14px;
  }

  .btn-default {
    text-align: center;
    cursor: pointer;
  }

  /*  滚动条样式  */
  body::-webkit-scrollbar {
    width: 5px;
  }

  body::-webkit-scrollbar-track {
    background: #eee;
    border-radius: 3px;
  }

  body::-webkit-scrollbar-thumb {
    background: #ccc;
    border-radius: 5px;
  }

  body::-webkit-scrollbar-thumb:hover {
    background: #c0c0c0;
  }

  body::-webkit-scrollbar-corner {
    background: #179a16;
  }

  /*  加载APP界面 */

  .loading-app {
    display: flex;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: #f0f3f4;
    z-index: 99;
    justify-content: center;
    align-items: center;
    display: none;
  }

  .loading-app-panel {

  }

  /*  APP加载动画  */
  .square-move {
    position: relative;
    width: 75px;
    height: 75px;
    margin: 0 auto;
  }

  .square-move .move-item {
    position: absolute;
    width: 20px;
    height: 20px;
    background-color: #41adef;
    border-radius: 3px;
    left: 0;
    top: 0;
  }

  .square-move .move-item:nth-child(2) {
    left: 25px;
    top: 0;
  }

  .square-move .move-item:nth-child(3) {
    left: 0;
    top: 25px;
  }

  .square-move.active .move-item:nth-child(1) {
    animation: a-move 2s infinite linear;
  }


  .square-move.active .move-item:nth-child(2) {
    animation: b-move 2s infinite linear;
  }


  .square-move.active .move-item:nth-child(3) {
    animation: c-move 2s infinite linear;
  }

  /*  名言警句  */

  .loading-saying {
    font-size: 26px;

  }

  /*  加载条  */
  .loading {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 2px;
    z-index: 999;
  }

  .loading-bar {
    position: absolute;
    width: 100%;
    height: 0;
    background-color: #23b7e5;
  }

  .loading.active {
    animation: changeBar 3s infinite 1s;
    -webkit-animation: changeBar 3s infinite 1s;
  }

  .loading.active .loading-bar {
    -webkit-animation: changeBar 3s infinite;
    -moz-animation: changeBar 3s infinite;
    animation: changeBar 3s infinite;
  }

  .loading .loading-bar:before {
    position: absolute;
    right: 50%;
    left: 50%;
    height: 2px;
    background-color: inherit;
    content: "";
  }

  .loading.active .loading-bar:before {
    -webkit-animation: moveBar 1s infinite;
    -moz-animation: moveBar 1s infinite;
    animation: moveBar 1s infinite;
  }

  /*  返回顶部  */
  .button-go-up {
    width: 40px;
    height: 40px;
    background: #fff;
    position: fixed;
    right: 20px;
    bottom: 20px;
    -webkit-box-shadow: 0 1px 3px rgba(0, 0, 0, .1);
    box-shadow: 0 1px 3px rgba(0, 0, 0, .1);
    border-radius: 50%;
  }

  .button-go-up:hover {
    background: #d4d4d4;
  }

  .icon-go-up {
    margin: 13px;
    color: #2f3342;
  }

  /**  头部导航  **/
  .header {
    width: 100%;
    height: 50px;
    position: fixed;
    top: 0;
    left: 0;
    background: #ffffff;
    z-index: 5;
    box-shadow: 0 1px 3px rgba(18, 18, 18, .1);
    -webkit-box-shadow: 0 1px 3px rgba(18, 18, 18, .1);
  }

  .header.header-transparent {
    background: transparent;
    box-shadow: none;
    color: #ffffff;
  }

  /*  LOGO  */
  .header-logo {
    width: 40px;
    height: 40px;
    background: url("./assets/image/head.jpg") center no-repeat;
    background-size: 100% 100%;
    margin: 5px 100px;
    border-radius: 50%;
  }

  .header-links {
    max-width: 1000px;
    height: 30px;
    position: absolute;
    display: flex;
    top: 10px;
    right: 40px;
  }

  /*  主题  */
  .header-theme {
    width: 20px;
    height: 20px;
    padding: 5px 15px;
    margin-right: 10px;
    cursor: pointer;
    border-radius: 5px;
    transition: .25s background-color ease-in-out;
  }

  .header-theme:hover {
    background: rgba(0, 0, 0, .05);
  }

  /*  搜索  */
  .header-search {
    width: 200px;
    height: 30px;
    position: relative;
    margin-right: 15px;
  }

  .search-icon {
    position: absolute;
    top: 7px;
    left: 10px;
  }

  .search-input {
    border: 1px solid #cfd4db;
    width: 160px;
    height: 28px;
    border-radius: 30px;
    outline: none;
    padding: 0 10px 0 30px;
    transition: .25s border ease-in-out;
    -webkit-transition: .25s border ease-in-out;
  }

  .search-input:focus {
    border: 1px solid #0074D9;
  }

  /*
    侧导航栏
  */
  .sidebar {
    width: 320px;
    height: 100%;
    position: fixed;
    z-index: 9;
    top: 0;
    left: -320px;
    box-shadow: 0 0 5px rgba(0, 0, 0, .2);
    background-color: #ffffff;
    background-image: url("./assets/image/bg-sidebar.jpg");
    background-position: bottom -100px center;
    background-size: contain;
    background-repeat: no-repeat;
    transition: .44s left ease-in-out;
  }

  .sidebar.active {
    left: 0;
  }

  .sidebar-panel {
    text-align: center;
    padding: 30px 10px;
  }

  .sidebar:hover {
    box-shadow: 0 0 15px rgba(0, 0, 0, .2);
  }

  /*  分类栏目列表  */
  .category-wrap {
    width: 250px;
    height: 100%;
    position: fixed;
    z-index: 8;
    top: 0;
    left: 315px;
    box-shadow: 0 0 5px rgba(0, 0, 0, .2);
    transition: .2s all ease-in-out;
    background-color: #ffffff;
    display: none;
  }


  .category-wrap:hover {
    box-shadow: 0 0 15px rgba(0, 0, 0, .2);
  }

  /*  TODO  */
  #app {
    min-height: 960px;
    background: #f4f4f4;
    display: flex;
  }

  /*  主题  */
  .theme--light {

  }

  /*
      全局动画-加载条
  */
  @keyframes changeBar {
    0% {
      background-color: #23b7e5;
    }
    33.3% {
      background-color: #23b7e5;
    }
    33.33% {
      background-color: #fad733;
    }
    66.6% {
      background-color: #fad733;
    }
    66.66% {
      background-color: #7266ba;
    }
    100% {
      background-color: #7266ba;
    }
  }

  @-webkit-keyframes changeBar {
    0% {
      background-color: #23b7e5;
    }
    33.3% {
      background-color: #23b7e5;
    }
    33.33% {
      background-color: #fad733;
    }
    66.6% {
      background-color: #fad733;
    }
    66.66% {
      background-color: #7266ba;
    }
    100% {
      background-color: #7266ba;
    }
  }

  @keyframes moveBar {
    0% {
      right: 50%;
      left: 50%
    }
    99.9% {
      right: 0;
      left: 0
    }
    100% {
      right: 50%;
      left: 50%
    }
  }

  @-webkit-keyframes moveBar {
    0% {
      right: 50%;
      left: 50%
    }
    99.9% {
      right: 0;
      left: 0
    }
    100% {
      right: 50%;
      left: 50%
    }
  }

  /*  APP加载动画  */
  @keyframes a-move {
    0% {
      left: 0;
      top: 0;
    }
    8% {
      left: 0;
      top: 0;
    }
    16% {
      left: 25px;
      top: 0;
    }
    24% {
      left: 25px;
      top: 0;
    }
    32% {
      left: 25px;
      top: 0;
    }
    40% {
      left: 25px;
      top: 25px;
    }
    48% {
      left: 25px;
      top: 25px;
    }
    56% {
      left: 25px;
      top: 25px;
    }
    64% {
      left: 0;
      top: 25px;
    }
    72% {
      left: 0;
      top: 25px;
    }
    80% {
      left: 0;
      top: 25px;
    }
    88% {
      left: 0;
      top: 0;
    }
    100% {
      left: 0;
      top: 0;
    }
  }

  @keyframes b-move {
    0% {
      left: 25px;
      top: 0;
    }
    8% {
      left: 25px;
      top: 25px;
    }
    16% {
      left: 25px;
      top: 25px;
    }
    24% {
      left: 25px;
      top: 25px;
    }
    32% {
      left: 0;
      top: 25px;
    }
    40% {
      left: 0;
      top: 25px;
    }
    48% {
      left: 0;
      top: 25px;
    }
    56% {
      left: 0;
      top: 0;
    }
    64% {
      left: 0;
      top: 0;
    }
    72% {
      left: 0;
      top: 0;
    }
    80% {
      left: 25px;
      top: 0;
    }
    88% {
      left: 25px;
      top: 0;
    }
    100% {
      left: 25px;
      top: 0;
    }
  }

  @keyframes c-move {
    0% {
      left: 0;
      top: 25px;
    }
    8% {
      left: 0;
      top: 25px;
    }
    16% {
      left: 0;
      top: 25px;
    }
    24% {
      left: 0;
      top: 0;
    }
    32% {
      left: 0;
      top: 0;
    }
    40% {
      left: 0;
      top: 0;
    }
    48% {
      left: 25px;
      top: 0;
    }
    56% {
      left: 25px;
      top: 0;
    }
    64% {
      left: 25px;
      top: 0;
    }
    72% {
      left: 25px;
      top: 25px;
    }
    80% {
      left: 25px;
      top: 25px;
    }
    88% {
      left: 25px;
      top: 25px;
    }
    100% {
      left: 0;
      top: 25px;
    }
  }

</style>
