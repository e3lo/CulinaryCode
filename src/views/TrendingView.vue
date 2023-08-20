<template>
  <div class="hero">
  </div>
  <div class="setup">
    <div class="body">
      <div class="heading">
        <h1>🔥Whats hot right now</h1>
        <p>See what everyone else is cooking up at the moment! These are some of the most popular and trendy dishes to bring out to the dining table</p>
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
  height: 200px;
  background-color: #8E5858;
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
  transform: translateY(-100px);
  background-color: #F2F2ED;
}

</style>