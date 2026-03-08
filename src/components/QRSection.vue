<script setup>
import { ref, onMounted } from 'vue'
import zaloQRImage  from '../assets/Zalo-QRCode.jpg'
import zaloQRImage2 from '../assets/tonMatPuTongThuy.jpg'
import zaloLogo     from '../assets/Zalo-Logo.png'

const isVisible = ref(false)

const branches = [
  {
    phone: '0912 630 520',
    location: 'Chi Nhánh Đơn Dương',
    desc: 'Quét mã để kết nối Zalo trực tiếp',
    qr: zaloQRImage,
    color: 'blue',
  },
  {
    phone: '0947 196 779',
    location: 'Chi Nhánh Đức Trọng',
    desc: 'Quét mã để kết nối Zalo trực tiếp',
    qr: zaloQRImage2,
    color: 'indigo',
  },
]

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => { if (entry.isIntersecting) isVisible.value = true },
    { threshold: 0.1 }
  )
  const el = document.querySelector('#qr-section')
  if (el) observer.observe(el)
})
</script>

<template>
  <section id="qr-section" class="py-24 bg-slate-50">
    <div class="max-w-5xl mx-auto px-4 sm:px-6 lg:px-8">

      <!-- Header -->
      <div :class="['text-center mb-14', isVisible ? 'animate-fade-up' : 'opacity-0']">
        <p class="section-label justify-center">Zalo</p>
        <h2 class="text-3xl md:text-4xl font-extrabold text-slate-900 mb-4">
          Kết Nối Nhanh Qua <span class="text-gradient">Zalo</span>
        </h2>
        <p class="text-slate-500 max-w-md mx-auto">
          Quét mã QR để nhắn tin trực tiếp với chúng tôi — phản hồi nhanh trong vòng vài phút.
        </p>
      </div>

      <!-- QR Cards -->
      <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
        <div
          v-for="(branch, index) in branches"
          :key="branch.phone"
          :class="[
            'bg-white rounded-2xl border border-slate-100 shadow-sm hover:shadow-lg transition-all duration-300 p-8 flex flex-col items-center text-center hover:-translate-y-1',
            isVisible ? 'animate-fade-up' : 'opacity-0',
          ]"
          :style="`animation-delay: ${index * 0.15}s`"
        >
          <!-- Zalo Logo -->
          <div class="w-16 h-16 rounded-2xl bg-blue-50 border border-blue-100 flex items-center justify-center mb-6">
            <img :src="zaloLogo" alt="Zalo" class="w-10 h-10 object-contain" />
          </div>

          <!-- QR Code -->
          <div class="mb-6">
            <img
              :src="branch.qr"
              :alt="`QR ${branch.location}`"
              class="w-52 h-52 object-contain rounded-xl border border-slate-100 shadow-sm mx-auto"
            />
            <div class="mt-3 flex items-center justify-center gap-2">
              <span class="w-2 h-2 bg-blue-500 rounded-full animate-pulse" />
              <span class="text-blue-600 text-xs font-semibold">Quét để kết nối</span>
            </div>
          </div>

          <!-- Info -->
          <div class="mb-6">
            <div class="inline-flex items-center gap-1.5 text-slate-500 text-sm mb-2">
              <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" />
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" />
              </svg>
              {{ branch.location }}
            </div>
            <p class="text-2xl font-extrabold text-slate-900">{{ branch.phone }}</p>
          </div>

          <!-- Call CTA -->
          <a
            :href="`tel:${branch.phone.replace(/\s/g, '')}`"
            class="btn-primary w-full text-center text-sm py-3"
          >
            Gọi Ngay
          </a>
        </div>
      </div>

      <!-- How to scan -->
      <div :class="['mt-12 bg-white rounded-2xl border border-slate-100 p-8', isVisible ? 'animate-fade-up' : 'opacity-0']" style="animation-delay: 0.3s">
        <h3 class="text-center font-bold text-slate-900 mb-6">Cách sử dụng mã QR</h3>
        <div class="grid grid-cols-1 sm:grid-cols-3 gap-6 text-center">
          <div v-for="(step, i) in [
            { num: '1', label: 'Mở Camera', desc: 'Dùng camera điện thoại hoặc app quét QR' },
            { num: '2', label: 'Quét Mã', desc: 'Hướng camera vào mã QR và chờ nhận diện' },
            { num: '3', label: 'Kết Nối', desc: 'Nhấn vào link hiện ra để nhắn tin qua Zalo' },
          ]" :key="i">
            <div class="w-10 h-10 rounded-full bg-blue-600 text-white font-bold text-sm flex items-center justify-center mx-auto mb-3">{{ step.num }}</div>
            <p class="font-semibold text-slate-800 mb-1">{{ step.label }}</p>
            <p class="text-slate-500 text-sm">{{ step.desc }}</p>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>
