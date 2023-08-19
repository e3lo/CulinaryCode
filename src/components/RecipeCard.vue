<template>
    <v-card>
        <v-row align="center">
            <v-card-title>{{ title }}</v-card-title>
            <v-card-text>{{ cookingHours }}Hrs</v-card-text>
        </v-row>
        
        <v-img max-height="400" cover :src="link"></v-img>
        <v-card-text>{{ description }}</v-card-text>
        <v-btn @click="seeRecipe">See Recipe</v-btn>
    </v-card>
</template>

<script setup>
    import { reactive, computed } from 'vue'

    const props = defineProps({
        title: String,
        cookingHours: Number,
        description : String,
        imageSrc : String,
    })

    const link = computed(() => {
        return ("https://cdn.vuetifyjs.com/images/cards/cooking.png")
    })

    function seeRecipe(){
        console.log("Cliock")
    }
</script>

<style scoped>


</style>