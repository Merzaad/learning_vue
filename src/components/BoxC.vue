<script setup lang="ts"></script>
<template>
  <div class="box"><slot /></div>
</template>

<style scoped>
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
</style>
