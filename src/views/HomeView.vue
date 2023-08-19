

<template>
  <v-parallax height="400" :src="parallaxLink" />
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
import parallaxLink from '@/assets/static/winterRoad.jpg';
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
.body {
  padding: 2em;
  padding-top: 3em;
  transform: translateY(-150px);
  background-color: #F2F2ED;
}

</style>