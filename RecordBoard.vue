<style scoped>
  .record-board {
    width: 100%;
    margin: 0 calc((100vw / 150) + 20px);
    animation: hide 0.5s ease forwards;
  }
  .active .record-board {
    animation: show 1s ease forwards;
  }
  @keyframes hide {
    0% {
      opacity: 1;
      transform: rotateZ(0deg) scale(1);
    }
    100% {
      opacity: 0;
      transform: rotateZ(999deg) scale(0);
    }
  }
  @keyframes show {
    0% {
      opacity: 0;
      transform: rotateZ(999deg) scale(0);
    }
    100% {
      opacity: 1;
      transform: rotateZ(0deg) scale(1);
    }
  }
</style>

<template>
  <div class="record-board">
    <RecordBoardHeader></RecordBoardHeader>
    <RecordBoardMain></RecordBoardMain>
  </div>
</template>

<script>
  import RecordBoardHeader from './RecordBoardHeader.vue'
  import RecordBoardMain from './RecordBoardMain.vue'
  export default {
    name: 'RecordBoard',
    components: {
      [RecordBoardHeader.name]: RecordBoardHeader,
      [RecordBoardMain.name]: RecordBoardMain
    }
  }
</script>
