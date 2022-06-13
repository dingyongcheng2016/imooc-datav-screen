<template>
  <div id="imooc-screen-container" :ref="ref">
    <template v-if="ready">
      <slot></slot>
    </template>
  </div>
</template>

<script>
  import autoResize from './autoResize.js'

  export default {
    name: 'DvFullScreenContainer',
    mixins: [autoResize],
    props: {
      options: {
        type: Object
      }
    },
    data() {
      return {
        ref: 'full-screen-container',
        allWidth: 0,
        allHeight: 0,
        scale: 0,
        datavRoot: '',
        ready: false
      }
    },
    methods: {
      afterAutoResizeMixinInit() {
        this.initConfig()
        this.setAppScale()
        this.ready = true
      },
      initConfig() {
        this.allWidth = this.width || this.originalWidth
        this.allHeight = this.height || this.originalHeight
        this.dom.style.width = `${this.allWidth}px`
        this.dom.style.height = `${this.allHeight}px`
      },
      setAppScale() {
        const currentWidth = document.body.clientWidth
        const currentHeight = document.body.clientHeight
        this.dom.style.transform = `scale(${currentWidth / this.allWidth}, ${currentHeight / this.allHeight})`
      },
      onResize() {
        this.setAppScale()
      }
    }
  }
</script>

<style lang="less">
  #imooc-screen-container {
    position: fixed;
    top: 0;
    left: 0;
    overflow: hidden;
    transform-origin: left top;
    z-index: 999;
  }
</style>
