<script setup>
import BlogPost from './components/BlogPost.vue';
import ButtonCounter from './components/ButtonCounter.vue';
</script>

<template>
  <div class="container">
  <h1>App</h1>
  <ButtonCounter></ButtonCounter>
  <button-counter></button-counter>
  <BlogPost title= "Post 1" id="1" body="description 1" colorText="primary"></BlogPost>
  <BlogPost title= "Post 2" id="2" body="description 2" colorText="secondary"></BlogPost>
  <BlogPost title= "Post 3" id="3" body="description 3" colorText="success"></BlogPost>
  <BlogPost title= "Post 7" id="7" body="description 7" colorText="primary"></BlogPost>
  </div>
</template>


