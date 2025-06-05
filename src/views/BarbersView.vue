<script setup>
import BServiceCard from '@/components/BServiceCard.vue'
import { useRouter } from 'vue-router'

import { ref } from 'vue'

const router = useRouter()

const goToBook = () => {
  router.push('booking')
}

const barbers = ref([
  {
    id: 0,
    pic: 'https://cdn.shopify.com/s/files/1/0013/3536/1603/files/Barber_Leaning_On_Barber_Chair.jpg?v=1661358030',
    job: 'Master Barber',
    title: "Alex 'The Sharpenator' Johnson",
    description:
      'With over 10 years of experience, Alex is passionate about delivering clean, precise cuts that reflect your personal style. He excels in classic cuts and modern fades.',
    skills: 'Specialties: Classic Cuts, Fades, Beard Styling',
  },
  {
    id: 1,
    pic: 'https://images.squarespace-cdn.com/content/v1/57065ff84d088e7900c2f3f0/1464897378554-KFK07O095EBUS7N9H9E9/Ottawa-Headshot--12.jpg',
    job: 'Senior Barber',
    title: "Sarah 'The Stylist' Miller",
    description:
      'Sarah brings a creative flair to every cut. She loves working with clients to find new styles and is an expert in textured cuts and contemporary looks.',
    skills: 'Specialties: Modern Styles, Textured Cuts, Color',
  },
  {
    id: 2,
    pic: 'https://media.istockphoto.com/id/623477902/photo/man-gets-a-haircut-at-his-barber.jpg?s=612x612&w=0&k=20&c=Gxrsli5A3O5g2ptwsWwca3I39UP-KtexqoGXGYsgyhY=',
    job: 'Barber',
    title: "David 'The Detailer' Chen",
    description:
      "David is known for his meticulous attention to detail and his ability to craft perfectly sculpted beard trims and sharp lineups. He's also great with kids' cuts.",
    skills: "Specialties: Beard Grooming, Lineups, Kids' Cuts",
  },
])
</script>

<template>
  <div class="sections">
    <section class="title-section">
      <div class="title cSpacing">
        <h1>Meet Our Talented Barbers</h1>
        <p>
          Our team is passionate about barbering and dedicated to providing you with the best
          service and style.
        </p>
      </div>
    </section>

    <section class="barbers-section">
      <div class="barbers cSpacing">
        <BServiceCard
          class="barbersCard dShadow emph"
          v-for="service in barbers"
          :key="service.id"
          :service="service"
        />
      </div>
    </section>
  </div>
</template>

<style scoped>
.title-section {
  background-color: #334155;
  text-align: center;
  color: #fff;
  padding: 4rem 0rem 4rem;
  h1 {
    margin: 0px;
    font-size: 3rem;
  }
  p {
    font-size: 1.5rem;
  }
}

.barbersCard {
  flex: 1;
}
.barbers-section {
  padding-top: 3rem;
  padding-bottom: 6rem;
  background-color: #f8fafc;
}

.barbers {
  display: flex;
  flex-direction: row;
  gap: 1.5rem;
}

.barbers h2 {
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
