<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    props: { dinosaur: String },
    data(): ComponentData {
        return { 
            dinosaurDetails: null 
        };
    },
    async mounted() {
        const res = await fetch(`http://localhost:8000/dinosaurs/${this.dinosaur}`);
        this.dinosaurDetails = await res.json();
    }
});
</script>

<template>
    <h1>{{ dinosaurDetails?.name }}</h1>
    <p>{{ dinosaurDetails?.description }}</p>
    <RouterLink to="/">🠠 Back to all dinosaurs</RouterLink>
</template>
