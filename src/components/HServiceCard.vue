<script setup>
defineProps({
  service: {
    type: Object,
    required: true,
  },
})

import { useRouter } from 'vue-router'

const router = useRouter()

const goToBook = () => {
  router.push('booking')
}
</script>

<template>
  <div class="card">
    <div class="card-header">
      <img :src="service.pic" />
    </div>
    <div class="card-body">
      <h3>{{ service.title }}</h3>
      <p class="description">{{ service.description }}</p>
      <p class="price">${{ service.price }}</p>
      <button @click="goToBook">Book This Service</button>
    </div>
  </div>
</template>

<style scoped>
.card {
  background-color: #fff;
  font-family: sans-serif;
  overflow: hidden;
}

.card-header {
  background-color: #8ca0b3;
  color: white;
  text-align: center;

  img {
    width: 100%;
    height: 15rem;
    object-fit: cover;
  }
}

.card-header h2 {
  margin: 0;
  font-size: 1.25rem;
}

.card-body {
  padding: 2rem;
}

.card-body h3 {
  margin: 0;
  font-size: 1.4rem;
}

.description {
  font-size: 1rem;
  color: #555;
  margin-bottom: 16px;
}

.price {
  font-size: 1.2rem;
  font-weight: bolder;
  color: #e19500;
  margin-bottom: 16px;
}

button {
  width: 100%;
  padding: 1rem;
  background-color: #314361;
  color: white;
  font-weight: bolder;
  font-size: 1rem;
  border: none;
  border-radius: 0.5rem;
  cursor: pointer;
  transition: background-color 0.2s ease;
  margin-top: 0.5rem;
}

button:hover {
  background-color: #1e293b;
}
</style>
