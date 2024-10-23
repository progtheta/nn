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
  
          <!-- Right-side menu (Sign-up, theme change) -->
          <ul class="nav flex-row align-items-center list-unstyled ms-xl-auto d-none d-xl-flex">
            <!-- Dropdown for theme switch -->
            <CustomDropDown is="li" custom-class="nav-item me-3">
              <button
                class="btn btn-link text-warning p-0 mb-0"
                id="bd-theme"
                aria-expanded="false"
                data-bs-toggle="dropdown"
                data-bs-display="static"
                type="button"
              >
                <BIconCircleHalf class="fs-5" />
              </button>
  
              <ul class="dropdown-menu min-w-auto dropdown-menu-end" aria-labelledby="bd-theme">
                <template v-for="(mode, idx) in themeModes" :key="idx">
                  <li :class="{ 'mb-1': idx != themeModes.length - 1 }">
                    <button
                      type="button"
                      class="dropdown-item d-flex align-items-center"
                      :class="{ active: mode.theme === useLayout.theme }"
                      @click="useLayout.setTheme(mode.theme)"
                    >
                      <component :is="mode.icon" />
                      &nbsp;&nbsp;{{ toSentenceCase(mode.theme) }}
                    </button>
                  </li>
                </template>
              </ul>
            </CustomDropDown>
  
            <!-- Trustpilot widget demo -->
            <div class="d-flex align-items-center ms-4">
              <img :src="trustpilotImage" alt="Trustpilot Widget" width="250" height="20" />
            </div>
  
            <!-- Phone number and operational hours -->
            <div class="d-flex align-items-center ms-4 phone-color">
              <font-awesome-icon :icon="faPhone" class="me-2 fs-4" />
              <div>
                <span class="fs-4 fw-bold">020 3890 3669</span>
                <br />
                <small>Daily Open From 08:00 - 23:59</small>
              </div>
            </div>
          </ul>
  
          <!-- Mobile right-side content (phone number, theme change, etc.) -->
          <ul class="nav flex-row align-items-center list-unstyled d-flex d-xl-none">
            <CustomDropDown is="li" custom-class="nav-item me-3">
              <button
                class="btn btn-link text-warning p-0 mb-0"
                id="bd-theme-mobile"
                aria-expanded="false"
                data-bs-toggle="dropdown"
                data-bs-display="static"
                type="button"
              >
                <BIconCircleHalf class="fs-5" />
              </button>
  
              <ul class="dropdown-menu min-w-auto dropdown-menu-end" aria-labelledby="bd-theme-mobile">
                <template v-for="(mode, idx) in themeModes" :key="idx">
                  <li :class="{ 'mb-1': idx != themeModes.length - 1 }">
                    <button
                      type="button"
                      class="dropdown-item d-flex align-items-center"
                      :class="{ active: mode.theme === useLayout.theme }"
                      @click="useLayout.setTheme(mode.theme)"
                    >
                      <component :is="mode.icon" />
                      &nbsp;&nbsp;{{ toSentenceCase(mode.theme) }}
                    </button>
                  </li>
                </template>
              </ul>
            </CustomDropDown>
  
            <!-- Mobile phone number -->
            <div class="d-flex align-items-center ms-3 phone-color">
              <font-awesome-icon :icon="faPhone" class="me-2 fs-4" />
              <span class="fs-4 fw-bold">020 3890 3669</span>
            </div>
          </ul>
        </b-container>
      </nav>
    </header>
  </template>
  
  <script setup lang="ts">
  import { onMounted, ref } from 'vue'
  
  import AppMenu from '@/components/navbar/AppMenu.vue'
  import CustomDropDown from '@/components/CustomDropDown.vue'
  import LogoBox from '@/components/LogoBox.vue'
  import MobileMenu from '@/views/flights/Home/components/MobileMenu.vue'
  import { BIconCircleHalf, BIconSun, BIconMoonStars } from 'bootstrap-icons-vue'
  import { faPhone } from '@fortawesome/free-solid-svg-icons'
  
  import { toSentenceCase } from '@/helpers/change-casting'
  import { useLayoutStore } from '@/stores/layout'
  import trustpilotImage from '@/assets/images/Image_6.png'
  
  type ThemeModeType = {
    theme: "light" | "dark" | "auto";
    icon: any;
  }
  
  const themeModes: ThemeModeType[] = [
    {
      icon: BIconSun,
      theme: 'light'
    },
    {
      icon: BIconMoonStars,
      theme: 'dark'
    },
    {
      icon: BIconCircleHalf,
      theme: 'auto'
    }
  ];
  
  const useLayout = useLayoutStore()
  
  let isSticky = ref<boolean>(false)
  let isMobileMenuOpen = ref<boolean>(false) // Mobile menu toggle state
  
  // Toggle the mobile menu open/close state
  const toggleMobileMenu = () => {
    isMobileMenuOpen.value = !isMobileMenuOpen.value
  }
  
  onMounted(() => {
    window.addEventListener('scroll', () => {
      isSticky.value = window.scrollY >= 400
    })
  })
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
  