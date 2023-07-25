<script setup lang="ts">
import { onMounted, onUnmounted, ref } from 'vue'

const refElement = ref(null)
const toggleBorder = (e: any) => {
  if (e.key === 'Enter') {
    // @ts-ignore
    refElement.value.dataset.type = refElement.value.dataset.type === '0' ? '1' : '0'
    console.log(refElement)
  }
}
onMounted(() => {
  window.addEventListener('keypress', toggleBorder)
})
onUnmounted(() => window.removeEventListener('keypress', toggleBorder))
</script>

<template>
  <div class="lifecycle" ref="refElement" data-type="0">press enter</div>
</template>

<style>
.lifecycle {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
}
div[data-type='1'] {
  border: 1px solid var(--color-green-light);
}
</style>
