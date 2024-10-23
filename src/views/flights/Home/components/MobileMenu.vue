<template>
    <div class="mobile-menu-container d-flex flex-column align-items-center py-4">
      <!-- Service and Contact Buttons -->
      <div class="w-100 d-flex justify-content-around mb-4">
        <button class="btn btn-primary w-45">Service</button>
        <button class="btn btn-secondary w-45">Contact</button>
      </div>
  
      <!-- Trustpilot Widget -->
      <div class="trustpilot-widget text-center mb-4">
        <img :src="trustpilotImage" alt="Trustpilot Widget" class="img-fluid" />
      </div>
  
      <!-- Phone Number and Operational Hours -->
      <!-- <div class="text-center">
        <div class="d-flex align-items-center justify-content-center mb-2">
          <font-awesome-icon :icon="faPhone" class="me-2" />
          <div>
            <span class="fw-bold fs-5">020 3890 3669</span>
            <br />
            <small>Daily Open From 08:00 - 23:59</small>
          </div>
        </div>
      </div> -->
    </div>
  </template>
  
  <script setup lang="ts">
  import { faPhone } from '@fortawesome/free-solid-svg-icons' // Import Font Awesome phone icon
  import trustpilotImage from '@/assets/images/Image_6.png'
  </script>
  
  <style scoped>
  /* Remove unnecessary custom CSS by using Bootstrap's w-100, w-45 classes */
  .w-45 {
    width: 45%;
  }
  </style>
  