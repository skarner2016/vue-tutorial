<script setup>
import { computed, ref } from 'vue';


const list = ref([1,2,3,4,5,6,7,8])

/**
 * 计算属性: 
 *  1. 计算属性中不应该有"副作用"
 *  2. 避免直接修改计算属性的值 (在计算属性外部只读)
 */
const computedList = computed(() => {
    return list.value.filter(item => item > 2)
})

setTimeout(() => {
    list.value.push(9, 10)
}, 2000);

</script>

<template>
    <div>
        原始响应式数据 - {{ list }}
    </div>
    <div>
        计算属性数据 - {{ computedList }}
    </div>
</template>