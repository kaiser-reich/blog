<template>
  <div class="rich-text">
    <!--    编辑工具    -->
    <ul class="editor-toolbar">
      <li class="toolbar-item" v-on:click="bold" v-bind:class="isActive(toolbarStatus.isBold)">
        <font-awesome-icon v-bind:icon="iconMap.bold"></font-awesome-icon>
      </li>
      <li class="toolbar-item" v-on:click="italic" v-bind:class="isActive(toolbarStatus.isItalic)">
        <font-awesome-icon v-bind:icon="iconMap.italic"></font-awesome-icon>
      </li>
      <li class="toolbar-item" v-on:click="heading" v-bind:class="isActive(toolbarStatus.isHeading)">
        <font-awesome-icon v-bind:icon="iconMap.heading"></font-awesome-icon>
      </li>
      <li class="toolbar-item" v-on:click="strikethrough" v-bind:class="isActive(toolbarStatus.isStrike)">
        <font-awesome-icon v-bind:icon="iconMap.strikethrough"></font-awesome-icon>
      </li>
      <li class="toolbar-item">
        <font-awesome-icon v-bind:icon="iconMap.font"></font-awesome-icon>
        <div class="current-color" v-bind:style="{'background-color': currentColor}"></div>
        <!--    字体颜色    -->
        <div class="font-color">
          <div class="default-color" v-on:click="fontColor">
            <div class="color-black"></div>
            <span class="color-text">默认颜色</span>
          </div>
          <ul class="color-list">
            <li class="color-item" v-for="color in colorList" v-on:click="fontColor(color.color)"
                v-bind:style="{'background-color':color.color,'border-color':color.subColor}"></li>
          </ul>
        </div>
      </li>
      <span class="editor-toolbar-separator"></span>
      <li class="toolbar-item" v-on:click="justifyLeft">
        <font-awesome-icon v-bind:icon="iconMap.alignLeft"></font-awesome-icon>
      </li>
      <li class="toolbar-item" v-on:click="justifyCenter">
        <font-awesome-icon v-bind:icon="iconMap.alignCenter"></font-awesome-icon>
      </li>
      <li class="toolbar-item" v-on:click="justifyRight">
        <font-awesome-icon v-bind:icon="iconMap.alignRight"></font-awesome-icon>
      </li>
      <span class="editor-toolbar-separator"></span>
      <li class="toolbar-item" v-on:click="insertOl">
        <font-awesome-icon v-bind:icon="iconMap.listUl"></font-awesome-icon>
      </li>
      <li class="toolbar-item" v-on:click="insertUl">
        <font-awesome-icon v-bind:icon="iconMap.listOl"></font-awesome-icon>
      </li>
      <span class="editor-toolbar-separator"></span>
      <li class="toolbar-item" v-on:click="quote">
        <font-awesome-icon v-bind:icon="iconMap.quote"></font-awesome-icon>
      </li>
      <li class="toolbar-item" v-on:click="ellipsis">
        <font-awesome-icon v-bind:icon="iconMap.ellipsis"></font-awesome-icon>
      </li>
      <li class="toolbar-item" v-on:click="code">
        <font-awesome-icon v-bind:icon="iconMap.code"></font-awesome-icon>
      </li>
      <span class="editor-toolbar-separator"></span>
      <li class="toolbar-item" v-on:click="createLink">
        <font-awesome-icon v-bind:icon="iconMap.paperclip"></font-awesome-icon>
      </li>
      <li class="toolbar-item" v-on:click="insertImage">
        <font-awesome-icon v-bind:icon="iconMap.image"></font-awesome-icon>
      </li>
    </ul>
    <!--    编辑区    -->
    <div class="editor-panel">
      <iframe id="editor" class="editor"
              src='javascript:void(function(){document.open();document.write("<style>@import \"./static/iframe.css\"</style>");document.close()}())'></iframe>
    </div>
  </div>
</template>

<script>
  var vm = null

  export default {
    name: 'rich-text',
    data () {
      return {
        editorIframe: null,
        editor: null,
        currentColor: '#000000',
        //工具栏状态
        toolbarStatus: {
          isBold: false,
          isItalic: false,
          isHeading: false,
          isStrike: false,
        },
        //图标映射
        iconMap: {
          bold: 'bold',
          italic: 'italic',
          heading: 'heading',
          list: 'list',
          listOl: 'list-ol',
          listUl: 'list-ul',
          paperclip: 'paperclip',
          quote: 'quote-left',
          code: 'code',
          strikethrough: 'strikethrough',
          font: 'font',
          image: 'image',
          ellipsis: 'ellipsis-h',
          alignLeft: 'align-left',
          alignRight: 'align-right',
          alignCenter: 'align-center'
        },
        //颜色列表
        colorList: [
          {
            color: 'rgb(107, 195, 245)',
            subColor: 'rgb(137, 212, 255)'
          },
          {
            color: 'rgb(98, 215, 199)',
            subColor: 'rgb(115, 253, 234)'
          },
          {
            color: 'rgb(116, 213, 67)',
            subColor: 'rgb(137, 250, 78)'
          },
          {
            color: 'rgb(218, 214, 87)',
            subColor: 'rgb(255, 243, 89)'
          },
          {
            color: 'rgb(217, 128, 120)',
            subColor: 'rgb(255, 150, 141)'
          },
          {
            color: 'rgb(243, 142, 193)',
            subColor: 'rgb(255, 160, 208)'
          },
          {
            color: 'rgb(8, 122, 192)',
            subColor: 'rgb(11, 132, 237)'
          },
          {
            color: 'rgb(25, 196, 176)',
            subColor: 'rgb(24, 231, 207)'
          },
          {
            color: 'rgb(83, 183, 49)',
            subColor: 'rgb(96, 216, 55)'
          },
          {
            color: 'rgb(213, 192, 44)',
            subColor: 'rgb(251, 226, 49)'
          },
          {
            color: 'rgb(217, 84, 66)',
            subColor: 'rgb(234, 0, 119)'
          },
          {
            color: 'rgb(204, 37, 121)',
            subColor: 'rgb(234, 0, 119)'
          },
          {
            color: 'rgb(6, 101, 159)',
            subColor: 'rgb(1, 118, 186)'
          },
          {
            color: 'rgb(0, 168, 158)',
            subColor: 'rgb(6, 143, 134)'
          },
          {
            color: 'rgb(29, 150, 6)',
            subColor: 'rgb(29, 177, 0)'
          },
          {
            color: 'rgb(210, 158, 4)',
            subColor: 'rgb(248, 186, 0)'
          },
          {
            color: 'rgb(202, 31, 12)',
            subColor: 'rgb(238, 35, 13)'
          },
          {
            color: 'rgb(173, 35, 105)',
            subColor: 'rgb(203, 41, 122)'
          },
          {
            color: 'rgb(2, 66, 109)',
            subColor: 'rgb(0, 78, 128)'
          },
          {
            color: 'rgb(3, 106, 101)',
            subColor: 'rgb(1, 124, 118)'
          },
          {
            color: 'rgb(5, 96, 4)',
            subColor: 'rgb(1, 112, 1)'
          },
          {
            color: 'rgb(217, 126, 5)',
            subColor: 'rgb(255, 146, 1)'
          },
          {
            color: 'rgb(154, 21, 4)',
            subColor: 'rgb(180, 23, 0)'
          },
          {
            color: 'rgb(130, 22, 80)',
            subColor: 'rgb(153, 25, 94)'
          },
          {
            color: 'rgb(182, 181, 181)',
            subColor: 'rgb(214, 213, 213)'
          },
          {
            color: 'rgb(124, 124, 124)',
            subColor: 'rgb(146, 146, 146)'
          },
          {
            color: 'rgb(80, 80, 80)',
            subColor: 'rgb(115, 253, 234)'
          },
        ]
      }
    },
    computed: {},
    created () {
      vm = this
    },
    mounted () {
      this.$data.editorIframe = document.getElementById('editor') && document.getElementById('editor').contentWindow
      this.$data.editor = document.getElementById('editor') && document.getElementById('editor').contentWindow

      let link = document.createElement('style')
      link.src = '../assets/css/iframe.css'
      link.innerHTML = '@import "../assets/css/iframe.css";'

      // link.rel='stylesheet">'
      // console.log(link)
      // this.$data.editor.document.getElementsByTagName("head")[0].appendChild(link);

      this.$data.editor.document.contentEditable = 'true'
      this.$data.editor.document.designMode = 'on'
    },
    methods: {
      //计算隐藏显示
      isActive: function (bool) {
        return bool ? 'active' : ''
      },

      //编辑文本
      execEditorCommand: function (name = '', args = null) {
        vm.$data.editor.document.execCommand(name, false, args)
      },

      //加粗
      bold: function () {
        vm.$data.toolbarStatus.isBold = !vm.$data.toolbarStatus.isBold
        vm.execEditorCommand('bold', null)
      },

      //倾斜
      italic: function () {
        vm.$data.toolbarStatus.isItalic = !vm.$data.toolbarStatus.isItalic
        vm.execEditorCommand('italic', null)
      },

      //标题
      heading: function () {
        vm.$data.toolbarStatus.isHeading = !vm.$data.toolbarStatus.isHeading
        vm.execEditorCommand('heading', null)
      },

      //删除线
      strikethrough: function () {
        vm.$data.toolbarStatus.isStrike = !vm.$data.toolbarStatus.isStrike
        vm.execEditorCommand('strikethrough', null)
      },

      //字体颜色
      fontColor: function (color = '#000000') {
        vm.$data.currentColor = color
        vm.execEditorCommand('foreColor', color)
      },

      //左对齐
      justifyLeft: function () {
        vm.execEditorCommand('justifyLeft', null)
      },

      //居中
      justifyCenter: function () {
        vm.execEditorCommand('justifyCenter', null)
      },

      //右对齐
      justifyRight: function () {
        vm.execEditorCommand('justifyRight', null)
      },

      //有序列表
      insertOl: function () {
        vm.execEditorCommand('insertOrderedList', null)
      },

      //无序列表
      insertUl: function () {
        vm.execEditorCommand('insertUnorderedList', null)
      },

      //引用
      quote: function () {
        vm.execEditorCommand('formatBlock', 'blockquote')
      },

      //分割线
      ellipsis: function () {
        vm.execEditorCommand('insertHorizontalRule', null)
      },
      //代码块
      code: function () {
        vm.execEditorCommand('code', null)
      },

      //链接
      createLink: function () {
        vm.execEditorCommand('createLink', 'ddd')
      },

      //图片
      insertImage: function () {
        let file = document.createElement('input')
        file.type = 'file'
        file.click()

        file.onchange = function () {
          vm.execEditorCommand('insertImage', vm.getObjectURL(this.files[0]))
          file = null
        }
      },

      //获取URL
      getObjectURL: function (file) {
        let url = null
        if (window.createObjcectURL !== undefined) {
          url = window.createOjcectURL(file)
        } else if (window.URL !== undefined) {
          url = window.URL.createObjectURL(file)
        } else if (window.webkitURL !== undefined) {
          url = window.webkitURL.createObjectURL(file)
        }
        return url
      },
    }
  }
</script>

<style scoped>
  /*  富文本  */
  .rich-text {
    margin: 60px auto;
    color: #7f7f7f;
    width: 600px;
    height: auto;
    background: #ffffff;
  }

  /*  编辑工具  */
  .editor-toolbar {
    padding: 5px;
    border-top: 1px #e1e1e1 solid;
    border-bottom: 1px #e1e1e1 solid;
  }

  .toolbar-item {
    display: inline-block;
    padding: 5px;
    cursor: pointer;
    border-radius: 6px;
    position: relative;
  }

  .toolbar-item:hover {
    background: #e1e1e1;
  }

  .toolbar-item.active {
    color: #1f4f89;
  }

  .current-color {
    height: 3px;
    width: 15px;
    background: #000000;
  }

  /*  分割线  */
  .editor-toolbar-separator {
    border-left: 1px #bbbbbb solid;
    height: 20px;
    width: 1px;
    margin: 0 10px;
  }

  /*  编辑区   */
  .editor-panel {
    padding: 10px;
  }

  .editor {
    width: 100%;
    min-height: 250px;
    border: none;
  }

  /*  字体颜色  */
  .font-color {
    width: 174px;
    height: 192px;
    background: #f1f3f7;
    box-shadow: 0 2px 4px #ccd0d7;
    position: absolute;
    top: 30px;
    left: 0;
    display: none;
  }

  .toolbar-item:nth-child(5):hover .font-color {
    display: block;
  }

  .color-list {
    padding: 9px;
    display: flex;
    flex-direction: row;
    align-items: center;
    flex-wrap: wrap;
  }

  .color-item {
    width: 18px;
    height: 18px;
    border-radius: 3px;
    margin: 3px;
    border-width: 1px;
    border-style: solid;
  }

  .color-item:hover {
    box-shadow: 0 0 10px #00e2ff;
    border-color: #fff !important;
  }

  /*  默认颜色  */
  .default-color {
    padding: 9px;
    display: flex;
    flex-direction: row;
    align-items: center;
    cursor: pointer;
    border-bottom: 1px #e0e0e0 solid;
  }

  .color-black {
    width: 18px;
    height: 18px;
    border-radius: 3px;
    margin: 3px;
    background: #000000;
    border: 1px #2f3342 solid;
  }

  .default-color:hover .color-black {
    box-shadow: 0 0 10px #00e2ff;
    border-color: #fff !important;
  }

  .color-text {
    margin-left: 10px;
    font-size: 14px;
  }
</style>
