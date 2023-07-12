<script setup>
import { ref, onMounted } from 'vue';

const flashcards = ref([]);

const fetchCards = async () => {
  const response = await fetch(`${import.meta.env.VITE_API_URL}/retrieve-all`);
  const { flashcards: newFlashcards } = await response.json();

  flashcards.value = newFlashcards;
}

onMounted(() => {
  fetchCards();
});
</script>

<template>
  <ul v-if="flashcards.length">
    <li v-for="flashcard of flashcards" :key="flashcard.id">
      <div class="card-content">
        <h2>{{ flashcard.name }}</h2>
        <br />
        <div>
          {{ flashcard.definition }}
        </div>
      </div>
    </li>
  </ul>
</template>

<style>
  .card-content {
    min-width: 50%;
    padding: 10px;
  }
</style>