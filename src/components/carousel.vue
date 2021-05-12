<!--
    轮播图组件
-->
<template>
  <div id="carousel" class="carousel">
    <!--    轮播图面板   -->
    <div class="carousel-panel">
      <div class="carousel-list">
        <div class="carousel-item" v-for="(item, $index) in carouselList" v-bind:style="getImage(item.image)"
             v-show="!$index"></div>
      </div>
      <!--    图片遮罩层   -->
      <div class="carousel-shadow"></div>
      <!--    图片遮罩层   -->
      <div class="carousel-info">
        <!--      文章标题    -->
        <h1 class="carousel-title">
          <a href="#">{{carouselList[lastIndex].title}}</a>
        </h1>
        <!--      点击阅读  -->
        <div class="carousel-read">
          <a href="#">点击阅读</a>
        </div>
      </div>
    </div>
    <!--    轮播控制   -->
    <div class="carousel-control">
        <span class="control-item" v-for="(item,$index) in carouselList" v-on:click="clickButton($index)"
              v-bind:class="[$index === 0 ? 'active' : '']">
          <svg t="1617087208000" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg"
               p-id="5973" width="24" height="24" fill="none"><path
            d="M418.048 950.08c-48.704-28.864-83.584-79.616-85.568-139.328C329.6 699.2 407.104 644.48 452.992 569.728c65.664-107.52 47.744-174.208 47.744-174.208S555.52 426.368 587.392 540.864c9.92 33.856 11.968 67.776 8.96 99.648-4.928 80.64-39.808 153.28-39.808 153.28s60.736-12.928 77.632-123.456c27.968 28.864 53.824 70.656 56.768 114.496 4.992 75.712-39.744 145.344-107.52 175.168 117.312-26.88 201.152-126.4 230.016-199.104 36.8-91.52 26.88-173.184 20.864-243.904-7.936-96.512 25.856-168.256 25.856-168.256s-64.704 18.944-112.512 97.536C725.76 482.176 716.8 534.848 716.8 534.848s4.992-46.72-25.92-132.352c-30.784-83.648-58.752-113.472-75.712-175.168C593.344 144.64 642.048 64 642.048 64S449.024 99.904 361.344 268.096C283.712 417.408 315.584 507.072 315.584 507.072S282.688 476.16 265.792 433.344 252.672 351.744 252.672 351.744 115.456 503.04 182.208 693.248C227.008 826.624 313.536 914.24 418.048 950.08z"
            p-id="5974"></path></svg>
        </span>
    </div>
  </div>
</template>

<script>
  let vm = null

  export default {
    name: 'carousel',
    data () {
      return {
        lastIndex: 0, //记录上张图片的位置
        isScroll: false, //是否在滚动
        MAX_CAROUSEL: 3,  //最大轮播数
        $controlItem: document.getElementsByClassName('control-item'),
        $carouselItem: document.getElementsByClassName('carousel-item'),
        carouselList: [
          {
            title: '你们轻轻唱，听完我就走。',
            image: require('../assets/image/blog-post-0.jpg')
          },
          {
            title: '你们轻轻唱，听完我就走11。',
            image: require('../assets/image/blog-post-1.jpg')
          },
          {
            title: '你们轻轻唱，听完我就走22。',
            image: require('../assets/image/blog-post-2.jpg')
          },
        ],  //轮播列表
      }
    },
    created () {
      vm = this
      console.log()
    },
    methods: {
      clickButton: function (index) {
        // console.log(index)
        if (vm.$data.lastIndex === index || vm.$data.isScroll) {
          return
        }

        for (let i = 0; i < vm.$data.MAX_CAROUSEL; i++) {
          if (i === index) {
            vm.$data.$controlItem[i].className = 'control-item active'
            vm.$data.$carouselItem[i].style.display = 'block'
          } else {
            vm.$data.$controlItem[i].className = 'control-item'

            vm.$data.isScroll = true
            vm.$data.timer = setTimeout(function () {
              vm.$data.isScroll = false
              vm.$data.$carouselItem[i].style.display = 'none'
            }, 480)
          }
        }

        if (index > vm.$data.lastIndex) {
          vm.$data.$carouselItem[index].className = 'carousel-item carousel-transition-right-in'
          vm.$data.$carouselItem[vm.$data.lastIndex].className = 'carousel-item carousel-transition-left-out'
        } else {
          vm.$data.$carouselItem[index].className = 'carousel-item carousel-transition-left-in'
          vm.$data.$carouselItem[vm.$data.lastIndex].className = 'carousel-item carousel-transition-right-out'
        }

        vm.$data.lastIndex = index
      },
      getImage: function (image) {
        return image ? 'background-image: url("' + image + '")' : ''
      }
    }
  }
</script>

<style scoped>

  .carousel {
    width: 1050px;
    height: 800px;
    overflow: hidden;
    margin: 70px auto;
    border-radius: 10px;
    position: relative;
  }

  /*  轮播图*/
  .carousel-panel, .carousel-list {
    width: 100%;
    height: 100%;
  }

  .carousel-panel:hover .carousel-item {
    transform: scale(1.05);
  }

  .carousel-shadow {
    width: 100%;
    height: 50%;
    position: absolute;
    bottom: 0;
    background: linear-gradient(180deg, rgba(49, 49, 48, 0), rgba(22, 29, 39, .9));
  }

  .carousel-item {
    width: 100%;
    height: 100%;
    background: url("../assets/image/blog-post-0.jpg") center no-repeat;
    background-size: cover;
    position: absolute;
    transition: all .45s ease-in-out;
  }

  .carousel-item.carousel-transition-left-in {
    animation: .5s carousel-transition-left-in ease-out;
  }

  .carousel-item.carousel-transition-left-out {
    animation: .5s carousel-transition-left-out ease-in;
  }

  .carousel-item.carousel-transition-right-in {
    animation: .5s carousel-transition-right-in ease-in-out;
  }

  .carousel-item.carousel-transition-right-out {
    animation: .5s carousel-transition-right-out ease-in-out;
  }

  .carousel-item:nth-child(1) {
    background: url("../assets/image/blog-post-1.jpg") center no-repeat;
    background-size: cover;
  }

  .carousel-item:nth-child(2) {
    background: url("../assets/image/blog-post-2.jpg") center no-repeat;
    background-size: cover;
  }

  /*  轮播遮罩  */
  .carousel-info {
    width: 100%;
    height: 50%;
    position: absolute;
    bottom: 0;
  }

  /*  文章标题  */
  .carousel-title {
    text-indent: 50px;
    margin-top: 200px;
  }

  .carousel-title > a {
    color: #ffffff;
    font-weight: bold;
  }

  /*  进行阅读  */
  .carousel-read {
    width: 100px;
    height: 35px;
    border-radius: 40px;
    text-align: center;
    line-height: 35px;
    background: #c20c0c;
    margin-left: 50px;
    opacity: .8;
    transition: .2s opacity linear;
  }

  .carousel-read:hover {
    opacity: 1;
  }

  .carousel-read > a {
    width: 100%;
    height: 100%;
    color: #ffffff;
    font-size: 14px;
    display: block;
  }

  /*  轮播控件  */
  .carousel-control {
    width: 100%;
    height: 80px;
    position: absolute;
    bottom: 0;
    text-align: center;
  }

  .control-item {
    width: 30px;
    height: 30px;
    border-radius: 50%;
    display: inline-block;
    margin-right: 15px;
    margin-top: 25px;
    cursor: pointer;
  }

  .control-item > svg {
    margin: 2px;
    fill: rgb(144, 145, 148);
  }

  .control-item > svg:hover {
    fill: rgb(196, 197, 200);
  }

  .control-item.active > svg {
    fill: #c20c0c;
    transform: scale(1.4);
    transition: .3s all ease-in-out;
  }

  /*  轮播切换动画  */
  @keyframes carousel-transition-left-in {
    0% {
      transform: translateX(-100%);
    }
    100% {
      transform: translateX(0);
    }
  }

  @-webkit-keyframes carousel-transition-left-in {
    0% {
      transform: translateX(-100%);
    }
    100% {
      transform: translateX(0);
    }
  }

  @keyframes carousel-transition-left-out {
    0% {
      transform: translateX(0);
    }
    100% {
      transform: translateX(-100%);
    }
  }

  @-webkit-keyframes carousel-transition-left-out {
    0% {
      transform: translateX(0);
    }
    100% {
      transform: translateX(-100%);
    }
  }

  @keyframes carousel-transition-right-in {
    0% {
      transform: translateX(100%);
    }
    100% {
      transform: translateX(0);
    }
  }

  @-webkit-keyframes carousel-transition-right-in {
    0% {
      transform: translateX(100%);
    }
    100% {
      transform: translateX(0);
    }
  }

  @keyframes carousel-transition-right-out {
    0% {
      transform: translateX(0);
    }
    100% {
      transform: translateX(100%);
    }
  }

  @-webkit-keyframes carousel-transition-right-out {
    0% {
      transform: translateX(0);
    }
    100% {
      transform: translateX(100%);
    }
  }
</style>
