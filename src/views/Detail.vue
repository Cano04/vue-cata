<script setup>
import { ref, onMounted } from 'vue'

const props = defineProps({ id: String })

const producto = ref(null)
const error = ref('')

onMounted(async () => {
  try {
    const res = await fetch(`https://fakestoreapi.com/products/${props.id}`)
    if (!res.ok) throw new Error('Error ' + res.status)
    producto.value = await res.json()
  } catch (e) {
    error.value = 'No se pudo cargar el producto.'
  }
})
</script>

<template>
  <router-link to="/" class="back">← Volver al catálogo</router-link>

  <p v-if="error" class="error">{{ error }}</p>
  <p v-else-if="!producto">Cargando…</p>

  <article v-else class="detail">
    <img :src="producto.image" :alt="producto.title" />
    <div>
      <h1>{{ producto.title }}</h1>
      <p class="category">{{ producto.category }}</p>
      <p class="price">${{ producto.price.toFixed(2) }}</p>
      <p>{{ producto.description }}</p>
      <p class="rating">
        Valoración: {{ producto.rating.rate }} / 5 ({{ producto.rating.count }} reseñas)
      </p>
    </div>
  </article>
</template>
