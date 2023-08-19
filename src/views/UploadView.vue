<template>
    <div class="setup card">
      <v-form @submit.prevent="checkRecipe">

        <v-text-field v-model="title" label="Title"></v-text-field>
        <v-text-field v-model="duration" label="Duration" suffix="Hrs"></v-text-field>
        <v-textarea v-model="description" label="Description"></v-textarea>
        
        <h2>Recipe instructions</h2>
        <v-textarea
        v-for="(step, index) in steps"
        :key="index"
        v-model="steps[index]"
        :label="'Step ' + (index + 1)"
        ></v-textarea>

        <v-btn @click="addStep">Add Step</v-btn>
        <v-btn @click="removeStep">Remove Step</v-btn>

        <h2> Final </h2>
        <v-btn type="submit">submit</v-btn>
      </v-form>
    </div>
</template>

<script setup>
import { ref } from 'vue'

const title = ref('')
const duration = ref('')
const description = ref('')

const steps = ref(["Do this", 'Then do this', 'Finally do that'])

function addStep() {
  steps.value.push("")
}

function removeStep() {
  steps.value.pop()
}

function checkRecipe() {
  let valid = true
  if (valid) {
    let recipeObject = {
      id : title.value, // Change this to remove conflicts
      title : title.value,
      duration : duration.value,
      description : description.value,
      steps : steps.value
    }

    saveRecipe(recipeObject)
  }
}

function saveRecipe(object) {
  const jsonValue = JSON.stringify(object)
  localStorage.setItem(object.id, jsonValue)
}
</script>
  
<style>
.card {
  margin: auto;
  max-width: 600px;
}
</style>
  