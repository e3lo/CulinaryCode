

<template>
  <v-parallax height="400" :src="parallaxLink" />
  <div class="setup">
    <div class="body">
      <div class="heading">
        <h1>Winter Recipes</h1>
        <p>Have a look at our amazing winter selection of heart warming recipes! Perfect for the cold winter nights and the toasty get togethers around the family dining</p>
      </div>
      <v-card text="..."></v-card>
    </div>
  </div>
</template>

<script setup>
import parallaxLink from '@/assets/static/winterRoad.jpg';
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