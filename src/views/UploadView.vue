<template>
    <div class="setup card">
      <v-form @submit.prevent="checkRecipe">

        <v-text-field v-model="title" label="Title"></v-text-field>
        <v-text-field v-model="duration" label="Duration" suffix="Hrs"></v-text-field>
        <v-textarea v-model="description" label="Description"></v-textarea>
        <v-text-field v-model="link" label="Image link"></v-text-field>
        
        <h2>Recipe instructions</h2>

        <div class="steps">
          <div class="steps__row" v-for="(step, index) in steps">
            <v-textarea
              :key="index"
              v-model="steps[index].instruction"
              :label="'Step ' + (index + 1)"
            ></v-textarea>
            <v-combobox label="Media Type" :items="['Instructions', 'Ingredients']" v-model="steps[index].type"></v-combobox>
          </div>
        </div>

        <v-row>
          <v-col cols="auto">
            <v-btn @click="removeStep" variant="tonal">Remove Step</v-btn>
          </v-col>

          <v-col cols="auto">
            <v-btn @click="addStep">Add Step</v-btn>
          </v-col>
        </v-row>
        <v-row>
          <v-col>
            <v-alert 
            type="success"
            title="Successfully Uploaded"
            text="You can now go to the home page and view your recipe submission"
            v-if="submitSuccess"
            ></v-alert>
            <v-btn type="submit" block color="#E9FEDF">submit</v-btn>
          </v-col>
        </v-row>
        
      </v-form>
    </div>
</template>

<script setup>
import { ref } from 'vue'

const title = ref('')
const duration = ref('')
const description = ref('')
const link = ref('')
const steps = ref([
  {
    instruction : "Do this",
    type : "Instructions"
},
{
    instruction : "Do this",
    type : "Instructions"
},
{
    instruction : "Do this",
    type : "Instructions"
},
])

const submitSuccess = ref(false)

console.log(submitSuccess)

function addStep() {
  steps.value.push({
    instruction : "",
    type : ""
},)
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
      link : link.value,
      steps : steps.value,
    }

    saveRecipe(recipeObject)
  }
}

function saveRecipe(object) {
  const jsonValue = JSON.stringify(object)
  console.log(jsonValue)
  localStorage.setItem(object.id, jsonValue)
  submitSuccess.value = true
}
</script>
  
<style>
.card {
  margin: auto;
  max-width: 800px;
}

.steps__row {
  display: grid;
  grid-template-columns: 3fr 1fr;
  column-gap: 1em;
}
</style>
  