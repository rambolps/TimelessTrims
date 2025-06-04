<script setup>
import { RouterLink, useRouter } from 'vue-router'

const router = useRouter()

const goToBook = () => {
  router.push('booking')
}

const goToHome = () => {
  router.push('/')
}
</script>

<template>
  <nav>
    <div id="topbar" class="cSpacing">
      <div>
        <h1 @click="goToHome">Timeless Trims</h1>
      </div>
      <div id="rightSide">
        <RouterLink to="/"><p class="route">Home</p></RouterLink>
        <RouterLink to="/services"><p class="route">Services</p></RouterLink>
        <RouterLink to="/barbers"><p class="route">Our Barbers</p></RouterLink>
        <RouterLink to="/contact"><p class="route">Contact Us</p></RouterLink>
        <button id="book" @click="goToBook">Book Now</button>
      </div>
    </div>
  </nav>
</template>

<style scoped>
#topbar {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
}

#rightSide {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
}

#book {
  margin-left: 1.25rem;
  background-color: #ff9c07;
  font-weight: 600;
  border: none;
  padding: 0.6rem 1.5rem;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 1.25rem;
  border-radius: 8px;
  color: #1e293b;
  transition:
    background-color 0.15s ease-in-out,
    transform 0.1s ease-in-out;
  cursor: pointer;
}

#book:hover {
  background-color: #e08900;
}

#book:active {
  background-color: #c97700;
  transform: translateY(1px);
}

.route {
  margin-left: 1.5rem;
  text-decoration: none;
  text-align: center;
  display: inline-block;
  font-size: 1.25rem;
  color: #fff;
  transition: color 0.3s ease-in-out;
  cursor: pointer;
}

.route:hover {
  color: #ff9c07;
}

a.router-link-exact-active > p.route {
  color: #ff9c07;
}

h1 {
  font-size: 2rem;
  cursor: pointer;
}

nav {
  background-color: #1e293b;
  color: #fff;
}
</style>
