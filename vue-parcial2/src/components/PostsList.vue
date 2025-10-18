<!-- src/components/PostsList.vue -->
<template>
  <div class="posts">
    <div v-for="(post, index) in posts" :key="index" class="post">
      <p><strong>{{ post.user }}</strong> - {{ post.time }}</p>
      <p>{{ post.text }}</p>
      <img v-if="post.image" :src="post.image" alt="Imagen del post" />
      <a v-if="post.comments" href="#">Ver los {{ post.comments }} comentarios</a>
    </div>
  </div>
</template>

<script setup>
defineProps({
  posts: {
    type: Array,
    required: true
  }
})
</script>

<style scoped>
.post {
  background: #fff;
  border: 1px solid #ddd;
  border-radius: 5px;
  padding: 10px;
  margin-bottom: 15px;
}
.post img {
  width: 100%;
  max-width: 400px;
  border-radius: 5px;
  margin-top: 8px;
}
</style>
