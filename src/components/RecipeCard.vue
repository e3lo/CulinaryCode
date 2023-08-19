<template>
    <div class="card">
        <div class="card__header">
            <h2 class="card__title">{{ title }}</h2>
            <p>{{ cookingHours }}Hrs</p>
        </div>

        <v-img max-height="400" cover :src="link"></v-img>
        <p>{{ description }}</p>
        
        <RouterLink :to="route"><button class="card__btn">See recipe</button></RouterLink>
    </div>
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
.card {
    margin:auto;
    background-color: #8E5858;
    color: #F2F2ED;
    padding: 1em 2em 2em 2em;
    max-width: 800px;
    border-radius: 20px;
    margin-bottom: 3em;
    display: flex;
    flex-direction: column;
    gap: 1em;
}

.card:hover {
    transition: 0.4s;
    box-shadow: 0px 4px 50px 0px rgba(0, 0, 0, 0.30);
}

.card__header {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.card__title {
    font-family: 'Playfair Display', serif;
    font-weight: 700;
    font-size: 36px;
    color: #F2F2ED;
}

.card__btn{
    margin-top: 1em;
    padding: 15px 90px 15px 90px;
    border-radius: 20px;
    background: #4B3232;
    color: #F2F2ED;
    transition: 0.4s;
}

.card__btn:hover{
    background: rgba(75, 50, 50, 0.60);
}
</style>