<script setup>
import { useRouter } from 'vue-router'
import { ref } from 'vue'

import VueDatePicker from '@vuepic/vue-datepicker'
import '@vuepic/vue-datepicker/dist/main.css'

const router = useRouter()

const goToHome = () => {
  router.push('/')
}

let booking = ref({
  state: 1,
  service: '',
  barber: '',
  date: null,
  price: null,
  fullName: '',
})

const back = () => {
  booking.value.state--
  progressPercentage.value -= 25
}

const update1 = () => {
  var s = document.getElementById('services')
  booking.value.service = s.value

  if (s.value != '') {
    const selectedOption = s.options[s.selectedIndex]
    booking.value.price = selectedOption.getAttribute('data-price')
    booking.value.state = 2
    progressPercentage.value = 50
  }

  console.log(booking)
}

const update2 = () => {
  var b = document.getElementById('barbers')
  booking.value.barber = b.value

  booking.value.state = 3
  progressPercentage.value = 75

  console.log(booking)
}

const update3 = () => {
  booking.value.state = 4
  progressPercentage.value = 100
  console.log(booking)
}

const update4 = () => {
  var f = document.getElementById('fullName')
  booking.value.fullName = f.value

  var c = document.getElementById('agree_policy')
  if (c.checked) {
    booking.value.state = 5
    progressPercentage.value = 100
  } else {
    alert('Please Agree To The Cancellation Policy.')
  }
  console.log(booking)
}

const progressPercentage = ref(25)
</script>

<template>
  <div class="sections">
    <section class="title-section">
      <div class="title cSpacing">
        <h1>Book Your Appointment</h1>
      </div>
    </section>
    <section class="book-section">
      <div class="book ceSpacing">
        <div class="card">
          <p v-if="booking.state < 5" class="ptitle">Step {{ booking.state }} of 4</p>
          <p v-if="booking.state > 4" class="ptitle">Completed!</p>
          <div class="progress-bar-track">
            <div
              class="progress-bar-fill"
              :style="{ width: progressPercentage + '%' }"
              role="progressbar"
              :aria-valuenow="progressPercentage"
              aria-valuemin="0"
              aria-valuemax="100"
              :aria-label="'Progress: ' + progressPercentage + '%'"
            ></div>
          </div>
          <div v-if="booking.state == 1" class="state1">
            <h2>1. Select Service</h2>
            <p>Choose a service</p>
            <select name="services" id="services" class="bDropdown">
              <option value="">-- Select a Service --</option>
              <option value="Executive Cut" data-price="55" data-duration="45 min">
                The Executive Cut ($55, 45 min)
              </option>
              <option value="Classic Haircut" data-price="45" data-duration="30 min">
                Classic Haircut ($45, 30 min)
              </option>
              <option value="Modern Fade & Style" data-price="60" data-duration="60 min">
                Modern Fade & Style ($60, 60 min)
              </option>
              <option value="Deluxe Beard Grooming" data-price="40" data-duration="45 min">
                Deluxe Beard Grooming ($40, 45 min)
              </option>
              <option value="Precision Beard Trim" data-price="30" data-duration="30 min">
                Precision Beard Trim ($30, 30 min)
              </option>
              <option value="Traditional Hot Towel Shave" data-price="50" data-duration="45 min">
                Traditional Hot Towel Shave ($50, 45 min)
              </option>
            </select>
            <button class="nButton" @click="update1()">Next: Choose Barber</button>
          </div>

          <div v-if="booking.state == 2" class="state1">
            <h2>2. Select Barber</h2>
            <p>Choose a barber</p>
            <select name="barbers" id="barbers" class="bDropdown">
              <option value="Any Available Barber">Any Available Barber</option>
              <option value="Alex Johnson">Alex 'The Sharpenator' Johnson</option>
              <option value="Sarah Miller">Sarah 'The Stylist' Miller</option>
              <option value="David Chen">David 'The Detailer' Chen</option>
            </select>
            <div class="bottomButtons">
              <button class="bButton" @click="back()">Back</button>
              <button class="nButton" @click="update2()">Next: Pick Date & Time</button>
            </div>
          </div>

          <div v-if="booking.state == 3" class="state1">
            <h2>3. Select Date & Time</h2>
            <p>Choose an appointment time</p>
            <VueDatePicker v-model="booking.date" time-picker-inline :is-24="false" />
            <div class="bottomButtons">
              <button class="bButton" @click="back()">Back</button>
              <button class="nButton" @click="update3()">Next: Your Details</button>
            </div>
          </div>

          <div v-if="booking.state == 4" class="state1">
            <h2>4. Your Details & Confirmation</h2>
            <div class="tInGroup">
              <label for="full-name" class="tLabel">Full Name</label>
              <input
                type="text"
                name="fullName"
                id="fullName"
                autocomplete="name"
                class="tInput"
                placeholder="First Last"
              />
            </div>
            <div class="tInGroup">
              <label for="email" class="tLabel">Email</label>
              <input
                type="email"
                name="email"
                id="email"
                autocomplete="email"
                class="tInput"
                placeholder="yourname@email.ca"
              />
            </div>
            <div class="tInGroup">
              <label for="phoneNum" class="tLabel">Phone Number</label>
              <input
                type="tel"
                name="phoneNum"
                id="phoneNum"
                autocomplete="tel-national"
                class="tInput"
                placeholder="(613) 555-0123"
              />
            </div>
            <div class="tInGroup">
              <label for="notes" class="tLabel">Notes (Optional)</label>
              <input
                type="text"
                name="notes"
                id="notes"
                autocomplete="name"
                class="tInput"
                placeholder="Any specific requests or information for your barber..."
              />
            </div>
            <div class="summary-box">
              <h3 class="summary-title">Booking Summary</h3>
              <p class="summary-item">
                <strong>Service: </strong> <span id="summary-service">{{ booking.service }}</span>
              </p>
              <p class="summary-item">
                <strong>Barber: </strong>
                <span id="summary-barber">{{ booking.barber }}</span>
              </p>
              <p class="summary-item">
                <strong>Date &amp; Time: </strong>
                <span id="summary-datetime">{{ booking.date }}</span>
              </p>
              <p class="summary-total">
                <strong>Total Price: $</strong> <span id="summary-price">{{ booking.price }}</span>
              </p>
            </div>
            <div class="policy-agreement-container">
              <label class="policy-label">
                <input
                  type="checkbox"
                  id="agree_policy"
                  name="agree_policy"
                  class="policy-checkbox"
                />
                <span class="policy-text">I agree to the cancellation policy.</span>
              </label>
            </div>
            <div class="bottomButtons">
              <button class="bButton" @click="back()">Back</button>
              <button class="gButton" @click="update4()">Confirm Booking</button>
            </div>
          </div>

          <div v-if="booking.state == 5" class="state5">
            <svg
              class="success-icon"
              fill="none"
              stroke="currentColor"
              viewBox="0 0 24 24"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"
              ></path>
            </svg>
            <h2>Thank You, {{ booking.fullName }}!</h2>
            <p>The appointment is confirmed</p>
            <div class="summary-box">
              <h3 class="summary-title">Appointment Details</h3>
              <p class="summary-item">
                <strong>Service: </strong> <span id="summary-service">{{ booking.service }}</span>
              </p>
              <p class="summary-item">
                <strong>Barber: </strong>
                <span id="summary-barber">{{ booking.barber }}</span>
              </p>
              <p class="summary-item">
                <strong>Date &amp; Time: </strong>
                <span id="summary-datetime">{{ booking.date }}</span>
              </p>
              <p class="summary-location">
                <strong>Location: </strong> <span>155 Metcalfe Street, Ottawa, ON K2P 1P4</span>
              </p>
            </div>
            <button class="eButton" @click="goToHome()">Back to Homepage</button>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.state5 {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  h2 {
    margin-bottom: 0rem;
  }

  p {
    margin-bottom: 0rem;
  }
}
.tInGroup {
  margin-top: 1rem;
}
.bottomButtons {
  margin-top: 1.5rem;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
.state1 {
  display: flex;
  flex-direction: column;
}
.card {
  background-color: #fff;
  border-radius: 1.5rem;
  padding: 2rem 5rem 5rem 5rem;
  display: flex;
  flex-direction: column;
}

.ptitle {
  color: #f59e0b;
  font-weight: 600;
  margin-bottom: 10px;
}
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

.book-section {
  background-color: #f1f5f9;
  padding-top: 5rem;
  padding-bottom: 5rem;
}

.progress-bar-track {
  width: 100%;
  background-color: #e5e7eb;
  height: 0.625rem;
  border-radius: 9999px;
  overflow: hidden;
  margin-top: 0px;
}

.progress-bar-fill {
  margin-top: 0px;
  background-color: #f59e0b;
  height: 100%;
  border-radius: 9999px;
  transition: width 0.3s ease-in-out;
}

.ceSpacing {
  margin-left: auto;
  margin-right: auto;
  max-width: min(60vw, 1000px);
  width: 100%;
}

.bDropdown {
  margin-top: 0.25rem;
  display: block;
  width: 100%;
  padding-top: 0.75rem;
  padding-bottom: 0.75rem;
  padding-left: 1rem;
  padding-right: 1rem;
  border-width: 1px;
  border-style: solid;
  border-color: #cbd5e1;
  background-color: #ffffff;
  border-radius: 0.5rem;
  box-shadow: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
}

.bDropdown:focus {
  outline: none;
  border-color: #f59e0b;
  box-shadow:
    0 0 0 3px #f59e0b,
    0 1px 2px 0 rgba(0, 0, 0, 0.05);
}

@media (min-width: 640px) {
  .bDropdown {
    font-size: 0.875rem;
    line-height: 1.25rem;
  }
}

.nButton {
  font-weight: 600;
  align-self: end;
  width: 15rem;
  height: 3rem;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 1.1rem;
  border-radius: 8px;
  border: none;
  margin-top: 1rem;
  transition:
    background-color 0.15s ease-in-out,
    transform 0.1s ease-in-out;
  cursor: pointer;
  background-color: rgb(245, 158, 11);
}

.nButton:hover {
  background-color: #e08900;
}

.nButton:active {
  background-color: #c97700;
  transform: translateY(1px);
}

.eButton {
  font-weight: 600;
  width: 15rem;
  height: 3rem;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 1.1rem;
  border-radius: 8px;
  border: none;
  margin-top: 1rem;
  transition:
    background-color 0.15s ease-in-out,
    transform 0.1s ease-in-out;
  cursor: pointer;
  background-color: rgb(245, 158, 11);
}

.eButton:hover {
  background-color: #e08900;
}

.eButton:active {
  background-color: #c97700;
  transform: translateY(1px);
}

.bButton {
  font-weight: 600;
  align-self: end;
  width: 7rem;
  height: 3rem;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 1.1rem;
  border-radius: 8px;
  border: none;
  margin-top: 1rem;
  transition:
    background-color 0.15s ease-in-out,
    transform 0.1s ease-in-out;
  cursor: pointer;
  background-color: rgb(226, 232, 240);
}

.bButton:hover {
  background-color: #cbd5e1;
}

.bButton:active {
  background-color: #9ea4ad;
  transform: translateY(1px);
}

.success-icon {
  margin-top: 2rem;
  width: 4rem;
  height: 4rem;
  color: #22c55e;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 0rem;
}

.gButton {
  font-weight: 600;
  align-self: end;
  width: 12rem;
  height: 3rem;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 1.1rem;
  border-radius: 8px;
  border: none;
  margin-top: 1rem;
  transition:
    background-color 0.15s ease-in-out,
    transform 0.1s ease-in-out;
  cursor: pointer;
  color: white;
  background-color: rgb(34, 197, 94);
}

.gButton:hover {
  background-color: #16a34a;
}

.gButton:active {
  background-color: #0f6f32;
  transform: translateY(1px);
}

.tLabel {
  display: block;
  font-size: 0.875rem;
  line-height: 1.25rem;
  font-weight: 500;
  color: rgb(51, 65, 85);
  margin-bottom: 0.25rem;
}

.tInput {
  display: block;
  width: 100%;
  margin-top: 0.25rem;
  padding-top: 0.75rem;
  padding-bottom: 0.75rem;
  padding-left: 1rem;
  padding-right: 1rem;
  border-width: 1px;
  border-style: solid;
  border-color: rgb(203, 213, 225);
  border-radius: 0.5rem;
  box-shadow: 0 1px 2px 0 rgb(0 0 0 / 0.05);
  font-size: 1rem;
  line-height: 1.5rem;
  box-sizing: border-box;
}

.tInput:focus {
  outline: 2px solid transparent;
  outline-offset: 2px;
  border-color: rgb(245, 158, 11);
  box-shadow:
    0 0 0 2px rgb(245, 158, 11),
    0 1px 2px 0 rgb(0 0 0 / 0.05);
}

@media (min-width: 640px) {
  .tInput {
    font-size: 0.875rem;
    line-height: 1.25rem;
  }
}

.summary-box {
  margin-top: 2rem;
  padding: 1.5rem;
  background-color: rgb(248, 250, 252);
  border-radius: 0.5rem;
  border-width: 1px;
  border-style: solid;
  border-color: rgb(226, 232, 240);
}

.summary-title {
  font-size: 1.125rem;
  line-height: 1.75rem;
  font-weight: 600;
  color: rgb(30, 41, 59);
  margin-bottom: 0.75rem;
}

.summary-item {
  font-size: 0.875rem;
  line-height: 1.25rem;
  color: rgb(71, 85, 105);
}
.summary-location {
  font-size: 0.875rem;
  line-height: 1.25rem;
  color: rgb(71, 85, 105);
}

.summary-total {
  font-size: 1.125rem;
  line-height: 1.75rem;
  font-weight: 700;
  color: rgb(30, 41, 59);
  margin-top: 0.5rem;
}

.policy-agreement-container {
  margin-top: 1.5rem;
}

.policy-label {
  display: flex;
  align-items: center;
  cursor: pointer;
}

.policy-checkbox {
  height: 1rem;
  width: 1rem;
  accent-color: rgb(217, 119, 6);
  border-width: 1px;
  border-style: solid;
  border-color: rgb(203, 213, 225);
  border-radius: 0.25rem;
  vertical-align: middle;
}

.policy-checkbox:focus {
  outline: 2px solid transparent;
  outline-offset: 2px;
  box-shadow: 0 0 0 2px rgb(245, 158, 11);
}

.policy-text {
  margin-left: 0.5rem;
  font-size: 0.875rem;
  line-height: 1.25rem;
  color: rgb(71, 85, 105);
}
</style>
