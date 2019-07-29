<style scoped>
  .trick {
    position: relative;
    display: inline-block;
  }
  .active img {
    animation: blurry 10s ease infinite 1s;
  }
  @keyframes blurry {
    0% {
      filter: blur(0px);
    }
    5% {
      filter: blur(10px);
    }
    10% {
      filter: blur(0px);
    }
  }
</style>

<template>
  <div class="trick">
    <slot></slot>
  </div>
</template>

<script>
  export default {
    name: 'Trick'
  }
</script>
