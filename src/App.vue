<script setup>
import Navbar from './components/Navbar.vue';
import logoImage from './assets/logo.png'
import HeroSection from './components/HeroSection.vue';
import ClientSection from './components/ClientSection.vue';
import FeaturesSection from './components/FeaturesSection.vue';
import SolutionsSection from './components/SolutionsSection.vue';
import StatsSection from './components/StatsSection.vue';
import TestimonialsSection from './components/TestimonialsSection.vue';
import CTASection from './components/CTASection.vue';
import ContactSection from './components/ContactSection.vue';
import Footer from './components/Footer.vue';
</script>

<template>
  <!-- ABSOLUTELY MASSIVE LOGO OPTIONS! -->
  <Navbar 
    :brand-logo="logoImage" 
    logo-size="titan"
  />
  <HeroSection />
  <ClientSection />
  <FeaturesSection />
  <SolutionsSection />
  <StatsSection />
  <TestimonialsSection />
  <CTASection />
  <ContactSection />
  <Footer />
  
  <!-- Size comparison: -->
  <!-- logo-size="massive"   - 112-144px -->
  <!-- logo-size="gigantic" - 128-176px -->
  <!-- logo-size="colossal" - 144-192px -->
  <!-- logo-size="titan"    - 160-224px (INSANELY BIG!) -->
</template>


