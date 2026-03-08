<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import logoImage from '../assets/logo.png'
import zaloLogo  from '../assets/Zalo-Logo.png'

const isScrolled       = ref(false)
const isMobileMenuOpen = ref(false)

const navItems = [
  { name: 'Giới Thiệu', href: '#about'    },
  { name: 'Sản Phẩm',   href: '#products' },
  { name: 'Dịch Vụ',    href: '#services' },
  { name: 'Liên Hệ',    href: '#contact'  },
]

const socialLinks = [
  {
    name: 'Facebook', url: 'https://www.facebook.com/share/1NtF39Gdm4/?mibextid=wwXIfr',
    icon: `<svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/></svg>`,
  },
  {
    name: 'Messenger', url: 'https://m.me/ton.thep.tong.thuy',
    icon: `<svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M12 0C5.373 0 0 4.975 0 11.111c0 3.497 1.745 6.616 4.472 8.652V24l4.086-2.242c1.09.301 2.246.464 3.442.464 6.627 0 12-4.974 12-11.111C24 4.975 18.627 0 12 0zm1.191 14.963l-3.055-3.26-5.963 3.26L10.732 8.1l3.13 3.26L19.764 8.1l-6.573 6.863z"/></svg>`,
  },
  { name: 'Zalo', url: '#qr-section', logoImage: zaloLogo, isInternal: true },
]

const handleScroll = () => { isScrolled.value = window.scrollY > 60 }
const closeMenu    = () => { isMobileMenuOpen.value = false; document.body.style.overflow = '' }
const openMenu     = () => { isMobileMenuOpen.value = true;  document.body.style.overflow = 'hidden' }

onMounted(()   => window.addEventListener('scroll', handleScroll, { passive: true }))
onUnmounted(() => { window.removeEventListener('scroll', handleScroll); document.body.style.overflow = '' })
</script>

<template>
  <header
    :class="[
      'fixed top-0 left-0 right-0 z-50 transition-all duration-400',
      isScrolled
        ? 'bg-[#070D1F]/95 backdrop-blur-xl shadow-[0_1px_0_rgba(255,255,255,0.06)]'
        : 'bg-transparent',
    ]"
  >
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between h-[68px] md:h-[76px]">

        <!-- Logo + Wordmark -->
        <a href="#home" class="flex items-center gap-3 flex-shrink-0">
          <img
            :src="logoImage" alt="Tòng Thuỷ"
            :class="['object-contain transition-all duration-300', isScrolled ? 'h-11 w-11' : 'h-12 w-12 md:h-[52px] md:w-[52px]']"
          />
          <div class="hidden sm:block leading-none">
            <p class="font-extrabold text-[15px] tracking-wide text-white">
              TÒNG THUỶ
            </p>
            <p class="text-[9px] font-semibold tracking-[0.22em] uppercase mt-0.5 text-white/40">
              Vật Liệu Xây Dựng
            </p>
          </div>
        </a>

        <!-- Desktop Nav -->
        <nav class="hidden md:flex items-center gap-8">
          <a
            v-for="item in navItems" :key="item.name" :href="item.href"
            class="nav-link text-[13px] font-semibold tracking-wide transition-colors duration-200 text-white/75 hover:text-white"
          >{{ item.name }}</a>
        </nav>

        <!-- Desktop Actions -->
        <div class="hidden md:flex items-center gap-2">
          <a
            v-for="s in socialLinks" :key="s.name" :href="s.url"
            :target="s.isInternal ? '_self' : '_blank'"
            :rel="s.isInternal ? '' : 'noopener noreferrer'"
            class="w-9 h-9 flex items-center justify-center rounded-lg transition-all duration-200 text-white/60 hover:text-white hover:bg-white/10"
          >
            <img v-if="s.logoImage" :src="s.logoImage" :alt="s.name" class="w-4 h-4 object-contain brightness-0 invert opacity-60" />
            <span v-else v-html="s.icon" />
          </a>
          <div class="mx-2 w-px h-4 bg-white/15" />
          <a
            href="tel:0947196779"
            :class="[
              'flex items-center gap-1.5 px-5 py-2.5 rounded-xl text-[13px] font-bold transition-all duration-200',
              'bg-blue-600 text-white hover:bg-blue-500 shadow-lg shadow-blue-600/30',
            ]"
          >
            <svg class="w-3.5 h-3.5 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" />
            </svg>
            Gọi Ngay
          </a>
        </div>

        <!-- Mobile hamburger -->
        <button
          @click="openMenu"
          class="md:hidden w-10 h-10 flex items-center justify-center rounded-xl transition-colors text-white hover:bg-white/10"
        >
          <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M4 6h16M4 12h10M4 18h16" />
          </svg>
        </button>
      </div>
    </div>
  </header>

  <!-- Mobile Full-Screen Overlay -->
  <Teleport to="body">
    <Transition
      enter-active-class="transition duration-250 ease-out"
      enter-from-class="opacity-0"
      enter-to-class="opacity-100"
      leave-active-class="transition duration-200 ease-in"
      leave-from-class="opacity-100"
      leave-to-class="opacity-0"
    >
      <div v-if="isMobileMenuOpen" class="md:hidden fixed inset-0 z-[60] bg-[#060D1E]/98 backdrop-blur-2xl flex flex-col">

        <!-- Top bar -->
        <div class="flex items-center justify-between px-5 h-[68px] border-b border-white/[0.06] flex-shrink-0">
          <div class="flex items-center gap-3">
            <img :src="logoImage" alt="Tòng Thuỷ" class="h-10 w-10 object-contain" />
            <div class="leading-none">
              <p class="font-extrabold text-sm text-white tracking-wide">TÒNG THUỶ</p>
              <p class="text-[9px] text-white/30 tracking-[0.22em] uppercase mt-0.5">Vật Liệu Xây Dựng</p>
            </div>
          </div>
          <button @click="closeMenu" class="w-10 h-10 flex items-center justify-center rounded-xl text-white/40 hover:text-white hover:bg-white/10 transition-all">
            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
        </div>

        <!-- Nav links -->
        <nav class="flex-1 flex flex-col justify-center px-6">
          <a
            v-for="(item, i) in navItems" :key="item.name" :href="item.href"
            class="group flex items-center justify-between py-5 border-b border-white/[0.05] animate-fade-up"
            :style="`animation-delay: ${i * 0.05}s`"
            @click="closeMenu"
          >
            <span class="text-[1.6rem] font-bold text-white/65 group-hover:text-white transition-colors duration-200">{{ item.name }}</span>
            <svg class="w-5 h-5 text-white/15 group-hover:text-blue-400 group-hover:translate-x-1 transition-all duration-200" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
            </svg>
          </a>
        </nav>

        <!-- Bottom CTA -->
        <div class="px-6 pb-10 pt-6 space-y-3 border-t border-white/[0.06] flex-shrink-0">
          <a href="tel:0947196779" @click="closeMenu"
            class="flex items-center justify-center gap-2 w-full py-4 bg-blue-600 hover:bg-blue-700 text-white font-bold rounded-2xl transition-colors text-base">
            <svg class="w-4 h-4 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" />
            </svg>
            Gọi Ngay — 0947 196 779
          </a>
          <div class="flex gap-2">
            <a v-for="s in socialLinks" :key="s.name" :href="s.url"
              :target="s.isInternal ? '_self' : '_blank'"
              class="flex-1 flex items-center justify-center gap-2 py-3 rounded-xl bg-white/[0.06] hover:bg-white/10 text-white/45 hover:text-white transition-all text-xs font-semibold"
              @click="closeMenu">
              <img v-if="s.logoImage" :src="s.logoImage" :alt="s.name" class="w-4 h-4 brightness-0 invert opacity-60" />
              <span v-else class="w-4 h-4 flex items-center" v-html="s.icon" />
              {{ s.name }}
            </a>
          </div>
        </div>
      </div>
    </Transition>
  </Teleport>
</template>
