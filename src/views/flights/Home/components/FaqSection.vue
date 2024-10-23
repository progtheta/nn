<template>
  <section class="container py-5">
    <div class="row mx-5">
      <!-- Left Section -->
      <div class="col-md-6 d-flex flex-column justify-content-center">
        <h2 class="text-info font-weight-bold mb-4">Unlock Your Travel Dreams</h2>
        <p class="text-muted mb-4">Transform your travel aspirations into reality with our expert services.</p>
        <ul class="list-unstyled text-dark">
          <li>✔ Personalized Travel Planning Tailored to You</li>
          <li>✔ Access to Exclusive Deals and Discounts</li>
          <li>✔ Seamless Travel Arrangements with No Hassle</li>
          <li>✔ 24/7 Support for Peace of Mind</li>
          <li>✔ Local Insights to Enhance Your Journey</li>
        </ul>
      </div>

      <!-- Right Section -->
      <div class="col-md-6">
        <div class="bg-light p-4 rounded shadow mb-4 d-flex align-items-center">
          <i class="fas fa-phone-alt text-success display-4 mr-3"></i>
          <div>
            <h3 class="h5 font-weight-bold">Call Us 📞</h3>
            <p>For Bookings & Latest Offers</p>
            <p class="text-primary font-weight-bold cursor-pointer">Call Our Experts Now</p>
          </div>
        </div>

        <div class="bg-light p-4 rounded shadow mb-4 d-flex align-items-center">
          <i class="fas fa-envelope text-success display-4 mr-3"></i>
          <div>
            <h3 class="h5 font-weight-bold">Deals in Your Inbox ✉️</h3>
            <p>Subscribe to our newsletter for our latest offers</p>
          </div>
        </div>

        <div class="bg-light p-4 rounded shadow d-flex align-items-center">
          <i class="fas fa-inbox text-success display-4 mr-3"></i>
          <div>
            <h3 class="h5 font-weight-bold">Email Enquiry? 🧾</h3>
            <p>Get your tailor-made holiday quote, we’re here to make it easy...</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'TravelDreamsSection',
};
</script>

<style scoped>
.bg-light {
  background-color: #f7f9fc; /* Light background color */
}

.text-info {
  color: #17a2b8; /* Info text color */
}
</style>
