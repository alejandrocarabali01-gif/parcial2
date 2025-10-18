<template>
  <div>
    <!-- Header principal -->
    <header class="header">
      <div class="logo">facebook</div>
      <input type="text" class="search-bar" placeholder="Buscar..." />
      <nav class="nav">
        <button @click="section = 'muro'">Muro</button>
        <button @click="section = 'info'">Info</button>
        <button @click="section = 'photos'">Fotos</button>
        <button @click="section = 'boxes'">Cajas</button>
      </nav>
    </header>

    <!-- Layout principal -->
    <div class="container">
      <!-- Sidebar izquierda -->
      <aside class="sidebar-left">
        <img src="/src/assets/perfil.png" alt="Perfil" class="perfil-img" />
        <h2 class="nombre">Alejandro Carabali</h2>
        <p class="info">Información</p>
        <p>info</p>
        <p>X Amigos</p>
        <div class="amigos">
          <div class="amigo"></div>
          <div class="amigo"></div>
          <div class="amigo"></div>
        </div>
        <a href="#">Ver todo</a>
      </aside>

      <!-- Contenido principal -->
      <main class="main-content">
        <component :is="currentSection" />
      </main>

      <!-- Sidebar derecha -->
      <aside class="sidebar-right">
        <div class="box">
          <p>Compartir algo</p>
          <button class="btn">Compartir</button>
        </div>
      </aside>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import Muro from './components/Muro.vue'
import Info from './components/Info.vue'
import Photos from './components/Photos.vue'
import Boxes from './components/Boxes.vue'


const section = ref('muro')

const currentSection = computed(() => {
  return {
    muro: Muro,
    info: Info,
    photos: Photos,
    boxes: Boxes
  }[section.value]
})
</script>


