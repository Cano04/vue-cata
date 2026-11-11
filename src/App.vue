<script setup>

const marcaAgua = 'MOY (Modo Oscuro)'
</script>

<template>
  <header class="top">
    <router-link to="/" class="brand">CATALOGO VUE</router-link>
  </header>

  <main class="wrap">
    <router-view />
  </main>

  <footer class="watermark" aria-hidden="true">{{ marcaAgua }}</footer>
</template>