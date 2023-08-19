<script setup>
import { RouterLink, RouterView } from 'vue-router'

function saveRecipe(object) {
  const jsonValue = JSON.stringify(object)
  localStorage.setItem(object.id, jsonValue)
}

let recipeObject = {
    id : "Boeuf Bourguignon",
    title : "Boeuf Bourguignon",
    duration : "3",
    description : "The recipe for the traditional braise of Burgundy may have changed slightly, but one ingredient remains non-negotiable: a bottle of the region's red wine.",
    link : "https://images-gmi-pmc.edge-generalmills.com/42fb4d81-8d92-40e2-9f0a-524edce5ca74.jpg",
    steps : ["Preheat oven to 150C. Heat half the oil in a casserole over medium heat, add speck and stir occasionally until golden (5-7 minutes).", "Remove from casserole and set aside. Reduce heat to low, add shallots and stir occasionally until golden (15-17 minutes).", "Remove from casserole and set aside. Increase heat to high, then, working in batches, toss beef in seasoned flour, shaking off excess, add to pan and turn occasionally until well browned (3-4 minutes).", "Remove from pan, set aside and repeat with remaining beef. Reduce heat to medium, add wine, stock, herbs, garlic and beef, bring to the simmer, season to taste, cover and braise in oven for 45 minutes.", "Add speck and shallots and braise until shallots and beef are very tender (45 minutes-1 hour).", "Meanwhile, heat butter and remaining oil in a frying pan over medium-high heat, add mushrooms, stir occasionally until golden (3-4 minutes)", "Then season to taste. Serve beef topped with mushrooms, with hot crusty baguette and buttered steamed potatoes."],
  }

saveRecipe(recipeObject)

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
