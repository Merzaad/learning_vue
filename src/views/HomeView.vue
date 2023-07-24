<script setup>
import { reactive, ref } from 'vue'
const reactiveState = reactive({
  value: 0
})
const refState = ref(0)
const increase = () => {
  reactiveState.value++
}
const increase2 = () => {
  refState.value++
}
const input = ref('')
const onInputChange = (e) => {
  input.value = e.target.value
}
const toggle = ref(false)
</script>

<template>
  <div class="basic">
    <div class="box">{{ reactiveState.value }} <button @click="increase">reactive++</button></div>
    <div class="box">{{ refState }} <button @click="increase2">ref++</button></div>
    <div class="box">{{ input }}<input :value="input" @input="onInputChange" /></div>
    <div class="box">
      <div v-if="toggle">toggled</div>
      <div v-else>not toggled</div>
      <button :class="toggle && 'toggle'" @click="toggle = !toggle">toggle</button>
    </div>
  </div>
</template>

<style scoped>
.basic {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
.box {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  border: 1px solid hsla(160, 100%, 37%, 0.5);
  border-radius: 8px;
  padding: 1rem;
  gap: 0.5rem;
}
.toggle {
  color: rgb(0, 172, 100);
}
</style>
