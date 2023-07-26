<script setup lang="ts">
import BoxC from '@/components/BoxC.vue'
import ButtonC from '@/components/ButtonC.vue'
import { computed, onMounted, onUnmounted, ref, watch } from 'vue'

const Element = ref(null)
const watchedState = ref(0)
const toggleBorder = (event: KeyboardEvent) => {
  if (event.key === 'Enter') {
    // @ts-ignore
    Element.value.dataset.type = Element.value.dataset.type === '0' ? '1' : '0'
    alert('Enter')
  }
}
onMounted(() => {
  window.addEventListener('keypress', toggleBorder)
})
onUnmounted(() => window.removeEventListener('keypress', toggleBorder))
const computedState = computed(() => watchedState.value + 1)
watch(watchedState, (newState) => {
  console.log(watchedState.value, newState, computedState.value)
})
</script>

<template>
  <div class="lifecycle">
    <BoxC>
      <div data-type="0" ref="Element">press enter</div>
    </BoxC>
    <BoxC>
      {{ watchedState }}
      <ButtonC @click="watchedState++">watched</ButtonC>
    </BoxC>
  </div>
</template>

<style>
.lifecycle {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  gap: 1rem;
  width: 100%;
}
div[data-type='1'] {
  color: var(--color-green-light);
}
</style>
