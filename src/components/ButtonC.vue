<script setup lang="ts">
defineProps<{ onClick: any }>()
</script>

<template>
  <button class="ButtonC" @click="onClick"><slot /></button>
</template>

<style scoped>
.ButtonC {
  background: rgb(45, 45, 45);
  border: 1px solid rgb(82, 82, 82);
  color: rgb(184, 184, 184);
  cursor: pointer;
  border-radius: 4px;
  padding: 0.25rem;
  transition: background 0.2s, border-color 0.2s;
}
.ButtonC:hover,
.ButtonC:focus-visible {
  outline: none;
  background: var(--color-green-dark);
  border-color: var(--color-green-light);
}
.ButtonC:active {
  transform: scale(0.95);
}
</style>
