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
      <h4>{{ service.job }}</h4>
      <p class="description">{{ service.description }}</p>
      <p class="skills">{{ service.skills }}</p>
      <button @click="goToBook">Book This Service</button>
    </div>
  </div>
</template>

<style scoped>
.card {
  background-color: #fff;
  font-family: sans-serif;
  overflow: hidden;
  text-align: center;
  display: flex;
  flex-direction: column;
  height: 100%;
}

.card-header {
  background-color: #4a5568;
  color: white;
  text-align: center;
  flex-shrink: 0;

  img {
    width: 100%;
    height: 18rem;
    object-fit: cover;
  }
}

.card-header h2 {
  margin: 0;
  font-size: 1.25rem;
}

.card-body {
  padding: 1.5rem;
  display: flex;
  flex-direction: column;
  flex-grow: 1;
}

.card-body h3 {
  margin: 0;
  font-size: 1.5rem;
}
.card-body h4 {
  margin-top: 1rem;
  font-size: 1.25rem;
  color: #e19500;
}

.description {
  font-size: 1rem;
  color: #555;
  margin-bottom: 16px;
}

.skills {
  font-size: 1rem;
  font-weight: bolder;
  margin-top: 2rem;
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
