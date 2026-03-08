<script setup>
import { ref, onMounted } from 'vue'

const isVisible = ref(false)

const services = [
  {
    title: 'Tôn Cao Cấp Bluescope',
    description: 'Phân phối độc quyền tôn Bluescope Zacs — tiêu chuẩn quốc tế, chống ăn mòn vượt trội, bền trên 30 năm.',
    accent: 'blue',
  },
  {
    title: 'Tôn Xốp PU Cách Nhiệt',
    description: 'Giảm nhiệt độ trong nhà đến 8°C, cách âm toàn diện, tiết kiệm điện năng đáng kể cho mọi công trình.',
    accent: 'emerald',
  },
  {
    title: 'Xà Gồ & Kèo Mái',
    description: 'Sản xuất và thi công xà gồ C, Z thép nguội. Kết cấu khung mái vững chắc, định hình theo bản vẽ.',
    accent: 'violet',
  },
  {
    title: 'Vật Tư Nhà Kính',
    description: 'Cung cấp đầy đủ vật tư cho nhà kính nông nghiệp — tôn PC sóng, màng PE, khung nhôm, phụ kiện chính hãng.',
    accent: 'amber',
  },
  {
    title: 'Gia Công Chuyên Nghiệp',
    description: 'Chấn diềm, máng xối, chớp gió — gia công chính xác theo kích thước yêu cầu, giao hàng tận công trình.',
    accent: 'rose',
  },
  {
    title: 'Uốn Sắt Định Hình',
    description: 'Uốn sắt theo hình U, V, O và các dạng đặc biệt theo yêu cầu. Máy móc hiện đại, độ chính xác cao.',
    accent: 'sky',
  },
]

const stats = [
  { val: '500+', label: 'Khách Hàng' },
  { val: '10+',  label: 'Năm Kinh Nghiệm' },
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
  <section id="services" class="relative py-24 md:py-32 bg-slate-950 overflow-hidden">

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
          <span class="text-[11px] font-bold uppercase tracking-[0.2em] text-blue-400">Dịch Vụ</span>
        </div>
        <div class="flex flex-col md:flex-row md:items-end md:justify-between gap-4">
          <h2 class="text-3xl sm:text-4xl md:text-5xl font-extrabold text-white leading-[1.1]">
            Giải Pháp Toàn Diện<br />
            <span class="text-gradient">Cho Mọi Công Trình</span>
          </h2>
          <p class="text-slate-300 text-sm sm:text-base leading-relaxed max-w-xs">
            Từ nguyên vật liệu đến thi công hoàn thiện — chúng tôi có tất cả.
          </p>
        </div>
      </div>

      <!-- Cards grid -->
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4">

        <!-- 01 — Bluescope Roofing -->
        <div
          :class="['group relative bg-white/[0.03] rounded-2xl border border-white/[0.07] p-8 hover:bg-white/[0.06] hover:border-white/[0.12] transition-all duration-300 overflow-hidden cursor-default', isVisible ? 'animate-fade-up' : 'opacity-0']"
          style="animation-delay: 0.05s"
        >
          <span class="absolute top-6 right-7 text-[11px] font-bold tabular-nums text-white/10 tracking-widest">01</span>
          <div class="inline-flex items-center justify-center w-12 h-12 rounded-xl bg-blue-500/10 text-blue-400 mb-6">
            <!-- Corrugated roofing sheet — solid profile -->
            <svg class="w-6 h-6" viewBox="0 0 24 24" fill="currentColor">
              <path d="M2 17h20v2H2v-2zm1.5-5h1c.28 0 .5.22.5.5V14h-2v-1.5c0-.28.22-.5.5-.5zm3 0h1c.28 0 .5.22.5.5V14H6v-1.5c0-.28.22-.5.5-.5zm3 0h1c.28 0 .5.22.5.5V14H9v-1.5c0-.28.22-.5.5-.5zm3 0h1c.28 0 .5.22.5.5V14h-2v-1.5c0-.28.22-.5.5-.5zm3 0h1c.28 0 .5.22.5.5V14h-2v-1.5c0-.28.22-.5.5-.5zm3 0h.5c.28 0 .5.22.5.5V14h-1.5l.5-1.5z"/>
              <path d="M12 3L2 9.5V12h20V9.5L12 3zm0 2.18L19.5 10H4.5L12 5.18z"/>
            </svg>
          </div>
          <h3 class="font-bold text-white text-[17px] leading-snug mb-2.5">{{ services[0].title }}</h3>
          <p class="text-slate-300 text-sm leading-relaxed">{{ services[0].description }}</p>
          <div class="absolute bottom-0 left-0 w-full h-[2px] bg-blue-500 scale-x-0 group-hover:scale-x-100 transition-transform duration-400 origin-left" />
        </div>

        <!-- 02 — PU Insulation -->
        <div
          :class="['group relative bg-white/[0.03] rounded-2xl border border-white/[0.07] p-8 hover:bg-white/[0.06] hover:border-white/[0.12] transition-all duration-300 overflow-hidden cursor-default', isVisible ? 'animate-fade-up' : 'opacity-0']"
          style="animation-delay: 0.12s"
        >
          <span class="absolute top-6 right-7 text-[11px] font-bold tabular-nums text-white/10 tracking-widest">02</span>
          <div class="inline-flex items-center justify-center w-12 h-12 rounded-xl bg-emerald-500/10 text-emerald-400 mb-6">
            <!-- Sandwich panel cross-section layers -->
            <svg class="w-6 h-6" viewBox="0 0 24 24" fill="currentColor">
              <rect x="2" y="3" width="20" height="3.5" rx="1"/>
              <rect x="2" y="8" width="20" height="7" rx="1" opacity="0.55"/>
              <rect x="2" y="17" width="20" height="3.5" rx="1"/>
              <path d="M9.5 11.5l1.5 1.5 3-3" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" fill="none"/>
            </svg>
          </div>
          <h3 class="font-bold text-white text-[17px] leading-snug mb-2.5">{{ services[1].title }}</h3>
          <p class="text-slate-300 text-sm leading-relaxed">{{ services[1].description }}</p>
          <div class="absolute bottom-0 left-0 w-full h-[2px] bg-emerald-500 scale-x-0 group-hover:scale-x-100 transition-transform duration-400 origin-left" />
        </div>

        <!-- 03 — Purlins -->
        <div
          :class="['group relative bg-white/[0.03] rounded-2xl border border-white/[0.07] p-8 hover:bg-white/[0.06] hover:border-white/[0.12] transition-all duration-300 overflow-hidden cursor-default', isVisible ? 'animate-fade-up' : 'opacity-0']"
          style="animation-delay: 0.19s"
        >
          <span class="absolute top-6 right-7 text-[11px] font-bold tabular-nums text-white/10 tracking-widest">03</span>
          <div class="inline-flex items-center justify-center w-12 h-12 rounded-xl bg-violet-500/10 text-violet-400 mb-6">
            <!-- C-channel / purlin cross-section -->
            <svg class="w-6 h-6" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
              <path d="M17 4H7v3h6v10H7v3h10" fill="currentColor" fill-opacity="0.15"/>
              <path d="M17 4H7v3h6v10H7v3h10"/>
            </svg>
          </div>
          <h3 class="font-bold text-white text-[17px] leading-snug mb-2.5">{{ services[2].title }}</h3>
          <p class="text-slate-300 text-sm leading-relaxed">{{ services[2].description }}</p>
          <div class="absolute bottom-0 left-0 w-full h-[2px] bg-violet-500 scale-x-0 group-hover:scale-x-100 transition-transform duration-400 origin-left" />
        </div>

        <!-- 04 — Greenhouse -->
        <div
          :class="['group relative bg-white/[0.03] rounded-2xl border border-white/[0.07] p-8 hover:bg-white/[0.06] hover:border-white/[0.12] transition-all duration-300 overflow-hidden cursor-default', isVisible ? 'animate-fade-up' : 'opacity-0']"
          style="animation-delay: 0.26s"
        >
          <span class="absolute top-6 right-7 text-[11px] font-bold tabular-nums text-white/10 tracking-widest">04</span>
          <div class="inline-flex items-center justify-center w-12 h-12 rounded-xl bg-amber-500/10 text-amber-400 mb-6">
            <!-- Greenhouse arch -->
            <svg class="w-6 h-6" viewBox="0 0 24 24" fill="currentColor">
              <path d="M12 2C7.58 2 4 5.58 4 10v11h2V10a6 6 0 0112 0v11h2V10c0-4.42-3.58-8-8-8z" opacity="0.9"/>
              <rect x="3" y="20" width="18" height="2" rx="1"/>
              <line x1="12" y1="4" x2="12" y2="21" stroke="currentColor" stroke-width="1.2" opacity="0.4"/>
              <line x1="4" y1="14" x2="20" y2="14" stroke="currentColor" stroke-width="1.2" opacity="0.4"/>
            </svg>
          </div>
          <h3 class="font-bold text-white text-[17px] leading-snug mb-2.5">{{ services[3].title }}</h3>
          <p class="text-slate-300 text-sm leading-relaxed">{{ services[3].description }}</p>
          <div class="absolute bottom-0 left-0 w-full h-[2px] bg-amber-500 scale-x-0 group-hover:scale-x-100 transition-transform duration-400 origin-left" />
        </div>

        <!-- 05 — Fabrication -->
        <div
          :class="['group relative bg-white/[0.03] rounded-2xl border border-white/[0.07] p-8 hover:bg-white/[0.06] hover:border-white/[0.12] transition-all duration-300 overflow-hidden cursor-default', isVisible ? 'animate-fade-up' : 'opacity-0']"
          style="animation-delay: 0.33s"
        >
          <span class="absolute top-6 right-7 text-[11px] font-bold tabular-nums text-white/10 tracking-widest">05</span>
          <div class="inline-flex items-center justify-center w-12 h-12 rounded-xl bg-rose-500/10 text-rose-400 mb-6">
            <!-- Precision cut / guillotine shear blade -->
            <svg class="w-6 h-6" viewBox="0 0 24 24" fill="currentColor">
              <path d="M3 3h18v3H3z"/>
              <path d="M3 18h18v3H3z"/>
              <path d="M5 6l7 6-7 6h3l7-6-7-6H5z" opacity="0.8"/>
              <rect x="17" y="6" width="2" height="12" rx="1" opacity="0.5"/>
            </svg>
          </div>
          <h3 class="font-bold text-white text-[17px] leading-snug mb-2.5">{{ services[4].title }}</h3>
          <p class="text-slate-300 text-sm leading-relaxed">{{ services[4].description }}</p>
          <div class="absolute bottom-0 left-0 w-full h-[2px] bg-rose-500 scale-x-0 group-hover:scale-x-100 transition-transform duration-400 origin-left" />
        </div>

        <!-- 06 — Steel Bending -->
        <div
          :class="['group relative bg-white/[0.03] rounded-2xl border border-white/[0.07] p-8 hover:bg-white/[0.06] hover:border-white/[0.12] transition-all duration-300 overflow-hidden cursor-default', isVisible ? 'animate-fade-up' : 'opacity-0']"
          style="animation-delay: 0.4s"
        >
          <span class="absolute top-6 right-7 text-[11px] font-bold tabular-nums text-white/10 tracking-widest">06</span>
          <div class="inline-flex items-center justify-center w-12 h-12 rounded-xl bg-sky-500/10 text-sky-400 mb-6">
            <!-- U-shape bent steel bar -->
            <svg class="w-6 h-6" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.8" stroke-linecap="round" stroke-linejoin="round">
              <path d="M5 4v10a7 7 0 0014 0V4" fill="currentColor" fill-opacity="0.1"/>
              <path d="M5 4v10a7 7 0 0014 0V4"/>
              <line x1="3" y1="4" x2="7" y2="4"/>
              <line x1="17" y1="4" x2="21" y2="4"/>
            </svg>
          </div>
          <h3 class="font-bold text-white text-[17px] leading-snug mb-2.5">{{ services[5].title }}</h3>
          <p class="text-slate-300 text-sm leading-relaxed">{{ services[5].description }}</p>
          <div class="absolute bottom-0 left-0 w-full h-[2px] bg-sky-500 scale-x-0 group-hover:scale-x-100 transition-transform duration-400 origin-left" />
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
          <p class="mt-2 text-xs sm:text-sm font-semibold uppercase tracking-widest text-slate-500">{{ item.label }}</p>
        </div>
      </div>

    </div>
  </section>
</template>
