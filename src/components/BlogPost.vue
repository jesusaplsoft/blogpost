<script setup>
import { defineProps, defineEmits } from "vue";


// defineProps(['title', 'id', 'body', 'colorText'])
defineProps({
    title: String,
    id: Number,
    body: {
        type: String,
        default: "Sin descripción"
    },
})
const emit = defineEmits(['cambiarFavoritoNombre'])
</script>

<template>
    <div class="card">
        <div class="card-body">
            <h5 class="card-title"> {{ id }} - {{ title }}</h5>
            <p class="card-text">{{ body }}</p>
            <button @click="emit('cambiarFavoritoNombre', title)"
                class="btn btn-sm btn-outline-primary">Favorito</button>
        </div>
    </div>
</template>
