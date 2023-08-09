<script setup lang="ts">
import ButtonC from '@/components/ButtonC.vue'
import BoxC from '@/components/BoxC.vue'
import { reactive, ref, computed, watch } from 'vue'
import ComponentC from '@/components/ComponentC.vue'
let id = 0
const initialList = [
  { id: id++, a: 'o' },
  { id: id++, a: 'o' },
  { id: id++, a: 'o' }
]
const list = ref(initialList)
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
const componentEmit = ref('')
const onInputChange = (e: any) => {
  input.value = e.target.value
}
const toggle = ref(false)
const array = ref([1, 2])
const object = ref<any>({ a: 1, b: { x: 1 } })
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
const listLength = computed(() => list.value.length)
watch(object, (newValue, oldValue) => {
  console.log('object', oldValue, newValue)
})
watch(
  () => object.value.a,
  (newValue, oldValue) => {
    console.log('() => object.value.a', oldValue, newValue)
  }
)
watch(
  () => object.value.b.x,
  (newValue, oldValue) => {
    console.log('() => object.value.b.x', oldValue, newValue)
  }
)
watch(
  () => reactiveState.value,
  (newValue, oldValue) => {
    console.log('reactiveState.value', oldValue, newValue)
  }
)
watch(reactiveState, (newValue, oldValue) => {
  console.log('reactiveState', oldValue, newValue)
})
watch(refState, (newValue, oldValue) => {
  console.log('refState', oldValue, newValue)
})
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
      <ButtonC @click="object.a++">object.a++</ButtonC>
      <ButtonC @click="object = { ...object, b: 1 }">{...object}</ButtonC>
      <ButtonC @click="object.b.x++">object.b.x++</ButtonC>

      <ButtonC @click="updateObjectWithDelay">delay</ButtonC>
    </BoxC>
    <BoxC>
      {{ componentEmit }}
      <ComponentC :text="input" @text-back="(text) => (componentEmit = text)" />
      <input :value="input" @input="onInputChange" />
    </BoxC>
    <BoxC>
      <div v-if="toggle">toggled</div>
      <div v-else>not toggled</div>
      <ButtonC :class="toggle && 'toggle'" @click="toggle = !toggle">toggle</ButtonC>
    </BoxC>
    <BoxC>
      <ul class="list">
        <ButtonC v-if="list.length === 0" @click="list = initialList">reset</ButtonC>
        <li v-for="item in list" :key="item.id">
          {{ item.a }}
          <ButtonC @click="list = list.filter((i) => i.id !== item.id)">x</ButtonC>
        </li>
      </ul>
      length :
      {{ listLength }}
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
.list {
  padding-inline-start: 0;
}
</style>
