<script setup>
import ServiceCard from '@/components/ServiceCard.vue'
import { useRouter } from 'vue-router'
import { ref } from 'vue'

const router = useRouter()

const goToBook = () => {
  router.push('booking')
}

const goToServices = () => {
  router.push('services')
}

const goToBarbers = () => {
  router.push('barbers')
}

const services = ref([
  {
    id: 0,
    pic: 'https://placehold.co/600x400/94A3B8/FFFFFF?text=Classic+Haircut',
    title: 'Classic Haircut',
    description: 'A timeless cut tailored to your style, includes wash and style.',
    price: '45',
  },
  {
    id: 1,
    pic: 'https://placehold.co/600x400/94A3B8/FFFFFF?text=Beard+Trim',
    title: 'Beard Trim',
    description: 'A precise beard trim and edge shaping with hot towel finish.',
    price: '25',
  },
  {
    id: 2,
    pic: 'https://placehold.co/600x400/94A3B8/FFFFFF?text=Hot+Towel+Shave',
    title: 'Hot Towel Shave',
    description: 'A luxurious traditional shave with hot towels and premium products.',
    price: '60',
  },
])
</script>

<template>
  <div id="sections">
    <section class="intro-section">
      <div class="overlay"></div>
      <div class="intro-content">
        <h1>Timeless Trims: Precision Cuts, Modern Style.</h1>
        <div class="buttons">
          <button class="iButton" id="introB" @click="goToBook">Book Appointment Now</button>
          <button class="iButton" id="introS" @click="goToServices">Explore Our Services</button>
        </div>
      </div>
    </section>

    <section class="welcome-section">
      <div class="welcome cSpacing">
        <div id="wLeft">
          <h2>Experience the Timeless Trims Difference</h2>
          <p>
            Located at 155 Metcalfe Street, Timeless Trims offers a blend of classic barbering
            techniques and contemporary styling. Our skilled barbers are committed to providing
            exceptional service in a welcoming atmosphere.
          </p>
          <p>
            We pride ourselves on attention to detail and a personalized approach for every client.
          </p>
        </div>
        <div id="wRight">
          <img
            class="dShadow"
            src="https://placehold.co/600x400/E2E8F0/334155?text=Welcoming+Shop+Interior"
          />
        </div>
      </div>
    </section>

    <section class="service-section">
      <div class="cSpacing">
        <h2>Popular Services</h2>
      </div>
      <div class="services cSpacing">
        <ServiceCard
          class="serviceCard"
          v-for="service in services"
          :key="service.id"
          :service="service"
        />
      </div>
    </section>

    <section class="team-section">
      <div class="team cSpacing">
        <div id="tLeft">
          <img
            class="dShadow"
            src="https://placehold.co/600x400/E2E8F0/334155?text=Welcoming+Shop+Interior"
          />
        </div>
        <div id="tRight">
          <h2>Expert Hands, Personalized Style</h2>
          <p>
            Our team of experienced barbers is here to listen to your needs and deliver a look
            you'll love. We're passionate about the art of barbering and dedicated to client
            satisfaction.
          </p>
          <button class="tButton" @click="goToBarbers">Meet the Team</button>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.team-section {
  background-color: #1e293b;
}
.team {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding: 6rem;
  gap: 4rem;
}

#tRight {
  p {
    font-size: 1.5rem;
    text-align: left;
    color: #cbd5d2;
  }

  h2 {
    font-size: 2.5rem;
    font-weight: bolder;
    color: #fff;
  }

  justify-content: start;
  align-items: start;
}

.tButton {
  font-weight: 600;
  width: 15rem;
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
  background-color: rgb(245, 158, 11);
}

.tButton:hover {
  background-color: #e08900;
}

.tButton:active {
  background-color: #c97700;
  transform: translateY(1px);
}

.dShadow {
  border-radius: 0.5rem;
  box-shadow:
    0 20px 25px -5px rgba(0, 0, 0, 0.1),
    0 8px 10px -6px rgba(0, 0, 0, 0.1);
}

.service-section {
  background-color: #f1f5f9;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding-top: 3rem;
  padding-bottom: 5rem;
  width: 100%;

  h2 {
    font-size: 2.5rem;
    align-self: center;
    text-align: center;
  }
}

.serviceCard {
  border-radius: 1rem;
  transition: transform 0.3s ease;
}

.serviceCard:hover {
  transform: scale(1.05);
}

.services {
  display: grid;
  gap: 2rem;
}

@media (min-width: 640px) {
  .services {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }
}

@media (min-width: 1024px) {
  .services {
    grid-template-columns: repeat(3, minmax(0, 1fr));
  }
}

.welcome {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding: 6rem;
  gap: 2rem;
}

#wLeft p {
  font-size: 1.5rem;
  text-align: left;
}

#wLeft h2 {
  font-size: 2.5rem;
  font-weight: bolder;
}

#sections {
  display: flex;
  flex-direction: column;
}
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
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  align-content: center;
  z-index: 1;
}

.intro-content h1 {
  font-size: 4rem;
  font-weight: bold;
  margin-bottom: 1.5rem;
}

.buttons {
  display: flex;
  flex-direction: row;
  gap: 1rem;
}

.iButton {
  font-weight: 600;
  width: 20rem;
  height: 4rem;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 1.25rem;
  border-radius: 8px;
  margin-left: 1.25rem;
  transition:
    background-color 0.15s ease-in-out,
    transform 0.1s ease-in-out;
  cursor: pointer;
}

#introB {
  background-color: #ff9c07;
  color: #1e293b;
  border: none;
}

#introB:hover {
  background-color: #e08900;
}

#introB:active {
  background-color: #c97700;
  transform: translateY(1px);
}

#introS {
  border: 2px solid #fff;
  background-color: transparent;
  color: #fff;
}

#introS:hover {
  background-color: #fff;
  color: #1e293b;
  border: transparent;
}

#introS:active {
  background-color: #ccc;
  transform: translateY(1px);
}
</style>
