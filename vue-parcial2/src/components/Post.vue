<template>
  <div class="post">
    <p><strong>{{ user }}</strong> - {{ time }}</p>
    <p>{{ text }}</p>
    <a v-if="comments" href="#">Ver los {{ comments }} comentarios</a>
    <div v-for="(img, i) in images" :key="i">
      <img :src="img" alt="Imagen del post" />
    </div>
  </div>
</template>

<script setup>
defineProps({
  user: String,
  time: String,
  text: String,
  comments: Number,
  images: Array
})
</script>
