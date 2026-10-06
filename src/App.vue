<script setup>
import { computed, ref } from 'vue';
import BlogPost from './components/BlogPost.vue';
import ButtonCounter from './components/ButtonCounter.vue';
import PaginatePost from './components/PaginatePost.vue';
const posts = ref([])
const favorito = ref("")
const posXpage = 10
const inicio = ref(0)
const fin = ref(posXpage)

const cambiarFavorito = (title) => {
  favorito.value=title
}

const next = () => {
  inicio.value = inicio.value + posXpage
  fin.value = fin.value + posXpage
}


const previus = () => {
  inicio.value = inicio.value - posXpage
  fin.value += - posXpage;
}

fetch('https://jsonplaceholder.typicode.com/posts')
.then((res) => res.json())
.then((data) => {posts.value = data} );

const maxLength = computed(() => posts.value.length )
</script>

<template>
  <div class="container">
  <h1>App</h1>
  <h2>Mis Post favorito : {{ favorito }}</h2>

  <PaginatePost @next="next" 
  @prev="previus" 
  :inicio="inicio" 
  :fin="fin" 
  :maxLength="maxLength"
  class="mb-2"/>

  <BlogPost 
  v-for="post in posts.slice(inicio, fin)"
  :key="post.id"
  :title= "post.title" 
  :id="post.id" 
  :body="post.body" 
  @cambiarFavoritoNombre="cambiarFavorito"
  class="mb-2"></BlogPost>
  </div>
</template>


