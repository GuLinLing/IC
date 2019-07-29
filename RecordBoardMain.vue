<style scoped>
  .record-board-main {
    padding: calc((100vw / 150) + 15px);
    background-color: #1c1d1f;
    border-radius: 0 0 5px 5px;
    box-shadow: 0 1px 4px rgba(0, 0, 0, .50), 0 0 6px rgba(0, 0, 0, .50);
  }
  ul {
    margin: 0;
    padding: 0;
  }
  .key {
    color: #BFBFBF;
  }
  .value {
    display: inline-block;
    color: #F7F7F9;
    opacity: 0;
  }
  .active li:nth-of-type(1) .value {
    animation: show 1s cubic-bezier(0.68, -0.55, 0.27, 1.55) forwards 1.3s;
  }
  .active li:nth-of-type(2) .value {
    animation: show 1s cubic-bezier(0.68, -0.55, 0.27, 1.55) forwards 1.4s;
  }
  .active li:nth-of-type(3) .value {
    animation: show 1s cubic-bezier(0.68, -0.55, 0.27, 1.55) forwards 1.5s;
  }
  .active li:nth-of-type(4) .value {
    animation: show 1s cubic-bezier(0.68, -0.55, 0.27, 1.55) forwards 1.6s;
  }
  .active li:nth-of-type(5) .value {
    animation: show 1s cubic-bezier(0.68, -0.55, 0.27, 1.55) forwards 1.7s;
  }
  li {
    padding: calc((100vw / 150) + 10px) 0;
    border-bottom: 1px solid #F6FCFE;
  }
  p {
    display: inline-block;
    margin: 0 calc((100vw / 150) + 10px);
  }
  @keyframes show {
    0% {
      opacity: 0;
      transform: translateX(200px);
    }
    30% {
      opacity: 0.5;
      transform: translateX(20px);
    }
    40% {
      transform: translateX(-20px);
    }
    50% {
      transform: translateX(10px);
    }
    60% {
      transform: translateX(-10px);
    }
    70% {
      transform: translateX(5px);
    }
    80% {
      transform: translateX(-5px);
    }
    100% {
      opacity: 1;
    }
  }
</style>

<template>
  <div class="record-board-main">
    <ul>
      <li
        v-for="(arr, i) in array"
        v-bind:key="i"
      >
        <p
          v-for="(item, j) in arr"
          v-bind:key="j"
        >
          <span class="key">{{ item.key }}</span>
          <span class="value">{{ item.value }}</span>
        </p>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: 'RecordBoardMain',
    created () {
      this.array = [
        [{ id: '0001', key: '主题：', value: '《 两个人的侣行 》' }],
        [{ id: '0002', key: '新郎：', value: '张大华' }],
        [{ id: '0003', key: '新娘：', value: '王晓华' }],
        [
          { id: '0004', key: '卷号：', value: '520' },
          { id: '0005', key: '场号：', value: '13' },
          { id: '0006', key: '镜号：', value: '14' }
        ],
        [{ id: '0007', key: '日期：', value: '2020.12.10 12:00' }]
      ]
    }
  }
</script>
