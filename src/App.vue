<script setup>
import Navbar from './components/Navbar.vue';
import logoImage from './assets/logo.png'
</script>

<template>
  <!-- ABSOLUTELY MASSIVE LOGO OPTIONS! -->
  <Navbar 
    :brand-logo="logoImage" 
    logo-size="titan"
  />
  
  <!-- Size comparison: -->
  <!-- logo-size="massive"   - 112-144px -->
  <!-- logo-size="gigantic" - 128-176px -->
  <!-- logo-size="colossal" - 144-192px -->
  <!-- logo-size="titan"    - 160-224px (INSANELY BIG!) -->
</template>


