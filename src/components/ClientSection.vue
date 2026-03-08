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
  { name: 'BlueScope',    logo: blueScopeLogo, accent: 'hover:border-blue-400',   bg: 'hover:bg-blue-50/60'   },
  { name: 'Hoa Sen',      logo: hoaSenLogo,    accent: 'hover:border-red-400',    bg: 'hover:bg-red-50/60'    },
  { name: 'Hòa Phát',    logo: hoaphatLogo,   accent: 'hover:border-orange-400', bg: 'hover:bg-orange-50/60' },
  { name: 'Tôn Đông Á',  logo: tongDongALogo, accent: 'hover:border-blue-400',   bg: 'hover:bg-blue-50/60'   },
  { name: 'Tôn Nam Kim',  logo: tonNamKimLogo, accent: 'hover:border-yellow-400', bg: 'hover:bg-yellow-50/60' },
  { name: 'Tôn Pomina',   logo: tonPominaLogo, accent: 'hover:border-green-400',  bg: 'hover:bg-green-50/60'  },
]

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => { if (entry.isIntersecting) isVisible.value = true },
    { threshold: 0.15 }
  )
  const el = document.querySelector('#about')
  if (el) observer.observe(el)
})
</script>

<template>
  <section id="about" class="py-24 bg-white">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">

      <!-- Header -->
      <div :class="['text-center mb-14', isVisible ? 'animate-fade-up' : 'opacity-0']">
        <p class="section-label justify-center">Đối Tác</p>
        <h2 class="text-2xl md:text-3xl font-extrabold text-slate-900 mb-3">
          Đại Lý Chính Thức Các Thương Hiệu Hàng Đầu
        </h2>
        <p class="text-slate-500 max-w-xl mx-auto">
          Chúng tôi tự hào là đại lý phân phối ủy quyền của những thương hiệu tôn thép uy tín nhất thị trường.
        </p>
      </div>

      <!-- Partner Logo Grid -->
      <div class="grid grid-cols-2 md:grid-cols-3 gap-5">
        <div
          v-for="(partner, index) in partners"
          :key="partner.name"
          :class="[
            'group relative flex flex-col items-center justify-center gap-4 p-8 rounded-2xl border-2 border-slate-100 bg-slate-50 transition-all duration-300 cursor-default',
            'hover:shadow-lg hover:-translate-y-1',
            partner.accent,
            partner.bg,
            isVisible ? 'animate-fade-up' : 'opacity-0',
          ]"
          :style="`animation-delay: ${index * 0.08}s`"
        >
          <!-- Logo -->
          <div class="w-full flex items-center justify-center" style="height: 96px;">
            <img
              :src="partner.logo"
              :alt="partner.name"
              class="max-w-full max-h-full object-contain grayscale group-hover:grayscale-0 opacity-50 group-hover:opacity-100 transition-all duration-400 scale-90 group-hover:scale-100"
            />
          </div>

          <!-- Divider -->
          <div class="w-10 h-px bg-slate-200 group-hover:bg-slate-300 transition-colors duration-300" />

          <!-- Name -->
          <p class="text-sm font-bold text-slate-400 group-hover:text-slate-700 tracking-wide uppercase transition-colors duration-300">
            {{ partner.name }}
          </p>
        </div>
      </div>

      <!-- Trust strip -->
      <div :class="['mt-12 flex flex-wrap justify-center gap-8 text-center', isVisible ? 'animate-fade-up' : 'opacity-0']" style="animation-delay: 0.5s">
        <div v-for="item in [
          { value: '6', label: 'Thương Hiệu Uy Tín' },
          { value: '10+', label: 'Năm Đại Lý' },
          { value: '100%', label: 'Hàng Chính Hãng' },
        ]" :key="item.label" class="flex flex-col items-center gap-1">
          <span class="text-2xl font-extrabold text-blue-600">{{ item.value }}</span>
          <span class="text-xs font-semibold text-slate-400 uppercase tracking-wider">{{ item.label }}</span>
        </div>
      </div>

    </div>
  </section>
</template>
