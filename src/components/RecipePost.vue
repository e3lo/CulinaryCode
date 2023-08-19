<template>
    <div>
      <h1> Welcome to Post page </h1>
      <p>This is the page that opens on <strong>/blog/{{ $route.params.id }}</strong> {{ recipe }}</p>
    </div>
</template>

<script setup>
    import { computed } from 'vue'

    const props = defineProps({
        id : String,
    })

    const recipe = localStorage.getItem(props.id)
    if (recipe != null) {

    } else {
        console.log(props.id)
    }
    
</script>