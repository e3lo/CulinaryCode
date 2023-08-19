<template>
    <v-card>
        <v-row align="center">
            <v-card-title>{{ title }}</v-card-title>
            <v-card-text>{{ cookingHours }}Hrs</v-card-text>
        </v-row>
        
        <v-img max-height="400" cover :src="link"></v-img>
        <v-card-text>{{ description }}</v-card-text>
        <RouterLink :to="route">See recipe</RouterLink>
    </v-card>
</template>

<script setup>
    import { reactive, computed } from 'vue'

    const props = defineProps({
        id: String,
        title: String,
        cookingHours: String,
        description : String,
        imageSrc : String,
    })

    const route = `/recipe/${props.id}`

    const link = computed(() => {
        return (props.imageSrc)
    })
</script>

<style scoped>


</style>