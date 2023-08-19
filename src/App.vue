<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
      <nav class="navigation">
        <div class="navigation__logo">
          <RouterLink to="/"><span class="playfair logo">Culinary</span><span class="logo">Code</span></RouterLink>
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
    align-items: center;
  }

  .navigation__logo {
    margin-right: auto;
  }

  .navigation__buttons {
    display: flex;
    gap: 2em;
  }

  .logo {
    font-weight: 700;
    font-size: 32px;
    color: #693232;
  }

</style>
