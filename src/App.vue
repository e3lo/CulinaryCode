<script setup>
import { RouterLink, RouterView } from 'vue-router'

function saveRecipe(object) {
  const jsonValue = JSON.stringify(object)
  localStorage.setItem(object.id, jsonValue)
}

</script>

<template>
  <header class="setup">
      <nav class="navigation">
        <div class="navigation__logo">
          <RouterLink to="/"><span class="playfair logo">Culinary</span><span class="logo">Code</span></RouterLink>
        </div>
        <div class="navigation__buttons">
          <RouterLink to="/">Home</RouterLink>
          <RouterLink to="/trending">Trending</RouterLink>
          <RouterLink to="/upload">Upload</RouterLink>
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

  a,
  .darkblue {
  text-decoration: none;
  color: #0E0E0F;
  transition: 0.4s;
  padding: 2px;
  font-weight: 700;
}

@media (hover: hover) {
  a:hover {
    background-color: hsla(40, 40%, 25%, 0.2);
  }
}
</style>
