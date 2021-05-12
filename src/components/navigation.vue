<template>
  <!--    导航栏    -->
  <nav class="navigation" v-bind:class="mode">
    <div class="nav-item active">
      <a href="" class="nav-link">
        <i class="nav-icon">
          <svg xmlns="http://www.w3.org/2000/svg" width="16px" height="16px" viewBox="0 0 24 24" fill="none"
               stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
               class="icon-svg">
            <path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"></path>
            <polyline
              points="9 22 9 12 15 12 15 22"></polyline>
          </svg>
        </i>
        <span class="text-style">首页</span>
      </a>
    </div>
    <div class="nav-item">
      <a href="" class="nav-link">
        <i class="nav-icon">
          <svg xmlns="http://www.w3.org/2000/svg" width="16px" height="16px" viewBox="0 0 24 24" fill="none"
               stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
               class="icon-svg">
            <path d="M12 20h9"></path>
            <path
              d="M16.5 3.5a2.121 2.121 0 0 1 3 3L7 19l-4 1 1-4L16.5 3.5z"></path>
          </svg>
        </i>
        <span class="text-style">随笔</span>
      </a>
    </div>
    <div class="nav-item">
      <a href="" class="nav-link">
        <i class="nav-icon">
          <svg xmlns="http://www.w3.org/2000/svg" width="16px" height="16px" viewBox="0 0 24 24" fill="none"
               stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
               class="icon-svg">
            <polyline points="22 12 16 12 14 15 10 15 8 12 2 12"></polyline>
            <path
              d="M5.45 5.11L2 12v6a2 2 0 0 0 2 2h16a2 2 0 0 0 2-2v-6l-3.45-6.89A2 2 0 0 0 16.76 4H7.24a2 2 0 0 0-1.79 1.11z"></path>
          </svg>
        </i>
        <span class="text-style">归档</span>
      </a>
    </div>
    <div class="nav-item">
      <a href="#" class="nav-link" v-on:click="openCategory">
        <i class="nav-icon">
          <font-awesome-icon class="icon-svg" v-bind:icon="iconMap.server"></font-awesome-icon>
        </i>
        <span class="text-style">分类</span>
        <i class="nav-arrow">
          <font-awesome-icon class="icon-angle" v-bind:icon="iconMap.angleDown"></font-awesome-icon>
        </i>
      </a>
    </div>
    <div class="nav-item">
      <a href="" class="nav-link">
        <i class="nav-icon">
          <svg xmlns="http://www.w3.org/2000/svg" width="16px" height="16px" viewBox="0 0 24 24" fill="none"
               stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
               class="icon-svg">
            <circle cx="12" cy="12" r="10"></circle>
            <line x1="12" y1="16" x2="12"
                  y2="12"></line>
            <line
              x1="12" y1="8" x2="12.01" y2="8"></line>
          </svg>
        </i>
        <span class="text-style">关于</span>
      </a>
    </div>
  </nav>
</template>

<script>
  let vm = null

  export default {
    name: 'navigation',
    props: ['mode'],
    data () {
      return {
        isOpen: true,
        iconMap: {
          server: 'server',
          angleUp: 'angle-up',
          angleRight: 'angle-right',
          angleDown: 'angle-down',
          angleLeft: 'angle-left',
          folder: 'folder-open'
        },
      }
    },
    created () {
      vm = this
    },
    methods: {
      openCategory: function () {
        vm.$data.isOpen = !vm.$data.isOpen
      }
    }
  }
</script>

<style scoped>
  /* navigation-start  */

  .navigation {

  }

  .navigation .nav-item {
    line-height: 30px;
    position: relative;
    color: #2f3342;
  }

  .navigation .nav-link {
    transition: transform .15s ease-out;
    display: block;
  }

  /*  箭头  */
  .navigation .icon-angle {
    font-size: 12px;
    color: #7f7f7f;
  }

  /*
    导航栏-顶部模式
  */
  .navigation.nav-header .nav-item {
    display: inline-block;
    margin-left: 15px;
  }

  .navigation.nav-header .nav-link:hover {
    margin-bottom: -2px;
    border-bottom: 2px solid #0074D9;
  }

  .navigation.nav-header .nav-item.active .nav-link {
    margin-bottom: -2px;
    border-bottom: 2px solid #46bd87;
  }

  /*
      导航栏-侧导航栏模式
   */
  .navigation.nav-sidebar {
    margin-top: 30px;
  }

  .navigation.nav-sidebar .nav-item {
    display: block;
    padding: 5px 0;
    cursor: pointer;
  }

  .navigation.nav-sidebar .nav-link:hover {
    transform: translateX(10px) scale(1.1);
  }

  .navigation.nav-sidebar .nav-item.active {
    color: #46bd87;
  }

  .navigation.nav-sidebar .nav-arrow {
    position: absolute;
    right: 110px;
  }
</style>
