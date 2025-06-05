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
      <p class="duration">{{ service.duration }}</p>
      <p class="price">${{ service.price }}</p>
      <button @click="goToBook">Book This Service</button>
    </div>
  </div>
</template>

<style scoped>
.card {
  background-color: #fff;
  overflow: hidden;
  display: flex;
  flex-direction: row;
  padding: 2rem 0rem 2rem 2rem;
  gap: 2rem;
  border-radius: 0.5rem;
}

.card-header {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
  flex-basis: 33.3333%;

  img {
    width: 100%;
    height: 15rem;
    object-fit: cover;
    border-radius: 0.375rem;
  }
}

.card-body {
  font-size: 1.1rem;
  color: #555;
  margin: 0 0 0.25rem 0;
  flex-grow: 1;
}

.card-body h3 {
  margin: 0 0 0.25rem 0;
  font-size: 1.5rem;
}

.description {
  font-size: 1.1rem;
  color: #555;
  margin: 0 0 0.25rem 0;
  flex-grow: 1;
}

.duration {
  color: #94a3b8;
  font-size: 1rem;
  margin: 0 0 0.25rem 0;
}

.price {
  font-size: 1.2rem;
  font-weight: bolder;
  color: #e19500;
  margin-bottom: 1rem;
}

button {
  width: 100%;
  max-width: 12rem;
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
