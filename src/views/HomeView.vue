<script setup>
import ServiceCard from '@/components/ServiceCard.vue'
import { ref } from 'vue'

const services = ref([
  {
    id: 0,
    pic: 'https://swungover.wordpress.com/wp-content/uploads/2013/09/annex-gable-clark_26.jpg',
    title: 'Classic Haircut',
    description: 'A timeless cut tailored to your style, includes wash and style.',
    price: '45',
  },
  {
    id: 1,
    pic: 'https://thebeardclub.com/cdn/shop/articles/how-to-trim-long-beard.jpg?v=1674046250&width=1920',
    title: 'Beard Trim',
    description: 'A precise beard trim and edge shaping with hot towel finish.',
    price: '25',
  },
  {
    id: 2,
    pic: 'https://hairsalonbarrie.ca/wp-content/uploads/2022/04/shave-thegem-blog-default.jpg',
    title: 'Hot Towel Shave',
    description: 'A luxurious traditional shave with hot towels and premium products.',
    price: '60',
  },
])
</script>

<template>
  <section class="intro-section">
    <div class="overlay"></div>

    <div class="intro-content">
      <h1>Timeless Trims: Precision Cuts, Modern Style.</h1>
      <div class="buttons">
        <RouterLink to="/booking">Book Appointment Now</RouterLink>
        <RouterLink to="/services">Explore Our Services</RouterLink>
      </div>
    </div>
  </section>

  <section class="service-section">
    <div class="services">
      <ServiceCard v-for="service in services" :key="service.id" :service="service" />
    </div>
  </section>

  <section class="team-section">
    <div class="team-image">
      <img src=" " />
    </div>

    <div class="team-content">
      <h2>Expert Hands, Personalized Style</h2>
      <p>
        Our team of experienced barbers is here to listen to your needs and deliver a look you'll
        love. We're passionate about the art of barbering and dedicated to client satisfaction.
      </p>
      <RouterLink to="/barbers">Meet the Team</RouterLink>
    </div>
  </section>
</template>

<style scoped>
.intro-section {
  position: relative;
  height: 50vh;
  background-image: url('https://images.unsplash.com/photo-1585747860715-2ba37e788b70?fm=jpg&q=60&w=3000&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8NHx8YmFyYmVyc2hvcHxlbnwwfHwwfHx8MA%3D%3D'); /* Replace with your image */
  background-size: cover;
  background-position: center;
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  overflow: hidden;
}

.overlay {
  position: absolute;
  inset: 0;
  background-color: black;
  opacity: 0.5;
  z-index: 1;
}

.intro-content {
  position: relative;
  z-index: 2;
  padding: 2rem;
}

.intro-content h1 {
  font-size: 2.5rem;
  font-weight: bold;
  margin-bottom: 1.5rem;
}

.buttons {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.buttons a {
  text-decoration: none;
  padding: 1rem 2rem;
  border-radius: 6px;
  font-weight: bold;
  font-size: 1rem;
  transition: background-color 0.2s ease;
}

.buttons .primary {
  background-color: #fbbf24; /* amber-500 */
  color: #1e293b; /* slate-900 */
}

.buttons .primary:hover {
  background-color: #f59e0b; /* amber-600 */
}

.buttons .secondary {
  background-color: transparent;
  border: 2px solid white;
  color: white;
}

.buttons .secondary:hover {
  background-color: white;
  color: #1e293b;
}

.team-section {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 60px 40px;
  background-color: #1c2532; /* dark blue-gray */
  color: #f1f5f9; /* light text */
  gap: 40px;
  flex-wrap: wrap;
}

.team-image {
  flex: 1;
  min-width: 300px;
}

.team-content {
  flex: 1;
  min-width: 300px;
}

.team-content h2 {
  font-size: 2rem;
  margin-bottom: 16px;
}

.team-content p {
  font-size: 1rem;
  line-height: 1.6;
  margin-bottom: 24px;
  color: #cbd5e1;
}

.team-button {
  background-color: #fbbf24; /* amber */
  color: #1c2532;
  padding: 12px 24px;
  text-decoration: none;
  border-radius: 6px;
  font-weight: bold;
  transition: background-color 0.2s ease;
}

.team-button:hover {
  background-color: #f59e0b;
}
</style>
