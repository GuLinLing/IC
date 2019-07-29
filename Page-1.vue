<style scoped>
</style>

<template>
  <section class="page-1">
    <Trick>
      <img src="@/assets/img/1.png">
    </Trick>
  </section>
</template>

<script>
  import Trick from '@/components/Trick.vue'
  export default {
    name: 'Page1',
    components: {
      [Trick.name]: Trick
    }
  }
</script>
