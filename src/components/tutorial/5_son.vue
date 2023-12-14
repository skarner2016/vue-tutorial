<script setup>

import { defineEmits } from 'vue';
// 接受父组件传来的信息
const props = defineProps({
  message: String,
  count: Number
})
console.log(props)

const emit = defineEmits([
  'get-msg'
])

const sendMsg = () => {
  emit('get-msg', 'this is son msg')
}

</script>

<template>
  <div>
    <h3>子组件App</h3>
    <div>父组件传入的数据 - {{ message }}</div>
    <div>父组件传入的数据 - {{ count }}</div>
    <button @click="sendMsg">button</button>
  </div>
</template>

<style scoped></style>
