<template>

  <div class="about">
    <h1>父传子页面测试</h1>
    <div>
      vue3 中 $on $children $listeners 已经被移除了
    </div>
    <button @click="fatherClick">父页面的按钮</button>
    获取子页面的值：{{ childName }}
    <div>
      <div>子页面</div>
      <div>
        <div>父组件展示子组件的数据</div>
        <div>{{ age }}</div>
      </div>
      <ChildTest msg="123123" @getChildData="getChild" ref="childRef" attrs='测试$attrs' />
    </div>
    <hr>

  </div>
</template>
<script setup lang="ts">
import { ref } from 'vue'
import ChildTest from '../components/ChildTest.vue'
const age = ref()
const childRef = ref()
const childName = ref()
// console.log(HelloWorld)
const getChild = (val: number) => {
  age.value = val
}
const fatherClick = () => {
  console.log(111)
  childName.value = childRef.value.getchildName()
}

</script>
<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    align-items: center;
  }
}
</style>
