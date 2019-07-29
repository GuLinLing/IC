<style scoped>
  .record-board-header {
    position: relative;
  }
  .record-board-header::before {
    content: '';
    position: absolute;
    left: 0;
    bottom: 0;
    width: calc((100vw / 150) + 10px);
    height: calc((100vw / 150) + 10px);
    background-color: #1c1d1f;
  }
  i {
    position: absolute;
    top: 0;
    left: 0;
    width: calc((100vw / 150) + 30px);
    height: 100%;
    background-color: #191a1e;
    border-radius: 5px;
  }
  i::before {
    content: '';
    position: absolute;
    top: -1px;
    left: calc((100vw / 150) + 20px);
    border-top: calc((100vw / 150) + 20px) solid transparent;
    border-left: calc((100vw / 150) + 40px) solid #191a1e;
    border-right: calc((100vw / 150) + 20px) solid transparent;
    border-bottom: calc((100vw / 150) + 40px) solid #191a1e;
  }
  span {
    position: absolute;
    width: calc((100vw / 150) + 10px);
    height: calc((100vw / 150) + 10px);
    border-radius: 50%;
    background-color: #46474a;
    box-shadow: 2px 2px 5px rgba(0, 0, 0, .50);
  }
  span:nth-of-type(1) {
    top: 10px;
    left: 10px;
  }
  span:nth-of-type(2) {
    left: 10px;
    bottom: 10px;
  }
  span:nth-of-type(3) {
    left: 50px;
    bottom: 10px;
  }
</style>

<template>
  <div class="record-board-header">
    <RecordBoardLine path="top"></RecordBoardLine>
    <RecordBoardLine path="bottom"></RecordBoardLine>
    <i></i>
    <span></span>
    <span></span>
    <span></span>
  </div>
</template>

<script>
  import RecordBoardLine from './RecordBoardLine.vue'
  export default {
    name: 'RecordBoardHeader',
    components: {
      [RecordBoardLine.name]: RecordBoardLine
    }
  }
</script>
