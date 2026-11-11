<script setup>
import { ref, computed, onMounted } from 'vue'

const productos = ref([])
const busqueda = ref('')
const cargando = ref(true)
const error = ref('')

// Lista filtrada: se recalcula sola cuando cambia "busqueda" o "productos"
const filtrados = computed(() => {
  const q = busqueda.value.trim().toLowerCase()
  return q
    ? productos.value.filter(p => p.title.toLowerCase().includes(q))
    : productos.value
})

onMounted(async () => {
  try {
    const res = await fetch('https://fakestoreapi.com/products')
    if (!res.ok) throw new Error('Error ' + res.status)
    productos.value = await res.json()
  } catch (e) {
    error.value = 'No se pudo cargar el catálogo. Revisa tu conexión.'
  } finally {
    cargando.value = false
  }
})
</script>

<template>
  <input
    v-model="busqueda"
    type="search"
    class="search"
    placeholder="Buscar producto por nombre"
    aria-label="Buscar producto por nombre"
  />

  <p v-if="cargando">Cargando productos…</p>
  <p v-else-if="error" class="error">{{ error }}</p>
  <p v-else-if="!filtrados.length">Sin resultados para "{{ busqueda }}".</p>

  <ul class="grid">
    <li v-for="p in filtrados" :key="p.id">
      <router-link :to="{ name: 'detalle', params: { id: p.id } }" class="card">
        <img :src="p.image" :alt="p.title" loading="lazy" />
        <h2>{{ p.title }}</h2>
        <p class="price">${{ p.price.toFixed(2) }}</p>
      </router-link>
    </li>
  </ul>
</template>
