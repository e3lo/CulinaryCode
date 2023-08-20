<template>
    <v-img :src="arrowLink" height="50"></v-img>
    <div class="step-card instruction-card" v-if="instructionType">
        <h3>✅Instruction</h3>
        <p>{{ item['instruction'] }}</p>
    </div>

    <div class="step-card ingredient-card" v-if="ingredientType">
        <h3>🥦Add Ingredient</h3>
        <p>{{ item['instruction'] }}</p>
    </div>

</template>

<script setup>
import { ref } from 'vue'
import arrowLink from '@/assets/static/arrow.png'

const props = defineProps({
    item : Object,
})

console.log(props.item)
const instructionType = ref(false)
const ingredientType = ref(false)
const imageType = ref(false)

switch(props.item['type']) {
    case "Instructions":
        console.log(props.item['instruction'])
        instructionType.value = true
        break
    case "Ingredients":
        ingredientType.value = true
        break
}

</script>

<style scoped>
.step-card {
    background-color: white;
    padding: 2em;
    border-radius: 20px;
    margin-bottom: 2em;
    margin-top: 2em;
}

.ingredient-card {
    background: rgba(255, 255, 255, 0.50);
    margin-left: auto;
    margin-right: auto;
    max-width: 500px;
}

</style>