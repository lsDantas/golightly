<script setup>
import DeckPanel from '../components/DeckPanel.vue'
</script>

<template>
  <div class="admin">
    <DeckPanel />
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .admin {
    min-height: 100vh;
    display: flex;
    flex-direction: row;
    align-items: center;
  }
}
</style>
