<script setup>
import SServiceCard from '@/components/SServiceCard.vue'
import { useRouter } from 'vue-router'

import { ref } from 'vue'

const router = useRouter()

const goToBook = () => {
  router.push('booking')
}

const haircuts = ref([
  {
    id: 0,
    pic: 'https://placehold.co/300x200/94A3B8/FFFFFF?text=Executive+Cut',
    title: 'The Executive Cut',
    description:
      'A tailored haircut including consultation, precision cutting, wash, scalp massage, and styling. Perfect for the modern professional seeking a sharp, refined look.',
    duration: 'Duration: Approx. 45 mins',
    price: '55',
  },
  {
    id: 1,
    pic: 'https://placehold.co/300x200/94A3B8/FFFFFF?text=Classic+Cut',
    title: 'Classic Haircut',
    description:
      'A traditional haircut focusing on clean lines and timeless style. Includes cut and basic styling.',
    duration: 'Duration: Approx. 30 mins',
    price: '45',
  },
  {
    id: 2,
    pic: 'https://placehold.co/300x200/94A3B8/FFFFFF?text=Modern+Fade',
    title: 'Modern Fade & Style',
    description:
      'Expertly executed fades (low, mid, high, skin fade) combined with modern styling techniques for a sharp, contemporary look.',
    duration: 'Duration: Approx. 60 mins',
    price: '60',
  },
])

const beardcuts = ref([
  {
    id: 3,
    pic: 'https://placehold.co/300x200/94A3B8/FFFFFF?text=Beard+Sculpt',
    title: 'Deluxe Beard Grooming',
    description:
      'Comprehensive beard care including trimming, shaping, lining with a straight razor, hot towel treatment, and conditioning with premium beard oils/balms.',
    duration: 'Duration: Approx. 45 mins',
    price: '40',
  },
  {
    id: 4,
    pic: 'https://placehold.co/300x200/94A3B8/FFFFFF?text=Beard+Trim+Simple',
    title: 'Precision Beard Trim',
    description:
      'Keep your beard looking sharp with a professional trim and line-up. Focuses on shape and neatness.',
    duration: 'Duration: Approx. 30 mins',
    price: '30',
  },
])

const shaves = ref([
  {
    id: 5,
    pic: 'https://placehold.co/300x200/94A3B8/FFFFFF?text=Hot+Shave',
    title: 'Traditional Hot Towel Shave',
    description:
      'The ultimate shaving experience. Includes pre-shave oils, multiple hot towels, rich lather, a close straight razor shave, and post-shave balm for smooth, refreshed skin.',
    duration: 'Duration: Approx. 45 mins',
    price: '50',
  },
])
</script>

<template>
  <div class="sections">
    <section class="groom-section">
      <div class="groom cSpacing">
        <h1>Our Grooming Services</h1>
      </div>
    </section>

    <section class="services-section">
      <div class="services cSpacing">
        <h2>Haircuts</h2>
        <SServiceCard
          class="serviceCard dShadow emph"
          v-for="service in haircuts"
          :key="service.id"
          :service="service"
        />
        <h2>Beard Care</h2>
        <SServiceCard
          class="serviceCard dShadow emph"
          v-for="service in beardcuts"
          :key="service.id"
          :service="service"
        />
        <h2>Shaves</h2>
        <SServiceCard
          class="serviceCard dShadow emph"
          v-for="service in shaves"
          :key="service.id"
          :service="service"
        />
      </div>
    </section>
    <section class="book-section">
      <div class="book cSpacing">
        <h1>Ready to look your best?</h1>
        <p>Book your preferred service today and experience the Timeless Trims difference.</p>
        <button class="tButton" @click="goToBook">Book Appointment Now</button>
      </div>
    </section>
  </div>
</template>

<style scoped>
.book-section {
  background-color: #f59e0b;
  padding-top: 3rem;
  padding-bottom: 4.5rem;
  text-align: center;
  h1 {
    font-size: 2rem;
  }
  p {
    font-size: 1.25rem;
  }
}
.tButton {
  font-weight: 600;
  width: 19rem;
  color: #fff;
  height: 4rem;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 1.25rem;
  border-radius: 8px;
  border: none;
  margin-top: 1rem;
  transition:
    background-color 0.15s ease-in-out,
    transform 0.1s ease-in-out;
  cursor: pointer;
  background-color: #1e293b;
}

.tButton:hover {
  background-color: #0f172a;
}

.tButton:active {
  background-color: #000;
  transform: translateY(1px);
}

.groom-section {
  background-color: #334155;
  h1 {
    text-align: center;
    margin: 0px;
    color: #fff;
    font-size: 3rem;
    padding: 4rem 0rem 4rem;
  }
}

.services-section {
  padding-top: 3rem;
  padding-bottom: 6rem;
  background-color: #f8fafc;
}

.services {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.services h2 {
  font-size: 1.875rem;
  font-weight: 700;
  color: #1e293b;
  margin-top: 2rem;
  margin-bottom: 1rem;
  border-bottom-width: 2px;
  border-bottom-style: solid;
  border-bottom-color: #f59e0b;
  padding-bottom: 0.5rem;
  display: inline-block;
  align-self: flex-start;
}
</style>
