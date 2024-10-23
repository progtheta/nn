<template>
    <header class="navbar-light header-sticky" :class="{ 'header-sticky-on': isSticky }">
      <nav class="navbar navbar-expand-xl">
        <b-container>
          <LogoBox />
  
          <!-- Mobile-specific button and menus -->
          <div class="d-flex d-xl-none">
            <!-- Button to toggle Mobile Menu -->
            <button
              class="navbar-toggler"
              type="button"
              @click="toggleMobileMenu"
              aria-controls="mobileMenu"
              :aria-expanded="isMobileMenuOpen ? 'true' : 'false'"
              aria-label="Toggle navigation"
            >
              <!-- Conditionally rendered icon -->
              <span v-if="!isMobileMenuOpen" class="navbar-toggler-icon"></span>
              <span v-else class="close-icon">&times;</span> <!-- Close icon -->
            </button>
          </div>
  
          <!-- Mobile menu -->
          <div :class="['collapse', { show: isMobileMenuOpen }]" id="mobileMenu">
            <MobileMenu />
          </div>
  
          <!-- Desktop menu only -->
          <div class="d-none d-xl-flex">
            <AppMenu start-booking-menu />
          </div>
  
          <!-- Right-side menu (Sign-up, Trustpilot widget, phone number) -->
          <ul class="nav flex-row align-items-center list-unstyled ms-xl-auto d-none d-xl-flex">
            <!-- Trustpilot widget demo -->
            <div class="d-flex align-items-center ms-4">
              <img :src="trustpilotImage" alt="Trustpilot Widget" width="250" height="20" />
            </div>
  
            <!-- Phone number and operational hours -->
            <div class="d-flex align-items-center ms-4 phone-color d-none d-xl-flex">
              <font-awesome-icon :icon="faPhone" class="me-2 fs-4" />
              <div>
                <a href="tel:02038903669" class="fw-bold fs-4">020 3890 3669</a>
                <br />
                <small>Daily Open From 08:00 - 23:59</small>
              </div>
            </div>
          </ul>
  
        </b-container>
      </nav>
    </header>
  </template>
  
  <script setup lang="ts">
  import { onMounted, ref } from 'vue';
  
  import AppMenu from '@/components/navbar/AppMenu.vue';
  import LogoBox from '@/components/LogoBox.vue';
  import MobileMenu from '@/views/flights/Home/components/MobileMenu.vue';
  import { faPhone } from '@fortawesome/free-solid-svg-icons';
  
  import { useLayoutStore } from '@/stores/layout';
  import trustpilotImage from '@/assets/images/Image_6.png';
  
  const useLayout = useLayoutStore();
  
  let isSticky = ref<boolean>(false);
  let isMobileMenuOpen = ref<boolean>(false); // Mobile menu toggle state
  
  const toggleMobileMenu = () => {
    isMobileMenuOpen.value = !isMobileMenuOpen.value;
  };
  
  onMounted(() => {
    window.addEventListener('scroll', () => {
      isSticky.value = window.scrollY >= 400;
    });
  });
  </script>
  
  <style scoped>
  .header-sticky-on {
    position: fixed;
    top: 0;
    width: 100%;
    z-index: 1000;
  }
  .phone-color {
    color: #1e90ff;
  }
  .close-icon {
    font-size: 24px;
    font-weight: bold;
  }
  </style>
  