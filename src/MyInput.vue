<template>
  <div class="myinput">
    <el-input ref="elInp" v-bind="attrs" @click="sum">
      <template v-for="(value, name) in slots" #[name]="scopedData">
        <slot :name="name"> </slot>
      </template>
    </el-input>
  </div>
</template>

<script setup>
import { onMounted, useAttrs, useSlots, ref } from 'vue'

const attrs = useAttrs()
const slots = useSlots()
const elInp = ref(null)
defineExpose({
  elInp
})

defineProps({
  a: Number,
  b: Number
})

onMounted(() => {
  // 直接访问 $attrs，无需通过 this
  console.log(attrs)
  console.log(slots)
})

const sum = () => {
  console.log('hello')
}
</script>

<style scoped>
.myinput {
  background-color: aqua;
  border: 10px solid red;
}
</style>
