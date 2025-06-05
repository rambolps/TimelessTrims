<script setup>
import { RouterLink } from 'vue-router'
</script>

<template>
  <footer>
    <div id="outer" class="cSpacing">
      <div id="top">
        <div id="left">
          <h6>Timeless Trims</h6>
          <p>155 Metcalfe Street, Ottawa, ON K2P 1P4</p>
          <p>(613) 555-0189</p>
          <p>bookings@timelesstrims.ca</p>
        </div>
        <div id="middle">
          <h6>Operating Hours</h6>
          <p>Monday - Friday: 9 AM - 7 PM</p>
          <p>Saturday: 10 AM - 5 PM</p>
          <p>Sunday: Closed</p>
        </div>
        <div id="right">
          <h6>Quick Links</h6>
          <RouterLink to="/services"><p class="route">Services</p></RouterLink>
          <RouterLink to="/barbers"><p class="route">Our Barbers</p></RouterLink>
          <RouterLink to="/booking"><p class="route">Book Appointment</p></RouterLink>
          <RouterLink to="/contact"><p class="route">Contact Us</p></RouterLink>
        </div>
      </div>
      <div id="bottom">
        <p>© 2025 Timeless Trims. All Rights Reserved.</p>
        <p>Designed By: Mathias Cheung & Ryan Rambali</p>
        <a
          href="https://www.google.com/maps/search/?api=1&query=155+Metcalfe+Street,+Ottawa,+ON+K2P+1P4"
          >View on Google Maps</a
        >
      </div>
    </div>
  </footer>
</template>

<style scoped>
footer {
  background-color: #0f172a;
}

h6 {
  color: #fff;
  font-size: 1.25em;
  margin-bottom: 0px;
}

#top {
  display: grid;
  gap: 2rem;
  margin-bottom: 2rem;
  text-align: left;
  padding-bottom: 1rem;
  border-bottom: 1px solid #334155;
}

p {
  color: #cbd5e1;
}

#right a {
  text-decoration: none;
  color: #cbd5e1;
}

@media (min-width: 768px) {
  #top {
    grid-template-columns: repeat(3, minmax(0, 1fr));
  }
}

#bottom {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.75rem;
  padding-bottom: 2rem;
}

#bottom p {
  margin-top: 0;
  margin-bottom: 0;
}

#bottom a {
  text-decoration: none;
  color: #cbd5e1;
}

#bottom a:hover {
  color: #e08900;
}

.route:hover {
  color: #ff9c07;
}
</style>
