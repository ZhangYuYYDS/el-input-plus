<template>
  <MyInput :a="1" :b="2" :c="3" v-model="user.name" @click="add" ref="inputRef">
    <template #prefix>
      <span>aaa</span>
    </template>
    <template #suffix>
      <span>bbb</span>
    </template>
    <template #prepend>
      <span>ccc</span>
    </template>
    <template #append>
      <span>ddd</span>
    </template>
  </MyInput>
</template>

<script setup>
import MyInput from '@/MyInput.vue'
import { reactive, ref, onMounted } from 'vue'

const user = reactive({ name: 'John', age: 18, grade: 98 })

const add = () => {
  user.age++
  console.log(user.age)
}

const inputRef = ref(null)
// inputRef.value.elInp.sum()

onMounted(() => {
  console.log('333', inputRef.value.elInp)
})
</script>

<style scoped></style>
