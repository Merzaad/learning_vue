<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <div class="main">
    <div class="nav">
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
    <div class="outlet">
      <RouterView />
    </div>
  </div>
</template>

<style scoped>
.main {
  display: flex;
  height: 100%;
  padding: 1rem;
  gap: 1rem;
}
.nav {
  height: 100%;
}
nav {
  display: flex;
  flex-direction: column;
  align-items: center;
  background: rgb(53, 52, 52);
  height: 100%;
  width: min-content;
  overflow-y: auto;
  border-radius: 8px;
}
.nav a {
  padding: 0.5rem 1rem;
  width: 100%;
}
.outlet {
  flex-grow: 1;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow-y: auto;
}
</style>
