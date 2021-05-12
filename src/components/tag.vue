<!--
  标签组件
-->
<template>
  <div class="tag">
    <div class="tag-panel">
      <!--      标签    -->
      <a class="tag-item" v-for="tag in tagList" v-bind:class="tag.type">
        <!--      标签图标    -->
        <span class="tag-icon">
          <font-awesome-icon v-bind:icon="tag.icon"/>
        </span>
        <span class="tag-title">{{tag.title}}</span>
      </a>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'tag',
    data () {
      return {
        //标签列表
        tagList: [{
          title: '好书推荐',
          type: 'live',
          icon: 'book'
        }, {
          title: 'music',
          type: 'skill',
          icon: 'music'
        }, {
          title: '工具',
          type: 'tools',
          icon: 'moon'
        }, {
          title: 'JAVASCRIPT',
          type: 'skill',
          icon: 'sun'
        }]
      }
    }
  }
</script>

<style scoped>
  .tag {
    margin: 60px auto;
  }

  .tag-panel {
    padding: 10px;
    margin: 10px;
  }

  /*  标签  */
  .tag-item {
    padding: 5px;
    border-radius: 10px;
    color: #ffffff;
    font-size: 13px;
    margin-right: 10px;
    background: #2f3342;
  }

  .tag-icon > i {
    color: #ffffff;
  }

  /**
    标签类型
    skill:技能
    live:生活
    tools:工具
    **/
  .tag-item.skill {
    background: #2f3342;
  }

  .tag-item.live {
    background: #46bd87;
  }

  .tag-item.tools {
    background: #880000;
  }
</style>
