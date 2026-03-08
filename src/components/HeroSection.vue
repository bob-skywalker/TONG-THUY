<script setup>
import { ref, onMounted } from 'vue'

const isLoaded = ref(false)

const stats = [
  { value: '500+', label: 'Khách Hàng' },
  { value: '10+', label: 'Năm Kinh Nghiệm' },
  { value: '2', label: 'Chi Nhánh' },
  { value: '6', label: 'Dòng Sản Phẩm' },
]

onMounted(() => {
  setTimeout(() => {
    isLoaded.value = true
  }, 100)
})
</script>

<template>
  <section id="home" class="relative w-full min-h-screen flex flex-col overflow-hidden">

    <!-- Video Background -->
    <video
      class="absolute inset-0 w-full h-full object-cover"
      autoplay muted loop playsinline
      preload="auto"
    >
      <source :src="'/VIDEO/1.MP4'" type="video/mp4" />
    </video>

    <!-- Overlay -->
    <div class="hero-overlay absolute inset-0" />

    <!-- Subtle grid pattern -->
    <div
      class="absolute inset-0 opacity-5"
      style="background-image: linear-gradient(rgba(255,255,255,0.1) 1px, transparent 1px), linear-gradient(90deg, rgba(255,255,255,0.1) 1px, transparent 1px); background-size: 60px 60px;"
    />

    <!-- Main Content -->
    <div class="relative z-10 flex-1 flex items-center">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 w-full pt-28 pb-16">
        <div class="max-w-3xl">

          <!-- Overline badge -->
          <div
            :class="['flex items-center gap-3 mb-6', isLoaded ? 'animate-fade-up' : 'opacity-0']"
          >
            <span class="flex items-center gap-2 bg-blue-600/20 border border-blue-400/30 text-blue-300 text-xs font-semibold tracking-widest uppercase px-4 py-1.5 rounded-full backdrop-blur-sm">
              <span class="w-1.5 h-1.5 bg-blue-400 rounded-full animate-pulse" />
              Đức Trọng · Lâm Đồng
            </span>
          </div>

          <!-- Headline -->
          <h1
            :class="['text-5xl sm:text-6xl md:text-7xl font-extrabold leading-tight mb-6 text-white', isLoaded ? 'animate-fade-up' : 'opacity-0']"
            style="animation-delay: 0.1s"
          >
            Vật Liệu
            <br />
            <span class="text-gradient-light">Xây Dựng</span>
            <br />
            Tòng Thuỷ
          </h1>

          <!-- Subheadline -->
          <p
            :class="['text-lg md:text-xl text-slate-300 mb-10 leading-relaxed max-w-xl', isLoaded ? 'animate-fade-up' : 'opacity-0']"
            style="animation-delay: 0.2s"
          >
            Chuyên phân phối tôn cao cấp Bluescope, vật liệu cách nhiệt PU và giải pháp mái hoàn chỉnh cho nhà ở, nhà xưởng và công trình nông nghiệp.
          </p>

          <!-- CTAs -->
          <div
            :class="['flex flex-wrap gap-4', isLoaded ? 'animate-fade-up' : 'opacity-0']"
            style="animation-delay: 0.3s"
          >
            <a href="#products" class="btn-primary text-base">
              Xem Sản Phẩm
            </a>
            <a href="#contact" class="btn-outline text-base">
              Liên Hệ Ngay
            </a>
          </div>
        </div>
      </div>
    </div>

    <!-- Stats Bar -->
    <div class="relative z-10 border-t border-white/10 bg-black/30 backdrop-blur-md">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid grid-cols-2 md:grid-cols-4 divide-x divide-white/10">
          <div
            v-for="stat in stats"
            :key="stat.label"
            :class="['py-6 px-8 text-center', isLoaded ? 'animate-fade-up' : 'opacity-0']"
            style="animation-delay: 0.4s"
          >
            <div class="text-3xl md:text-4xl font-extrabold text-white mb-1">{{ stat.value }}</div>
            <div class="text-xs font-semibold tracking-wider text-slate-300 uppercase">{{ stat.label }}</div>
          </div>
        </div>
      </div>
    </div>

    <!-- Scroll Indicator -->
    <div
      :class="['absolute bottom-28 md:bottom-24 right-8 md:right-12 flex flex-col items-center gap-2', isLoaded ? 'animate-fade-up' : 'opacity-0']"
      style="animation-delay: 0.6s"
    >
      <span class="text-white/40 text-xs font-medium tracking-widest uppercase" style="writing-mode: vertical-rl">Cuộn xuống</span>
      <div class="w-px h-12 bg-gradient-to-b from-white/40 to-transparent" />
    </div>
  </section>
</template>
