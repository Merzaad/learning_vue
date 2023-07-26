<script setup lang="ts">
import { watch } from 'vue'

const props = defineProps<{ text: string }>()
const emit = defineEmits(['textBack'])
watch(props, () => {
  emit('textBack', props.text.split('').reverse().join(''))
})
</script>

<template>
  <div>{{ text }}</div>
</template>
