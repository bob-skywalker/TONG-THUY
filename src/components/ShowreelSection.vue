<script setup>
import { ref } from 'vue'
import thumbnail from '../assets/official-thumb.jpg'

const playing  = ref(false)
const videoRef = ref(null)

const play = () => {
  playing.value = true
  // Let the DOM update, then play + show controls
  setTimeout(() => {
    if (videoRef.value) {
      videoRef.value.play().catch(() => {})
    }
  }, 50)
}
</script>

<template>
  <section class="relative bg-[#070D1F]">

    <!-- Section label -->
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 pt-14 pb-7">
      <div class="flex items-center gap-3">
        <span class="block w-8 h-0.5 bg-blue-400 rounded-full" />
        <span class="text-[11px] font-bold uppercase tracking-[0.2em] text-blue-400">Video Giới Thiệu</span>
      </div>
      <h2 class="mt-3 text-2xl sm:text-3xl md:text-4xl font-extrabold text-white leading-tight">
        Tòng Thuỷ — Tôn Thép Uy Tín<br class="hidden sm:block" />
        <span class="text-gradient-light">Lâm Đồng & Tây Nguyên</span>
      </h2>
    </div>

    <!-- Video player — full width, no side padding -->
    <div class="relative w-full bg-black" style="aspect-ratio: 16/9;">

      <!-- Thumbnail + play overlay (shown before play) -->
      <Transition
        leave-active-class="transition duration-400 ease-in"
        leave-from-class="opacity-100"
        leave-to-class="opacity-0"
      >
        <div
          v-if="!playing"
          class="absolute inset-0 z-10 cursor-pointer group"
          @click="play"
        >
          <!-- Thumbnail -->
          <img
            :src="thumbnail"
            alt="Video giới thiệu Tòng Thuỷ"
            class="w-full h-full object-cover"
            loading="lazy"
            decoding="async"
          />

          <!-- Dark gradient overlay -->
          <div class="absolute inset-0 bg-gradient-to-t from-black/60 via-black/20 to-black/10" />

          <!-- Play button -->
          <div class="absolute inset-0 flex items-center justify-center">
            <div class="relative flex items-center justify-center">
              <!-- Pulse ring -->
              <div class="absolute w-24 h-24 sm:w-28 sm:h-28 rounded-full bg-white/10 animate-ping" style="animation-duration: 2s;" />
              <!-- Button circle -->
              <div class="relative w-20 h-20 sm:w-24 sm:h-24 rounded-full bg-white/95 group-hover:bg-white group-hover:scale-110 transition-all duration-300 flex items-center justify-center shadow-2xl shadow-black/50">
                <svg class="w-8 h-8 sm:w-9 sm:h-9 text-blue-600 ml-1" fill="currentColor" viewBox="0 0 24 24">
                  <path d="M8 5v14l11-7z" />
                </svg>
              </div>
            </div>
          </div>

          <!-- Bottom bar caption -->
          <div class="absolute bottom-0 left-0 right-0 px-6 sm:px-10 pb-6 sm:pb-8">
            <p class="text-white/50 text-xs sm:text-sm font-medium">
              Nhấn để xem video giới thiệu đầy đủ
            </p>
          </div>
        </div>
      </Transition>

      <!-- Actual video (rendered always, shown when playing) -->
      <video
        ref="videoRef"
        class="absolute inset-0 w-full h-full object-contain bg-black"
        :class="playing ? 'z-20' : 'z-0'"
        controls
        playsinline
        preload="metadata"
        @ended="playing = false"
      >
        <source src="/VIDEO/OFFICIAL_VIDEO.mp4" type="video/mp4" />
      </video>

    </div>

    <!-- Bottom spacer -->
    <div class="h-14" />

  </section>
</template>
