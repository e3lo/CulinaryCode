

<template>
  <div class="hero">
    <div class="hero__header">
      <h1>Cooking, but simplified to code</h1>
      <p>Enjoy bloatless recipes where you don't need to scroll to Tasmania to find the recipe</p>
    </div>
    <img class="hero__image" :src="heroImage">
  </div>
  <div class="setup">
    <div class="body">
      <div class="heading">
        <h1>Winter Recipes</h1>
        <p>Have a look at our amazing winter selection of heart warming recipes! Perfect for the cold winter nights and the toasty get togethers around the family dining</p>
      </div>
      <RecipeCard v-for="(value, key) in parsedData" :id="value.id" :title="value.title" :cookingHours="value.duration" :description="value.description" :imageSrc="value.link" />
    </div>
  </div>
</template>

<script setup>
import heroImage from '@/assets/static/Saly-38.png';
import RecipeCard from '@/components/RecipeCard.vue'


const keys = Object.keys(localStorage);

const parsedData = {};

for (const key of keys) {
  try {
    parsedData[key] = JSON.parse(localStorage.getItem(key));
  } catch (error) {
    console.error(`Error parsing data for key '${key}':`, error);
  }
}

console.log(parsedData);
</script>

<style scoped>
.heading {
  text-align: center;
  padding-bottom: 2em;
  max-width: 600px;
  margin: auto;
}

.hero {
  height: 600px;
  background-color: #8E5858;
  display: flex;
  justify-content: center;
  align-items: center;
}

.hero__header {
  max-width: 400px;
  color: #F2F2ED;
  transform: translateY(-50px);
}

.hero__image {
  max-width: 500px;
}
.body {
  padding: 2em;
  padding-top: 3em;
  transform: translateY(-150px);
  background-color: #F2F2ED;
}

</style>