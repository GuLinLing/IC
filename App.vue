<style scoped>
  #app {
    position: relative;
    color: #f8f8f8;
    background-color: #393e49;
    overflow: hidden;
  }
  img {
    position: fixed;
    top: 20px;
    right: 20px;
    width: calc((100vw / 150) + 35px);
    user-select: none;
    animation: rotate 3s linear infinite;
  }
  img.pause {
    animation-play-state: paused;
  }
  @keyframes rotate {
    from {
      transform: rotateZ(0deg);
    }
    to {
      transform: rotateZ(360deg);
    }
  }
</style>

<template>
  <div id="app">
    <div
      class="pages"
      ref="pages"
    >
      <Page0></Page0>
      <Page1></Page1>
      <Page2></Page2>
      <Page3></Page3>
      <Page4></Page4>
      <Page5></Page5>
      <Page6></Page6>
      <Page7></Page7>
      <Page8></Page8>
      <Page9></Page9>
      <Page10></Page10>
    </div>
    <img
      v-on:click="musicClickHandler"
      src="@/assets/img/music.svg"
    >
  </div>
</template>

<script>
import Page0 from './views/page0'
import Page1 from './views/page1'
import Page2 from './views/page2'
import Page3 from './views/page3'
import Page4 from './views/page4'
import Page5 from './views/page5'
import Page6 from './views/page6'
import Page7 from './views/page7'
import Page8 from './views/page8'
import Page9 from './views/page9'
import Page10 from './views/page10'
export default {
  name: 'app',
  mounted () {
    let children = this.$refs.pages.children
    this.scroll = {
      min: 0,
      index: 0,
      max: children.length - 1,
      lock: false
    }
    children[this.scroll.index].classList.add('active')
    this.$el.addEventListener('wheel', this.whellHandler)
  },
  methods: {
    musicClickHandler (event) {
      event.target.classList.toggle('pause')
    },
    whellHandler (event) {
      let num = event.wheelDelta ? event.wheelDelta : event.detail // 兼容性
      if (num > 0) {
        !this.scroll.lock && this.scrollHandler('prev')
      }
      if (num < 0) {
        !this.scroll.lock && this.scrollHandler('next')
      }
    },
    scrollHandler (key) {
      this.scroll.lock = true
      this.scroll.index = key === 'prev'
        ? Math.max(this.scroll.index - 1, this.scroll.min)
        : Math.min(this.scroll.index + 1, this.scroll.max)
      let pages = this.$refs.pages.children
      let pageItem = pages[this.scroll.index]
      if (this.$el.scrollIntoView) { // 兼容性
        pageItem.scrollIntoView({ behavior: 'smooth' })
      } else {
        this.$el.scrollTop = pageItem.offsetTop
      }
      if (!pageItem.classList.contains('active')) {
        Array.prototype.forEach.call(
          pages,
          item => item.classList.remove('active')
        )
        pageItem.classList.add('active')
      }
      setTimeout(() => this.scroll.lock = false, 1000)
    }
  },
  components: {
    [Page0.name]: Page0,
    [Page1.name]: Page1,
    [Page2.name]: Page2,
    [Page3.name]: Page3,
    [Page4.name]: Page4,
    [Page5.name]: Page5,
    [Page6.name]: Page6,
    [Page7.name]: Page7,
    [Page8.name]: Page8,
    [Page9.name]: Page9,
    [Page10.name]: Page10
  }
}
</script>
