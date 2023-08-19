<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
      <nav class="navigation">
        <div class="navigation__logo">
          <span>Culinary</span><span>Code</span>
        </div>
        <div class="navigation__buttons">
          <RouterLink to="/">Home</RouterLink>
          <RouterLink to="/trending">Trending</RouterLink>
          <RouterLink to="/login">Login</RouterLink>
        </div>

      </nav>
  </header>

  <RouterView />
</template>

<style scoped>
  .navigation {
    display: flex;
  }

  .navigation__logo {
    margin-right: auto;
  }

  .navigation__buttons {
    display: flex;
    gap: 2em;
  }

</style>
