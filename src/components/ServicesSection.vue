<script setup>
import { ref, onMounted } from 'vue'
import logo1 from '../assets/logo-1.png'
import logo2 from '../assets/logo-2.png'
import logo3 from '../assets/logo-3.png'
import logo4 from '../assets/logo-4.png'
import logo5 from '../assets/logo-5.png'
import logo6 from '../assets/logo-6.png'

const isVisible = ref(false)

const services = [
  { title: 'Tôn Cao Cấp Bluescope',   description: 'Phân phối độc quyền tôn Bluescope Zacs — tiêu chuẩn quốc tế, chống ăn mòn vượt trội, bền trên 30 năm.',                                     accent: 'blue',    logo: logo1 },
  { title: 'Tôn Xốp PU Cách Nhiệt',   description: 'Giảm nhiệt độ trong nhà đến 8°C, cách âm toàn diện, tiết kiệm điện năng đáng kể cho mọi công trình.',                                      accent: 'emerald', logo: logo2 },
  { title: 'Xà Gồ & Kèo Mái',        description: 'Sản xuất và thi công xà gồ C, Z thép nguội. Kết cấu khung mái vững chắc, định hình theo bản vẽ.',                                           accent: 'violet',  logo: logo3 },
  { title: 'Vật Tư Nhà Kính',         description: 'Cung cấp đầy đủ vật tư cho nhà kính nông nghiệp — tôn PC sóng, màng PE, khung nhôm, phụ kiện chính hãng.',                                 accent: 'amber',   logo: logo4 },
  { title: 'Gia Công Chuyên Nghiệp',  description: 'Chấn diềm, máng xối, chớp gió — gia công chính xác theo kích thước yêu cầu, giao hàng tận công trình.',                                    accent: 'rose',    logo: logo5 },
  { title: 'Uốn Sắt Định Hình',       description: 'Uốn sắt theo hình U, V, O và các dạng đặc biệt theo yêu cầu. Máy móc hiện đại, độ chính xác cao.',                                         accent: 'sky',     logo: logo6 },
]

const stats = [
  { val: '500+', label: 'Khách Hàng' },
  { val: '30+',  label: 'Năm Kinh Nghiệm' },
  { val: '2',    label: 'Chi Nhánh' },
  { val: '100%', label: 'Hàng Chính Hãng' },
]

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => { if (entry.isIntersecting) isVisible.value = true },
    { threshold: 0.08 }
  )
  const el = document.querySelector('#services')
  if (el) observer.observe(el)
})
</script>

<template>
  <section id="services" class="relative py-24 md:py-32 bg-slate-900 overflow-hidden">

    <!-- Ambient glows -->
    <div class="pointer-events-none absolute inset-0">
      <div class="absolute top-0 right-1/4 w-[600px] h-[500px] rounded-full bg-blue-700/8 blur-[120px]" />
      <div class="absolute bottom-0 left-1/4 w-[400px] h-[400px] rounded-full bg-violet-700/6 blur-[100px]" />
    </div>

    <!-- Subtle grid texture -->
    <div
      class="pointer-events-none absolute inset-0 opacity-[0.03]"
      style="
        background-image:
          linear-gradient(rgba(148,163,184,0.4) 1px, transparent 1px),
          linear-gradient(90deg, rgba(148,163,184,0.4) 1px, transparent 1px);
        background-size: 48px 48px;
      "
    />

    <div class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">

      <!-- Header -->
      <div :class="['mb-16 md:mb-20', isVisible ? 'animate-fade-up' : 'opacity-0']">
        <div class="flex items-center gap-3 mb-5">
          <span class="block w-8 h-px bg-blue-500 rounded" />
          <span class="text-[11px] font-bold uppercase tracking-[0.2em] text-blue-400">Sản Phẩm</span>
        </div>
        <div class="flex flex-col md:flex-row md:items-end md:justify-between gap-4">
          <h2 class="text-3xl sm:text-4xl md:text-5xl font-extrabold text-white leading-[1.1]">
            Giải Pháp Toàn Diện<br />
            <span class="text-gradient">Cho Mọi Công Trình</span>
          </h2>
          <p class="text-slate-200 text-base sm:text-lg leading-relaxed max-w-xs">
            Từ nguyên vật liệu đến thi công hoàn thiện — chúng tôi có tất cả.
          </p>
        </div>
      </div>

      <!-- Cards grid -->
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-5">
        <div
          v-for="(s, i) in services"
          :key="s.title"
          :class="['group rounded-2xl bg-slate-900 shadow-lg hover:shadow-2xl hover:shadow-blue-900/30 transition-all duration-400 hover:-translate-y-1 overflow-hidden', isVisible ? 'animate-fade-up' : 'opacity-0']"
          :style="`animation-delay: ${0.05 + i * 0.07}s`"
        >
          <!-- Image -->
          <div class="relative overflow-hidden" style="height: 240px;">
            <img :src="s.logo" :alt="s.title" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500" loading="lazy" />
            <!-- Gradient overlay -->
            <div class="absolute inset-0 bg-gradient-to-t from-slate-950 via-slate-950/30 to-transparent" />
            <!-- Tag -->
            <div class="absolute top-3 left-3">
              <span class="bg-blue-600/90 backdrop-blur-sm text-white text-xs font-semibold px-2.5 py-1 rounded-full">
                {{ String(i + 1).padStart(2, '0') }}
              </span>
            </div>
          </div>
          <!-- Title & description -->
          <div class="p-5">
            <h3 class="text-white font-bold text-base mb-1">{{ s.title }}</h3>
            <p class="text-slate-300 text-base leading-relaxed font-medium">{{ s.description }}</p>
          </div>
        </div>
      </div>

      <!-- Trust strip -->
      <div
        :class="['mt-14 border-t border-white/10 pt-12 grid grid-cols-2 sm:grid-cols-4 gap-8', isVisible ? 'animate-fade-up' : 'opacity-0']"
        style="animation-delay: 0.5s"
      >
        <div v-for="item in stats" :key="item.label" class="text-center">
          <p class="text-4xl sm:text-5xl font-extrabold text-white tabular-nums">
            <span class="text-gradient">{{ item.val }}</span>
          </p>
          <p class="mt-2 text-xs sm:text-sm font-semibold uppercase tracking-widest text-slate-400">{{ item.label }}</p>
        </div>
      </div>

    </div>
  </section>
</template>
