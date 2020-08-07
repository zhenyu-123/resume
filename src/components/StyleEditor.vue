<template>
<!--  -->
  <div class="styleEditor" ref="container">
    <!-- css样式 -->
    <div class="code" v-html="codeInStyleTag"></div>
    <!-- 代码 -->
    <pre class="" v-html="highlightedCode"></pre>
  </div>
</template>

<script>
  import Prism from 'prismjs'
  export default {
    name: 'Editor',
    props: ['code'],
    computed: {
      highlightedCode: function () {
        //代码高亮，语言选择css。
        return Prism.highlight(this.code, Prism.languages.css)
      },
      codeInStyleTag: function () {
        return `<style>${this.code}</style>`
      }
    },
    methods: {
      goBottom() {
        this.$refs.container.scrollTop = 100000
      }
    }
  }

</script>

<style scoped>
  pre{
  }
  @media (max-width:500px){
    pre{

    }
  }
  .code {
    display: none;
  }
</style>
