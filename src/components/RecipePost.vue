<template>
    <div id="color-block"></div>
    <div class="setup main">
    <div class="header">
        <h1> {{ recipe.title }} </h1>
        <p> {{ recipe.description }}</p>
    </div>
    

    <div class="image-stat">
        <div class="image-stat__top-bar">
            <p><b>Very difficult</b></p>
            <p><b>{{ recipe.duration }} Hrs </b></p>
        </div>
        <v-img :src="recipe.link" :max-height="500" cover></v-img>
    </div>

    <div class="steps">
        <div class="steps__heading">
            <h1>Steps</h1>

            {{ recipe.preInstruction }}
        </div>

        <StepsComponent v-for="items in recipe.steps" :item="items"/>
    </div>
    
    </div>
</template>

<script setup>
    import { computed, ref } from 'vue'
    import StepsComponent from './StepsComponent.vue';

    const props = defineProps({
        id : String,
    })

    const rating = ref(3)

    const recipe = JSON.parse(localStorage.getItem(props.id))
</script>

<style scoped>
#color-block {
    background: #8E5858; 
    height: 200px;
    width: 100%;
}

.main {
    margin: 2em;
    transform: translateY(-100px);
    background-color: #F2F2ED;
    padding: 2em;
    padding-top: 3em;
}

@media (min-width: 1280px) {
  .main {
    margin: auto;
  }
}

.header {
    text-align: center;
    padding-bottom: 2em;
    max-width: 600px;
    margin: auto;
}

.image-stat {
    max-width: 800px;
    margin: auto;
    padding-bottom: 2em;
}
.image-stat__top-bar {
    display: flex;
    justify-content: space-between;
}

.steps {
    max-width: 800px;
    margin: auto;
}

.steps__heading {
    text-align: center;
}

.steps__ol {
    list-style: inside decimal;
}

li {
    margin-bottom: 2em;
}
</style>