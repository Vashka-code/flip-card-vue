<template>
  <main class="main">
    <cards-list :count="3" />
  </main>
</template>

<script setup lang="ts">
import CardsList from '../widgets/CardsList/CardsList.vue'
</script>

<style scoped>
.main {
  height: 100dvh;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #0c0e1c;
  background-image: url('./assets/bg.svg');
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
}
</style>
