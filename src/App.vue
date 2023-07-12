<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <div class="wrapper">
      <h1>Golightly</h1>
    </div>
  </header>

  <RouterView />

  <nav>
    <RouterLink to="/">Home</RouterLink>
    <RouterLink to="/admin">Admin</RouterLink>
  </nav>
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
  padding-top: 4rem;
  justify-content: center;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
  display: flex;
  flex-direction: row;
  justify-content: center;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: center;
    flex-wrap: wrap;
    font-family: 'Edu TAS Beginner', cursive;
    font-size: 32px;
  }

  nav {
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
