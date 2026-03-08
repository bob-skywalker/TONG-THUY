<script setup>
import { ref, onMounted } from 'vue'
import hoaSenLogo    from '../assets/hoasen.png'
import hoaphatLogo   from '../assets/hoaphat.png'
import blueScopeLogo from '../assets/blueScope.png'
import tongDongALogo from '../assets/tonDongA.png'
import tonNamKimLogo from '../assets/tonNamKim.png'
import tonPominaLogo from '../assets/tonPomina.png'

const isVisible = ref(false)

const partners = [
  { name: 'BlueScope',    logo: blueScopeLogo  },
  { name: 'Hoa Sen',      logo: hoaSenLogo      },
  { name: 'Hòa Phát',    logo: hoaphatLogo     },
  { name: 'Tôn Đông Á',  logo: tongDongALogo   },
  { name: 'Tôn Nam Kim',  logo: tonNamKimLogo   },
  { name: 'Tôn Pomina',   logo: tonPominaLogo   },
]

/* Duplicate for seamless 50% loop */
const row1 = [...partners, ...partners, ...partners, ...partners]

const stats = [
  { value: '6',    suffix: '',  label: 'Thương Hiệu Uy Tín' },
  { value: '10',   suffix: '+', label: 'Năm Phân Phối'       },
  { value: '100',  suffix: '%', label: 'Hàng Chính Hãng'     },
]

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => { if (entry.isIntersecting) isVisible.value = true },
    { threshold: 0.1 }
  )
  const el = document.querySelector('#about')
  if (el) observer.observe(el)
})
</script>

<template>
  <section id="about" class="relative py-24 overflow-hidden bg-slate-950">

    <!-- Ambient glow top -->
    <div class="pointer-events-none absolute -top-40 left-1/2 -translate-x-1/2 w-[700px] h-[400px] rounded-full bg-blue-600/10 blur-3xl" />

    <!-- Subtle grid texture -->
    <div
      class="pointer-events-none absolute inset-0 opacity-[0.035]"
      style="
        background-image:
          linear-gradient(rgba(148,163,184,0.4) 1px, transparent 1px),
          linear-gradient(90deg, rgba(148,163,184,0.4) 1px, transparent 1px);
        background-size: 48px 48px;
      "
    />

    <div class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">

      <!-- ── Header ─────────────────────────────── -->
      <div :class="['text-center mb-16', isVisible ? 'animate-fade-up' : 'opacity-0']">
        <!-- overline -->
        <div class="inline-flex items-center gap-2 mb-5">
          <span class="block w-8 h-px bg-blue-500 rounded" />
          <span class="text-xs font-bold uppercase tracking-[0.2em] text-blue-400">Đối Tác Chiến Lược</span>
          <span class="block w-8 h-px bg-blue-500 rounded" />
        </div>

        <h2 class="text-3xl sm:text-4xl md:text-5xl font-extrabold text-white leading-tight mb-5">
          Đại Lý Ủy Quyền Chính Thức<br class="hidden sm:block">
          <span class="text-gradient">Những Thương Hiệu Hàng Đầu</span>
        </h2>

        <p class="text-slate-300 max-w-xl mx-auto text-base sm:text-lg leading-relaxed">
          Phân phối tôn thép chính hãng từ các tập đoàn uy tín nhất<br class="hidden md:block">
          Việt Nam và quốc tế — chất lượng đảm bảo, giá tốt nhất.
        </p>
      </div>

      <!-- ── Marquee — single row, scroll left ─── -->
      <div
        class="relative mb-16 overflow-hidden"
        :class="isVisible ? 'animate-fade-up' : 'opacity-0'"
        style="animation-delay: 0.2s"
      >
        <!-- edge fades -->
        <div class="pointer-events-none absolute left-0 top-0 bottom-0 w-24 z-10 bg-gradient-to-r from-slate-950 to-transparent" />
        <div class="pointer-events-none absolute right-0 top-0 bottom-0 w-24 z-10 bg-gradient-to-l from-slate-950 to-transparent" />

        <div class="marquee-track flex gap-5">
          <div
            v-for="(p, i) in row1"
            :key="'r1-' + i"
            class="flex-shrink-0 flex items-center gap-3 px-7 py-5 bg-white rounded-2xl shadow-sm min-w-[190px] sm:min-w-[220px]"
          >
            <img
              :src="p.logo"
              :alt="p.name"
              class="h-10 sm:h-12 w-auto object-contain flex-shrink-0"
              loading="lazy"
              decoding="async"
            />
            <span class="text-sm font-semibold text-slate-700 whitespace-nowrap">{{ p.name }}</span>
          </div>
        </div>
      </div>

      <!-- ── Stats bar ───────────────────────────── -->
      <div
        :class="[
          'border-t border-white/10 pt-12 grid grid-cols-3 gap-4 sm:gap-8',
          isVisible ? 'animate-fade-up' : 'opacity-0',
        ]"
        style="animation-delay: 0.45s"
      >
        <div v-for="s in stats" :key="s.label" class="text-center">
          <p class="text-4xl sm:text-5xl font-extrabold text-white tabular-nums">
            {{ s.value }}<span class="text-blue-400">{{ s.suffix }}</span>
          </p>
          <p class="mt-2 text-xs sm:text-sm font-semibold uppercase tracking-widest text-slate-500">
            {{ s.label }}
          </p>
        </div>
      </div>

    </div>
  </section>
</template>
