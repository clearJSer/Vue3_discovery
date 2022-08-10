<script setup lang="ts">
import { defineEmits, ref, defineExpose, getCurrentInstance, useAttrs } from 'vue'
defineProps<{
  msg: string
}>()
const childName = ref('子组件的值')
const emits = defineEmits(['getChildData'])
const clickButton = (e: Event) => {
  emits("getChildData", new Date().getTime())
}


// $parent
const instance = getCurrentInstance()
console.log('孙子 $parent', instance)


// attrs
const attrs = useAttrs()
console.log('孙子走 $attrs', attrs)

// ref 父组件调用子组件的函数
const getchildName = () => {
  console.log(12312, childName.value)
  return childName.value
}

defineExpose({ getchildName })
</script>


<template>
  <div class="greetings">
    <div>========孙子组件========</div>
    <h1 class="green">{{ msg }}</h1>
    <h1>11{{ $attrs.attrs }}</h1>
    <button @click="clickButton">孙子组件按钮</button>
  </div>
</template>