<template>
  <div class="home-page">
    <rich-text></rich-text>
    <sidebar></sidebar>
    <tag></tag>
        <navigation></navigation>
<!--    <category></category>-->
    <timeline></timeline>
    <carousel></carousel>
    <div class="post-list">
      <blog-post v-for="item in list" v-bind:title="item.title" v-bind:value="item.value"
                 v-bind:image="item.image"></blog-post>
    </div>
  </div>
</template>

<script>
  import blogPost from '../components/blog-post'
  import navigation from '../components/navigation'
  import carousel from '../components/carousel'
  import timeline from '../components/timeline'
  import tag from '../components/tag'
  import sidebar from '../components/sidebar'
  import category from '../components/category'
  import RichText from '../components/rich-text'

  export default {
    name: 'home',
    components: {
      RichText,
      'category': category,
      'sidebar': sidebar,
      'tag': tag,
      'timeline': timeline,
      'carousel': carousel,
      'blog-post': blogPost,
      'navigation': navigation
    },
    data () {
      return {
        list: [
          {
            title: '《C++ Primer》笔记 第15章 面向对象程序设计',
            value: '面向对象程序设计的核心思想是数据抽象、继承和动态绑定。通过继承联系在一起的类构成一种层次关系。通常在层次关系的根部有一个基类，其他类则直接或间接地从基类继...',
            image: require('../assets/image/blog-post.jpg')
          },
          {
            title: '《The Notebook》Chapter 2 Ghosts Part 5',
            value: 'She still had trouble believing it, even as she held the proof1 in her hands....',
            image: require('../assets/image/blog-post.jpg')
          },
          {
            title: '《The Notebook》Chapter 2 Ghosts Part 4',
            value: 'During their time together, his father would talk about birds and animals or ...',
            image: require('../assets/image/blog-post.jpg')
          },
          {
            title: '《The Notebook》Chapter 2 Ghosts Part 3',
            value: 'He was handsome, intelligent, and driven1, a successful lawyer eight years ol...',

          }
        ],
        message: 'C9'
      }
    }
  }
</script>

<style scoped>
  .home-page {
    width: 100%;
  }

  .post-list {
    width: 700px;
    margin: 20px auto;
  }


</style>
