<style scoped>
  ul {
    position: relative;
    margin: 0 0 0 5px;
    padding: 0 calc((100vw / 150) + 14px);
    font-size: 0;
    text-align: center;
    white-space: nowrap;
    overflow: hidden;
    box-shadow: 0 1px 4px rgba(0, 0, 0, .50), 0 0 6px rgba(0, 0, 0, .50);
  }
  .active .top {
    transform-origin: 10px 10px;
    transform: rotateZ(-45deg);
    animation: rotate 1s cubic-bezier(0.68, -0.55, 0.68, 0) forwards 2s;
  }
  .bottom {
    margin-top: 3px;
  }
  li {
    display: inline-block;
    width: calc((100vw / 150) + 28px);
    height: calc((100vw / 150) + 28px);
  }
  li:nth-child(odd) {
    background-color: #f0f9fe;
  }
  li:nth-child(even) {
    background-color: #000;
  }
  .top > li {
    transform: skewX(44deg);
  }
  .bottom > li {
    transform: skewX(-44deg);
  }
  .top::before {
    content: '';
    position: absolute;
    left: 0;
    bottom: 0;
    border-top: calc((100vw / 150) + 14px) solid transparent;
    border-left: calc((100vw / 150) + 14px) solid #191a1d;
    border-right: calc((100vw / 150) + 14px) solid transparent;
    border-bottom: calc((100vw / 150) + 14px) solid #191a1d;
  }
  .top::after {
    content: '';
    position: absolute;
    top: 0;
    right: 0;
    border-top: calc((100vw / 150) + 14px) solid #191a1d;
    border-left: calc((100vw / 150) + 14px) solid transparent;
    border-right: calc((100vw / 150) + 14px) solid #191a1d;
    border-bottom: calc((100vw / 150) + 14px) solid transparent;
  }
  .bottom::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    border-top: calc((100vw / 150) + 14px) solid #191a1d;
    border-left: calc((100vw / 150) + 14px) solid #191a1d;
    border-right: calc((100vw / 150) + 14px) solid transparent;
    border-bottom: calc((100vw / 150) + 14px) solid transparent;
  }
  .bottom::after {
    content: '';
    position: absolute;
    right: 0;
    bottom: 0;
    border-top: calc((100vw / 150) + 14px) solid transparent;
    border-left: calc((100vw / 150) + 14px) solid transparent;
    border-right: calc((100vw / 150) + 14px) solid #191a1d;
    border-bottom: calc((100vw / 150) + 14px) solid #191a1d;
  }
  @keyframes rotate {
    from {
      transform: rotateZ(-45deg);
    }
    to {
      transform: rotateZ(0deg);
    }
  }
</style>

<template>
  <ul v-bind:class="path">
    <li
      v-for="item in num"
      v-bind:key="item"
    />
  </ul>
</template>

<script>
  export default {
    name: 'RecordBoardLine',
    props: {
      path: {
        type: String,
        default: 'top'
      }
    },
    data () {
      return {
        num: 10
      }
    },
    mounted () {
      this.computedNum()
      window.addEventListener('resize', this.computedNum)
    },
    destroyed () {
      window.removeEventListener('resize', this.computedNum)
    },
    methods: {
      computedNum () {
        let wrap = this.$parent.$parent.$el
        let box = this.$el.children[0]
        let wrapWidth = wrap.clientWidth - wrap.offsetLeft - (window.innerWidth / 150 + 30)
        let boxWidth = box.clientWidth
        this.num = Math.floor(wrapWidth / boxWidth)
      }
    }
  }
</script>
