<!-- src/components/Muro.vue -->
<template>
  <div class="muro">
    <!-- Caja para compartir -->
    <div class="post-box">
      <textarea
        v-model="nuevoPost"
        placeholder="¿Qué estás pensando?"
        rows="3"
      ></textarea>
      <button class="btn" @click="compartirPost">Compartir</button>
    </div>

    <!-- Lista de publicaciones -->
    <PostsList :posts="posts" />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import PostsList from './PostsList.vue'

// Lista de publicaciones iniciales
const posts = ref([
  {
    user: 'ROSA ISELA',
    time: 'Lunes a las 8:45pm',
    text: 'ME ENCANTA 👍',
    comments: 6,
    image: '/src/assets/mujer.jpg'
  },
  {
    user: 'ALEJANDRO CARABALI',
    time: 'Lunes a las 11:46pm',
    text: 'ME COMPRÉ MI GUITARRA...',
    comments: 0,
    image: '/src/assets/perfil.png'
  }
])

// Texto del nuevo post
const nuevoPost = ref('')

// Función para compartir nuevo post
function compartirPost() {
  if (!nuevoPost.value.trim()) {
    alert('Escribe algo antes de compartir.')
    return
  }

  const fecha = new Date()
  const hora = fecha.toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' })
  const dia = fecha.toLocaleDateString('es-ES', { weekday: 'long' })

  // Crear nuevo post
  const nuevo = {
    user: 'Alejandro Carabali',
    time: `${dia} a las ${hora}`,
    text: nuevoPost.value,
    comments: 0,
    image: '/src/assets/perfil.png'
  }

  // Agregarlo arriba en la lista
  posts.value.unshift(nuevo)

  // Limpiar textarea
  nuevoPost.value = ''
}
</script>

<style scoped>
.muro {
  width: 100%;
  padding: 10px;
}

.post-box {
  background: #f7f7f7;
  padding: 10px;
  border-radius: 5px;
  margin-bottom: 20px;
}

textarea {
  width: 100%;
  border: 1px solid #ccc;
  border-radius: 3px;
  padding: 8px;
  margin-bottom: 10px;
  resize: none;
}

.btn {
  background-color: #4267b2;
  color: white;
  border: none;
  border-radius: 4px;
  padding: 6px 15px;
  cursor: pointer;
}

.btn:hover {
  background-color: #365899;
}
</style>

