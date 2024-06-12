<script setup lang="ts">
import { RouterView } from 'vue-router'
import AppHeader from './components/AppHeader.vue'
import AppFooter from './components/AppFooter.vue'
</script>

<template>
  <div>
    <AppHeader />
    <main class="container mt-5 pt-5"><RouterView /></main>
    <AppFooter />
  </div>
</template>

<style scoped></style>
