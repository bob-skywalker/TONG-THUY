<script setup>
import { ref, onMounted } from 'vue'

const isVisible = ref(false)

const services = [
  {
    icon: `<svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M19 21V5a2 2 0 00-2-2H7a2 2 0 00-2 2v16m14 0h2m-2 0h-5m-9 0H3m2 0h5M9 7h1m-1 4h1m4-4h1m-1 4h1m-5 10v-5a1 1 0 011-1h2a1 1 0 011 1v5m-4 0h4"/></svg>`,
    title: 'Tôn Cao Cấp Bluescope',
    description: 'Phân phối độc quyền tôn Bluescope Zacs — tiêu chuẩn quốc tế, chống ăn mòn vượt trội, bền trên 30 năm.',
    color: 'blue',
  },
  {
    icon: `<svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z"/></svg>`,
    title: 'Tôn Xốp PU Cách Nhiệt',
    description: 'Giải pháp cách nhiệt — cách âm toàn diện. Giảm nhiệt độ trong nhà đến 8°C, tiết kiệm điện năng đáng kể.',
    color: 'green',
  },
  {
    icon: `<svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M19.428 15.428a2 2 0 00-1.022-.547l-2.387-.477a6 6 0 00-3.86.517l-.318.158a6 6 0 01-3.86.517L6.05 15.21a2 2 0 00-1.806.547M8 4h8l-1 1v5.172a2 2 0 00.586 1.414l5 5c1.26 1.26.367 3.414-1.415 3.414H4.828c-1.782 0-2.674-2.154-1.414-3.414l5-5A2 2 0 009 10.172V5L8 4z"/></svg>`,
    title: 'Xà Gồ & Kèo Mái',
    description: 'Sản xuất và thi công xà gồ C, Z thép nguội. Kết cấu khung mái vững chắc, định hình theo bản vẽ.',
    color: 'purple',
  },
  {
    icon: `<svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M3.055 11H5a2 2 0 012 2v1a2 2 0 002 2 2 2 0 012 2v2.945M8 3.935V5.5A2.5 2.5 0 0010.5 8h.5a2 2 0 012 2 2 2 0 104 0 2 2 0 012-2h1.064M15 20.488V18a2 2 0 012-2h3.064M21 12a9 9 0 11-18 0 9 9 0 0118 0z"/></svg>`,
    title: 'Vật Tư Nhà Kính',
    description: 'Cung cấp đầy đủ vật tư cho nhà kính nông nghiệp — tôn PC sóng, màng PE, khung nhôm, phụ kiện chính hãng.',
    color: 'yellow',
  },
  {
    icon: `<svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.065-2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.608 2.296.07 2.572-1.065z"/><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"/></svg>`,
    title: 'Gia Công Chuyên Nghiệp',
    description: 'Chấn diềm, máng xối, chớp gió — gia công chính xác theo kích thước yêu cầu, giao hàng tận công trình.',
    color: 'red',
  },
  {
    icon: `<svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M4 7v10c0 2.21 3.582 4 8 4s8-1.79 8-4V7M4 7c0 2.21 3.582 4 8 4s8-1.79 8-4M4 7c0-2.21 3.582-4 8-4s8 1.79 8 4m0 5c0 2.21-3.582 4-8 4s-8-1.79-8-4"/></svg>`,
    title: 'Uốn Sắt Định Hình',
    description: 'Uốn sắt theo hình U, V, O và các dạng đặc biệt theo yêu cầu. Máy móc hiện đại, độ chính xác cao.',
    color: 'indigo',
  },
]

const colorMap = {
  blue:   { bg: 'bg-blue-50',   icon: 'bg-blue-100 text-blue-600',   border: 'group-hover:border-blue-200' },
  green:  { bg: 'bg-green-50',  icon: 'bg-green-100 text-green-600',  border: 'group-hover:border-green-200' },
  purple: { bg: 'bg-purple-50', icon: 'bg-purple-100 text-purple-600', border: 'group-hover:border-purple-200' },
  yellow: { bg: 'bg-amber-50',  icon: 'bg-amber-100 text-amber-600',  border: 'group-hover:border-amber-200' },
  red:    { bg: 'bg-red-50',    icon: 'bg-red-100 text-red-600',    border: 'group-hover:border-red-200' },
  indigo: { bg: 'bg-indigo-50', icon: 'bg-indigo-100 text-indigo-600', border: 'group-hover:border-indigo-200' },
}

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => { if (entry.isIntersecting) isVisible.value = true },
    { threshold: 0.1 }
  )
  const el = document.querySelector('#services')
  if (el) observer.observe(el)
})
</script>

<template>
  <section id="services" class="py-24 bg-white">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">

      <!-- Header -->
      <div :class="['text-center mb-16', isVisible ? 'animate-fade-up' : 'opacity-0']">
        <p class="section-label justify-center">Dịch Vụ</p>
        <h2 class="text-3xl md:text-4xl font-extrabold text-slate-900 mb-4">
          Giải Pháp Toàn Diện<br />
          <span class="text-gradient">Cho Mọi Công Trình</span>
        </h2>
        <p class="text-slate-500 max-w-2xl mx-auto text-lg leading-relaxed">
          Từ nguyên vật liệu đến thi công hoàn thiện — chúng tôi cung cấp mọi thứ bạn cần cho mái nhà và kết cấu thép.
        </p>
      </div>

      <!-- Services Grid -->
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
        <div
          v-for="(service, index) in services"
          :key="service.title"
          :class="[
            'group p-7 rounded-2xl border-2 border-transparent hover:border-gray-100 bg-gray-50 hover:bg-white transition-all duration-300 hover:shadow-lg hover:-translate-y-1',
            isVisible ? 'animate-fade-up' : 'opacity-0',
          ]"
          :style="`animation-delay: ${index * 0.08}s`"
        >
          <!-- Icon -->
          <div :class="['inline-flex items-center justify-center w-14 h-14 rounded-xl mb-5', colorMap[service.color].icon]" v-html="service.icon" />

          <!-- Content -->
          <h3 class="text-lg font-bold text-slate-900 mb-2">{{ service.title }}</h3>
          <p class="text-slate-500 text-sm leading-relaxed">{{ service.description }}</p>
        </div>
      </div>

    </div>
  </section>
</template>
