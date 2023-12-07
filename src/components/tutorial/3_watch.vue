<script setup>
import { ref, watch } from 'vue'

/**
 * watch: 用于监听一个或者多个数据变化,数据变化时执行函数
 *  tips:
 *      1. immediate (立即执行)
 *      2. deep (深度监听)
 */

const count = ref(0)
const setCount = () => {
  count.value++
}

const name = ref("name")
const appendName = () => {
  name.value += "p"
}

const immediate = ref("immediate")
const appendImmediate = () => {
    immediate.value += "p"
}
// 1. 监听一个数据的变化
watch(count, (newValue, oldValue) => {
  console.log(newValue, oldValue)
})

// 2. 监听多个数据变化
watch([count, name], ([newCount, newName], [oldCount, oldName]) => {
  console.log(newCount, newName, oldCount, oldName)
})

// 3. immediate (立即执行)
watch(count, (newValue, oldValue) => {
  console.log(newValue, oldValue)
}, {
    immediate: true
})

// 4. deep (深度监听)

const status = ref({count:0})
const addStatusCount = () => {
    status.value.count ++
}

// 此时无法监听到 status.count 的变化
// watch(status, (newValue, oldValue) => {
//     console.log(newValue, oldValue)
// })


// 此时可以监听到 status.count 的变化
watch(status, (newValue, oldValue) => {
    console.log(newValue.count, oldValue.count)
}, {
    deep: true
})

</script>

<template>
  <div>
    <button @click="setCount">count: {{ count }}</button>
  </div>
  <div>
    <button @click="appendName">name: {{ name }}</button>
  </div>

  <div>
    <button @click="appendImmediate">immediate: {{ immediate }}</button>
  </div>

  <div>
    <button @click="addStatusCount">deep: {{ status.count }}</button>
  </div>
</template>
