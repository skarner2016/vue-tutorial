<script setup>
import { ref } from 'vue';
import son from './5_son.vue'

const count = ref(100)
setTimeout(() => {
  count.value /= 2
}, 2000)

const getMsg = (msg) => {
  console.log(msg)
}

</script>

<template>
  <div>
    <h2>父组件App</h2>
    <!-- <son :count="count" message="father message"></son> -->
    <son @get-msg="getMsg"></son>
  </div>
</template>

<style scoped>
</style>