<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import logoImage from '../assets/logo.png'
import zaloLogo from '../assets/Zalo-Logo.png'

const isScrolled = ref(false)
const isMobileMenuOpen = ref(false)

const navItems = [
  { name: 'Giới Thiệu', href: '#about' },
  { name: 'Sản Phẩm', href: '#products' },
  { name: 'Dịch Vụ', href: '#services' },
  { name: 'Liên Hệ', href: '#contact' },
]

const socialLinks = [
  {
    name: 'Facebook',
    url: 'https://www.facebook.com/share/1NtF39Gdm4/?mibextid=wwXIfr',
    icon: `<svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/></svg>`,
  },
  {
    name: 'Messenger',
    url: 'https://m.me/ton.thep.tong.thuy',
    icon: `<svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M12 0C5.373 0 0 4.975 0 11.111c0 3.497 1.745 6.616 4.472 8.652V24l4.086-2.242c1.09.301 2.246.464 3.442.464 6.627 0 12-4.974 12-11.111C24 4.975 18.627 0 12 0zm1.191 14.963l-3.055-3.26-5.963 3.26L10.732 8.1l3.13 3.26L19.764 8.1l-6.573 6.863z"/></svg>`,
  },
  {
    name: 'Zalo',
    url: '#contact',
    logoImage: zaloLogo,
    isInternal: true,
  },
]

const handleScroll = () => {
  isScrolled.value = window.scrollY > 60
}

const closeMobileMenu = () => {
  isMobileMenuOpen.value = false
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll, { passive: true })
})
onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
  <header
    :class="[
      'fixed top-0 left-0 right-0 z-50 transition-all duration-300',
      isScrolled
        ? 'bg-white/95 backdrop-blur-md shadow-sm border-b border-gray-100'
        : 'bg-transparent',
    ]"
  >
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between h-20 md:h-24">

        <!-- Logo -->
        <a href="#home" class="flex-shrink-0">
          <img
            :src="logoImage"
            alt="Tòng Thuỷ Logo"
            :class="[
              'object-contain transition-all duration-300',
              isScrolled ? 'h-14 w-14' : 'h-16 w-16 md:h-20 md:w-20',
            ]"
          />
        </a>

        <!-- Desktop Nav -->
        <nav class="hidden md:flex items-center gap-8">
          <a
            v-for="item in navItems"
            :key="item.name"
            :href="item.href"
            :class="[
              'nav-link text-sm font-semibold tracking-wide transition-colors duration-200',
              isScrolled ? 'text-slate-700 hover:text-blue-600' : 'text-white/90 hover:text-white',
            ]"
          >
            {{ item.name }}
          </a>
        </nav>

        <!-- Social + CTA (Desktop) -->
        <div class="hidden md:flex items-center gap-4">
          <!-- Social icons -->
          <div class="flex items-center gap-2">
            <a
              v-for="social in socialLinks"
              :key="social.name"
              :href="social.url"
              :target="social.isInternal ? '_self' : '_blank'"
              :rel="social.isInternal ? '' : 'noopener noreferrer'"
              :title="social.name"
              :class="[
                'p-2 rounded-lg transition-colors duration-200',
                isScrolled
                  ? 'text-slate-600 hover:text-blue-600 hover:bg-blue-50'
                  : 'text-white/80 hover:text-white hover:bg-white/15',
              ]"
            >
              <img
                v-if="social.logoImage"
                :src="social.logoImage"
                :alt="social.name"
                class="w-5 h-5 object-contain grayscale"
              />
              <span v-else v-html="social.icon" />
            </a>
          </div>

          <!-- CTA button -->
          <a
            href="tel:0947196779"
            :class="[
              'flex items-center gap-2 px-5 py-2.5 rounded-lg text-sm font-semibold transition-all duration-200',
              isScrolled
                ? 'bg-blue-600 text-white hover:bg-blue-700 shadow-sm'
                : 'bg-white text-blue-700 hover:bg-blue-50 shadow-lg',
            ]"
          >
            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" />
            </svg>
            Gọi Ngay
          </a>
        </div>

        <!-- Mobile Hamburger -->
        <button
          class="md:hidden p-2 rounded-lg transition-colors"
          :class="isScrolled ? 'text-slate-700' : 'text-white'"
          @click="isMobileMenuOpen = !isMobileMenuOpen"
          aria-label="Toggle menu"
        >
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path
              v-if="!isMobileMenuOpen"
              stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
              d="M4 6h16M4 12h16M4 18h16"
            />
            <path
              v-else
              stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
              d="M6 18L18 6M6 6l12 12"
            />
          </svg>
        </button>
      </div>
    </div>

    <!-- Mobile Menu -->
    <Transition
      enter-active-class="transition duration-200 ease-out"
      enter-from-class="opacity-0 -translate-y-2"
      enter-to-class="opacity-100 translate-y-0"
      leave-active-class="transition duration-150 ease-in"
      leave-from-class="opacity-100 translate-y-0"
      leave-to-class="opacity-0 -translate-y-2"
    >
      <div
        v-show="isMobileMenuOpen"
        class="md:hidden bg-white border-t border-gray-100 shadow-lg"
      >
        <div class="max-w-7xl mx-auto px-4 py-6 space-y-1">
          <a
            v-for="item in navItems"
            :key="item.name"
            :href="item.href"
            class="block px-4 py-3 text-slate-700 font-semibold rounded-lg hover:bg-blue-50 hover:text-blue-600 transition-colors"
            @click="closeMobileMenu"
          >
            {{ item.name }}
          </a>

          <div class="pt-4 border-t border-gray-100 flex items-center gap-4 px-4">
            <a
              v-for="social in socialLinks"
              :key="social.name"
              :href="social.url"
              :target="social.isInternal ? '_self' : '_blank'"
              class="p-2 text-slate-600 hover:text-blue-600 rounded-lg hover:bg-blue-50 transition-colors"
              @click="closeMobileMenu"
            >
              <img v-if="social.logoImage" :src="social.logoImage" :alt="social.name" class="w-5 h-5 grayscale" />
              <span v-else v-html="social.icon" />
            </a>

            <a
              href="tel:0947196779"
              class="ml-auto btn-primary text-sm py-2 px-5"
              @click="closeMobileMenu"
            >
              Gọi Ngay
            </a>
          </div>
        </div>
      </div>
    </Transition>
  </header>
</template>
