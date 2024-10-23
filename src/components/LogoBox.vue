<template>
  <router-link :to="{ name: 'flights.home' }" class="navbar-brand">
    <template v-if="!onlyLight">
      <img class="light-mode-item navbar-brand-item" :class="customClass" :src="newLogo" alt="logo" />
      <img
        class="dark-mode-item navbar-brand-item"
        :class="customClass"
        :src="newLogo"
        alt="logo"
      />
    </template>

    <img v-if="onlyLight" class="navbar-brand-item" :src="logoLight" alt="logo" />
  </router-link>
</template>

<script setup lang="ts">
import logo from '@/assets/images/logo.svg'
import newLogo from '@/assets/images/travelnfare.png'
import logoLight from '@/assets/images/logo-light.svg'

defineProps({
  customClass: String,
  onlyLight: {
    type: Boolean,
    default: false
  }
})
</script>
