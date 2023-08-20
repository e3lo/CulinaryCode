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
          <RouterLink to="/"><span class="playfair logo"><i>Culinary</i></span><span class="logo">Code</span></RouterLink>
        </div>
        <div class="navigation__buttons">
          <RouterLink to="/">Home</RouterLink>
          <RouterLink to="/trending">Trending</RouterLink>
          <RouterLink to="/upload">Upload</RouterLink>
          <!--
            Removed as not finished
            <RouterLink to="/login">Login</RouterLink>
          -->
        </div>
      </nav>
  </header>
  <RouterView />
  <div class="footer">
    <span class="playfair logo light"><i>Culinary</i></span><span class="logo light">Code</span>
    <p class="light">© 2023 — CulinaryCode, LLC</p>
    
  </div>
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

  .light {
    color: white;
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

.footer {
  width: 100%;
  background-color: #8E5858;
  margin: auto;
  text-align: center;
  padding-top: 3em;  
  padding-bottom: 2em;
}
</style>
