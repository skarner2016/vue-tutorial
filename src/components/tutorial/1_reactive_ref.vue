<script setup>
import { reactive, ref } from 'vue';

/**
 * 相同点: 
 *    1. 响应式的对象
 *    2. ref 函数的内部实现依赖于 reactive
 * 不同点: 
 *    1. reactive 不同处理简单类型的数据
 *    2. ref 参数类型支持更好,但是必须通过 .value 访问修改
 */


// reactive: 接收对象类型的数据,并返回一个响应式的对象
const state = reactive({
  count: 0
})

const addCount1 = () => {
  state.count ++
}

// ref: 接收简单类型或者对象类型的数据,并返回一个响应式的对象
const count = ref(0)

const addCount2 = () => {
  count.value++
}

</script>

<template>
  <div>
    <button @click="addCount1"> reactive: {{  state.count }}</button>
  </div>

  <div>
    <button @click="addCount2"> ref: {{ count }} </button>
  </div>
</template>