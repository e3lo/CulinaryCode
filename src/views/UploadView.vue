<template>
    <div class="setup card">
      <v-form @submit.prevent="checkRecipe">

        <v-text-field v-model="title" label="Title"></v-text-field>
        <v-text-field v-model="duration" label="Duration" suffix="Hrs"></v-text-field>
        <v-textarea v-model="description" label="Description"></v-textarea>
        <v-text-field v-model="link" label="Image link"></v-text-field>
        
        <h2>Recipe instructions</h2>
        <v-textarea
        v-for="(step, index) in steps"
        :key="index"
        v-model="steps[index]"
        :label="'Step ' + (index + 1)"
        ></v-textarea>
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
const steps = ref(["Do this", 'Then do this', 'Finally do that'])

const submitSuccess = ref(false)

console.log(submitSuccess)

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
      link : link.value,
      steps : steps.value,
    }

    saveRecipe(recipeObject)
  }
}

function saveRecipe(object) {
  const jsonValue = JSON.stringify(object)
  localStorage.setItem(object.id, jsonValue)
  submitSuccess.value = true
}
</script>
  
<style>
.card {
  margin: auto;
  max-width: 600px;
}
</style>
  