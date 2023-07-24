<script setup lang="ts">
import ButtonC from '@/components/ButtonC.vue'
import BoxC from '@/components/BoxC.vue'
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
const onInputChange = (e: any) => {
  input.value = e.target.value
}
const toggle = ref(false)
const array = ref([1, 2])
const object = ref<any>({ a: 1 })

const updateArrayWithDelay = () => {
  setTimeout(() => {
    array.value.push(1)
  }, 1500)
}
const updateObjectWithDelay = () => {
  setTimeout(() => {
    object.value.a++
  }, 1500)
}
</script>

<template>
  <div class="basic">
    <BoxC>
      {{ reactiveState.value }}
      <ButtonC @click="increase">reactive++</ButtonC>
    </BoxC>
    <BoxC>
      {{ refState }}
      <ButtonC @click="increase2">ref++</ButtonC>
    </BoxC>
    <BoxC>
      {{ array }}
      <ButtonC @click="array.push(1)">array.push</ButtonC>
      <ButtonC @click="array = [...array, 2]">[...array]</ButtonC>
      <ButtonC @click="updateArrayWithDelay">delay</ButtonC>
    </BoxC>
    <BoxC>
      {{ object }}
      <ButtonC @click="object.a++">object.b</ButtonC>
      <ButtonC @click="object = { ...object, b: 1 }">{...object}</ButtonC>
      <ButtonC @click="updateObjectWithDelay">delay</ButtonC>
    </BoxC>
    <BoxC>
      {{ input }}
      <input :value="input" @input="onInputChange" />
    </BoxC>
    <BoxC>
      <div v-if="toggle">toggled</div>
      <div v-else>not toggled</div>
      <ButtonC :class="toggle && 'toggle'" @click="toggle = !toggle">toggle</ButtonC>
    </BoxC>
  </div>
</template>

<style scoped>
.basic {
  display: flex;
  flex-direction: column;

  gap: 1rem;
}
.toggle {
  color: rgb(0, 172, 100);
}
</style>
