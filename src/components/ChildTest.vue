<script setup lang="ts">
import SumziTest from '../components/SunziTest.vue'
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
console.log('$parent', instance)


// attrs
const attrs = useAttrs()
console.log('$attrs', attrs)

// ref 父组件调用子组件的函数
const getchildName = () => {
  console.log(12312, childName.value)
  return childName.value
}

defineExpose({ getchildName })
</script>


<template>
  <div class="greetings">
    <h1 class="green">{{ msg }}</h1>
    <h1>childName:{{ childName }}</h1>
    <h1>{{ $attrs.attrs }}</h1>
    <button @click="clickButton">子组件按钮</button>
    <hr>
    <h2>孙子组件</h2>
    <SumziTest msg='孙子你好' name="孙子的name"></SumziTest>
  </div>
</template>