<script setup>
import Navbar              from './components/Navbar.vue'
import HeroSection         from './components/HeroSection.vue'
import ShowreelSection     from './components/ShowreelSection.vue'
import ClientSection       from './components/ClientSection.vue'
import ServicesSection     from './components/ServicesSection.vue'
import ProductsSection     from './components/ProductsSection.vue'
import TestimonialsSection from './components/TestimonialsSection.vue'
import QRSection           from './components/QRSection.vue'
import ContactSection      from './components/ContactSection.vue'
import Footer              from './components/Footer.vue'
</script>

<template>
  <Navbar />
  <HeroSection />
  <ShowreelSection />
  <ClientSection />
  <ServicesSection />
  <ProductsSection />
  <TestimonialsSection />
  <QRSection />
  <ContactSection />
  <Footer />

  <!-- Mobile floating call button -->
  <a
    href="tel:0947196779"
    class="md:hidden fixed bottom-5 right-5 z-40 flex items-center gap-2 px-4 py-3 bg-blue-600 hover:bg-blue-700 text-white text-sm font-bold rounded-2xl shadow-lg shadow-blue-600/40 transition-all active:scale-95"
    aria-label="Gọi ngay"
  >
    <svg class="w-4 h-4 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5"
        d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" />
    </svg>
    Gọi Ngay
  </a>
</template>
