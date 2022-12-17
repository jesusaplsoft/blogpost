<script setup>
import { ref } from 'vue'

import ButtonCounter from './components/ButtonCounter.vue'
import BlogPost from './components/BlogPost.vue'
import PaginatePost from './components/PaginatePost.vue'
import LoadingSpinner from './components/LoadingSpinner.vue'

const loading = ref(true)

const posts = ref([])
const postxpage = 10
const inicio = ref(0)
const fin = ref(postxpage)

const favorito = ref('')
const cambiarFavorito = title => favorito.value = title

const next = () => {
    inicio.value += postxpage
    fin.value += postxpage
}
const prev = () => {
    inicio.value -= postxpage
    fin.value -= postxpage
}

fetch("https://jsonplaceholder.typicode.com/posts")
    .then(res => res.json())
    .then(data => posts.value = data)
    .catch(error => console.log(error))
    .finally(() => loading.value = false)
</script>

<template>
    <div class="container">
        <LoadingSpinner v-if="loading"/>
        <h1>APP</h1>
        <h2>Mi Post Favorito: {{ favorito }}</h2>

        <PaginatePost @next="next" @prev="prev" :inicio="inicio" :fin="fin" :postSize="posts.length" class="mb-2" />

        <BlogPost v-for="post in posts.slice(inicio, fin)" :key="post.id" :title="post.title" :id="post.id"
            :body="post.body" @cambiarFavoritoNombre="cambiarFavorito" class="mb-2">
        </BlogPost>
    </div>
</template>