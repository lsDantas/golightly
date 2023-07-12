<script setup>
import { ref, onMounted } from 'vue';

const id = ref(undefined);
const name = ref(undefined);
const definition = ref(undefined);
const flipped = ref(false);

const fetchNextCard = async () => {
  const response = await fetch(`${import.meta.env.VITE_API_URL}/retrieve-next`);
  const newCard = await response.json();

  if (newCard) {
    id.value = newCard.id;
    name.value = newCard.name
    definition.value = newCard.definition
  } else {
    id.value = undefined;
    name.value = undefined;
    definition.value = undefined;
  }

  flipped.value = false;
}

const upgradeCard = async () => {
  const response = await fetch(`${import.meta.env.VITE_API_URL}/upgrade/${id.value}`);
  console.log('Response: ', response);

  await fetchNextCard();
};

const downgradeCard = async () => {
  const response = await fetch(`${import.meta.env.VITE_API_URL}/downgrade/`);
  console.log('Response: ', response);

  await fetchNextCard();
}

onMounted(() => {
  fetchNextCard();
});

</script>

<template>
  <div class="card-container">
    <div class="card-content">
      <h2>{{ name }}</h2>
      <br />
      <div v-if="flipped">
        {{ definition }}
      </div>
    </div>
    <div class="card-buttons">
      <button @click="flipped = !flipped">Flip</button>
      <br />
      <div v-if="flipped" class="flipped-buttons-container">
        <button @click="upgradeCard">Got it.</button>
        <button @click="downgradeCard">Didn't get it.</button>
      </div>
    </div>
    
  </div>
</template>

<style>
  .card-container {
    display: flex;
    align-items: center;
    flex-direction: column;
    padding-top: 50px;
  }
  .card-content {
    min-width: 50%;
  }
  .card-buttons {
    display: flex;
    flex-direction: column;
    align-items: center;
    flex-grow: 1;
    padding-top: 30px;
  }

  .flipped-buttons-container {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    margin: 20px;
  }
  .flipped-button {
    padding: 10px;
  }
</style>