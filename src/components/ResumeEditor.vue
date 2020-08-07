<template>

  <div class="resumeEditor" :class="{htmlMode:enableHtml}" ref="container">
    <img class="avatar" src="../assets/avatar.jpg" alt="">

    <div v-if="enableHtml" v-html="result"></div>
    <pre v-else>{{result}}</pre>
  </div>
</template>

<script>
  import marked from 'marked'
  export default {
    props: ['markdown', 'enableHtml'],
    name: 'ResumeEditor',
    computed: {
      result: function () {
        return this.enableHtml ? marked(this.markdown) : this.markdown
      }
    },
    methods: {
      goBottom: function () {
        this.$refs.container.scrollTop = 100000
      },
      goTop: function(){
        this.$refs.container.scrollTop = 0
      }
    }
  }

</script>

<style scoped>
    .resumeEditor{
       position: relative;
    }
  @media (max-width:500px){
    .resumeEditor{
       position: relative;
    }

  }
  .htmlMode {
    animation: flip 2s;
  }

  @keyframes flip {
    from {
      opacity: 0;
    }
    to {
      opacity: 1;
    }
  }
  .avatar{
    position: absolute;
    top: 5px;
    right: 1em;
    width: 50px;
    height: 50px;
    border-radius: 50%;
  }
  .avatar::after{
    content: "";
    display: block;
    clear: both;
  }
  .avatar:hover {
    transform: rotate(666turn);
    transition-duration: 59s;
    transition-timing-function: cubic-bezier(.34, 0, .84, 1)
}
</style>
