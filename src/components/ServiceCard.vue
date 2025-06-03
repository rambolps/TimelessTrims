<script setup>
defineProps({
  service: {
    type: Object,
    required: true,
  },
})
</script>

<template>
  <div class="card">
    <div class="card-header">
      <img src="" />
    </div>
    <div class="card-body">
      <h3>{{ service.title }}</h3>
      <p class="description">{{ service.description }}</p>
      <p class="price">${{ service.price }}</p>
      <button>Learn More & Book</button>
    </div>
  </div>
</template>

<style scoped>
.card {
  width: 300px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  overflow: hidden;
  background-color: #fff;
  font-family: sans-serif;
}

.card-header {
  background-color: #8ca0b3;
  color: white;
  text-align: center;
  padding: 24px 16px;
}

.card-header h2 {
  margin: 0;
  font-size: 24px;
}

.card-body {
  padding: 16px;
}

.card-body h3 {
  margin: 0 0 8px;
  font-size: 18px;
}

.description {
  font-size: 14px;
  color: #555;
  margin-bottom: 16px;
}

.price {
  font-size: 18px;
  font-weight: bold;
  color: #e19500;
  margin-bottom: 16px;
}

button {
  width: 100%;
  padding: 10px;
  background-color: #2e3b4e;
  color: white;
  font-weight: bold;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  transition: background-color 0.2s ease;
}

button:hover {
  background-color: #1f2b3a;
}
</style>
