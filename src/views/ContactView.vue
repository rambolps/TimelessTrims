<script setup></script>

<template>
  <div class="sections">
    <section class="title-section">
      <div class="title cSpacing">
        <h1>Get In Touch</h1>
        <p>We'd love to hear from you. Reach out with any questions or to book an appointment.</p>
      </div>
    </section>

    <section class="main-contact-section">
      <div class="main cSpacing contact-container">
        <div class="contact-top-row">
          <div class="contact-block">
            <h2 class="contact-heading">Contact Timeless Trims</h2>
            <div class="contact-details">
              <p>
                <strong class="contact-label">Address:</strong><br />
                155 Metcalfe Street, Ottawa, ON K2P 1P4
              </p>
              <p>
                <strong class="contact-label">Phone:</strong><br />
                <a href="tel:+16135550189" class="contact-link">(613) 555-0189</a>
              </p>
              <p>
                <strong class="contact-label">Email:</strong><br />
                <a href="mailto:bookings@timelesstrims.ca" class="contact-link"
                  >bookings@timelesstrims.ca</a
                >
              </p>
            </div>
          </div>

          <div class="contact-block">
            <h2 class="contact-heading">Operating Hours</h2>
            <div class="contact-text">
              <p>Monday - Friday: 9:00 AM - 7:00 PM</p>
              <p>Saturday: 10:00 AM - 5:00 PM</p>
              <p>Sunday: Closed</p>
            </div>
          </div>
        </div>

        <div class="contact-map-row">
          <div class="contact-block">
            <h2 class="contact-heading">Find Us</h2>
            <div class="map-embed-container dShadow">
              <iframe
                src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d2800.0000000000005!2d-75.69400000000001!3d45.42100000000001!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x4cce050f00000001%3A0x1234567890abcdef!2s155%20Metcalfe%20St%2C%20Ottawa%2C%20ON%20K2P%201P4!5e0!3m2!1sen!2sca!4v1678886400000!5m2!1sen!2sca"
                style="border: 0"
                allowfullscreen="true"
                loading="lazy"
                referrerpolicy="no-referrer-when-downgrade"
                title="Google Maps location for Timeless Trims"
              >
              </iframe>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.sections {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}
.title-section {
  background-color: #334155;
  text-align: center;
  color: #fff;
  padding: 4rem 0rem;
}
.title-section h1 {
  margin: 0;
  font-size: 4.25rem;
}
.title-section p {
  font-size: 1.85rem;
}

.main-contact-section {
  padding-top: 4rem;
  padding-bottom: 4rem;
  background-color: #f8fafc;
  flex-grow: 1;
}

.contact-container {
  width: 100%;
  margin-left: auto;
  margin-right: auto;
  padding-left: 1rem;
  padding-right: 1rem;
  max-width: 1140px;
  display: flex;
  flex-direction: column;
  gap: 0rem;
}

.contact-top-row {
  display: flex;
  flex-wrap: wrap;
  gap: 2rem;
  width: 100%;
}

.contact-top-row > .contact-block {
  flex: 1 1 calc(50% - 1rem);
  min-width: 280px;
}

.contact-map-row {
  width: 100%;
}

.contact-heading {
  font-size: 2.15rem;
  line-height: 2.5rem;
  font-weight: 600;
  color: rgb(30, 41, 59);
  margin-bottom: 1.5rem;
}

.contact-details,
.contact-text {
  font-size: 1.4rem;
  line-height: 2rem;
  color: rgb(71, 85, 105);
}

.contact-label {
  color: rgb(51, 65, 85);
  font-weight: 600;
}

.contact-link {
  color: rgb(217, 119, 6);
  text-decoration: none;
}
.contact-link:hover {
  color: rgb(180, 83, 9);
  text-decoration: underline;
}

.map-embed-container {
  position: relative;
  width: 100%;
  padding-bottom: 75%;
  height: 0;
  border-radius: 0.5rem;
  overflow: hidden;
}
.map-embed-container iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  border: 0;
}
</style>
