<!--
  分类栏目
-->
<template>
  <div class="category">
    <!--  分类列表  -->
    <ul class="category-list">
      <!--  分类元素 -->
      <li class="category-item" v-for="category in categoryList">
        <a href="#" class="category-link">
          <i class="category-icon icon-svg">
            <font-awesome-icon v-bind:icon="['far',iconMap.folder]"></font-awesome-icon>
          </i>
          <span class="category-title text-style text-ellipsis">{{category.title}}</span>
        </a>
        <!--  子分类列表  -->
        <ul class="category-list sub-category-list">
          <!--  子分类元素 -->
          <li class="category-item sub-category-item" v-for="subCategory in category.subCategoryList">
            <a href="#" class="category-link sub-category-link">
              <i class="icon-svg category-icon sub-category-icon ">
                <font-awesome-icon v-bind:icon="iconMap.folder"></font-awesome-icon>
              </i>
              <span class="text-style text-ellipsis category-title sub-category-title">{{subCategory.title}}</span>
            </a>
          </li>
        </ul>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: 'category',
    data () {
      return {
        //图标映射
        iconMap: {
          folder: 'folder'
        },
        //栏目列表
        categoryList: [
          {
            'title': '第三罗马',
            href: '',
            subCategoryList: [
              {
                'title': '第三罗马',
                href: '',
              },
              {
                'title': '国富论',
                href: ''
              },
              {
                'title': '天命',
                href: ''
              },
              {
                'title': '人权人权人权人权人权',
                href: ''
              },
              {
                'title': '我们的海',
                href: ''
              }
            ]
          },
          {
            'title': '国富论',
            href: ''
          },
          {
            'title': '天命',
            href: '',
            subCategoryList: [
              {
                'title': '第三罗马',
                href: '',
              },
              {
                'title': '国富论',
                href: ''
              },
            ]
          },
          {
            'title': '人权人权人权人权人权',
            href: '',
            subCategoryList: [
              {
                'title': '第三罗马',
                href: '',
              }
            ]
          },
          {
            'title': '我们的海',
            href: ''
          }
        ]
      }
    }
  }
</script>

<style scoped>
  .category {
    position: absolute;
    top: auto;
    left: 0;
    z-index: 10;
    width: 100%;
    height: 100%;
    /*background: #ffffff;*/
    /*box-shadow: 1px 2px 3px rgba(0, 0, 0, .2);*/
    overflow-y: auto;
    color: #7f7f7f;
  }

  /*  滚动条样式*/
  .category::-webkit-scrollbar {
    width: 5px;
  }

  .category::-webkit-scrollbar-track {
    background: #eee;
    border-radius: 3px;
  }

  .category::-webkit-scrollbar-thumb {
    background: #ccc;
    border-radius: 5px;
  }

  .category::-webkit-scrollbar-thumb:hover {
    background: #c0c0c0;
  }

  .category::-webkit-scrollbar-corner {
    background: #179a16;
  }

  /*  分类列表  */
  .category-list {
    padding: 10px;
  }

  .category-link {
    display: flex;
    padding: 7px 15px;
    cursor: pointer;
  }

  .category-link:hover {
    background-color: rgba(0, 0, 0, .05);
  }

  .category-icon {

  }

  .category-title {
    margin-left: 15px;
  }

  /*  子分类列表   */
  .sub-category-list {
    padding: 0 0 0 20px;
  }
</style>
