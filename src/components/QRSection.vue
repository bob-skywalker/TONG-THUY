<script setup>
import { ref, onMounted } from 'vue'
import zaloQRImage  from '../assets/Zalo-QRCode.jpg'
import zaloQRImage2 from '../assets/tonMatPuTongThuy.jpg'
import zaloLogo     from '../assets/Zalo-Logo.png'

const isVisible = ref(false)

const branches = [
  {
    phone:    '0912 630 520',
    location: 'Chi Nhánh Đơn Dương',
    address:  '40A Tân Lập, Xã Ka Đô, Lâm Đồng',
    qr:       zaloQRImage,
  },
  {
    phone:    '0947 196 779',
    location: 'Chi Nhánh Đức Trọng',
    address:  'Phú Thạnh, Hiệp Thạnh, Đức Trọng',
    qr:       zaloQRImage2,
  },
]

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => { if (entry.isIntersecting) isVisible.value = true },
    { threshold: 0.08 }
  )
  const el = document.querySelector('#qr-section')
  if (el) observer.observe(el)
})
</script>

<template>
  <section id="qr-section" class="relative py-28 md:py-36 overflow-hidden bg-[#060c1a]">

    <!-- Background grid -->
    <div class="absolute inset-0 opacity-[0.04]"
         style="background-image: linear-gradient(rgba(96,165,250,1) 1px, transparent 1px), linear-gradient(90deg, rgba(96,165,250,1) 1px, transparent 1px); background-size: 48px 48px;" />

    <!-- Glow orbs -->
    <div class="absolute -top-32 -left-32 w-[500px] h-[500px] rounded-full bg-blue-600/10 blur-[120px] pointer-events-none" />
    <div class="absolute -bottom-32 -right-32 w-[500px] h-[500px] rounded-full bg-blue-500/10 blur-[120px] pointer-events-none" />
    <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[800px] h-[400px] rounded-full bg-blue-700/5 blur-[100px] pointer-events-none" />

    <div class="relative max-w-5xl mx-auto px-4 sm:px-6 lg:px-8">

      <!-- Header -->
      <div :class="['text-center mb-16', isVisible ? 'animate-fade-up' : 'opacity-0']">
        <!-- Pill label -->
        <div class="inline-flex items-center gap-2.5 mb-6 px-4 py-2 rounded-full border border-blue-500/20 bg-blue-500/5 backdrop-blur-sm">
          <img :src="zaloLogo" alt="Zalo" class="w-4 h-4 object-contain" />
          <span class="text-[11px] font-bold uppercase tracking-[0.25em] text-blue-400">Kết Nối Zalo</span>
          <span class="w-1.5 h-1.5 rounded-full bg-emerald-400 animate-pulse" />
        </div>

        <h2 class="text-4xl sm:text-5xl font-extrabold text-white leading-tight mb-4 tracking-tight">
          Nhắn Tin &amp;
          <span class="relative inline-block">
            <span class="text-gradient-light">Báo Giá Nhanh</span>
          </span>
        </h2>
        <p class="text-slate-300 text-sm sm:text-base max-w-md mx-auto leading-relaxed">
          Quét mã QR bằng Zalo để nhắn tin trực tiếp.<br class="hidden sm:block"/>
          Phản hồi trong <span class="text-blue-400 font-semibold">vài phút</span>.
        </p>
      </div>

      <!-- Cards grid -->
      <div class="grid sm:grid-cols-2 gap-5 lg:gap-6">
        <div
          v-for="(branch, index) in branches"
          :key="branch.phone"
          :class="[
            'group relative rounded-2xl overflow-hidden',
            isVisible ? 'animate-fade-up' : 'opacity-0',
          ]"
          :style="`animation-delay: ${0.1 + index * 0.12}s`"
        >
          <!-- Gradient border via pseudo wrapper -->
          <div class="absolute inset-0 rounded-2xl p-px bg-gradient-to-br from-blue-500/40 via-blue-600/10 to-transparent group-hover:from-blue-400/70 group-hover:via-blue-500/30 transition-all duration-500" />

          <!-- Card body -->
          <div class="relative h-full rounded-[15px] bg-white/[0.04] backdrop-blur-sm border border-white/5 p-7 flex flex-col items-center text-center gap-6 group-hover:bg-white/[0.07] transition-colors duration-500">

            <!-- QR code frame -->
            <div class="relative flex-shrink-0">
              <!-- Corner brackets -->
              <div class="absolute -top-2 -left-2 w-6 h-6 border-t-2 border-l-2 border-blue-400 rounded-tl-md transition-all duration-300 group-hover:border-blue-300 group-hover:-top-3 group-hover:-left-3" />
              <div class="absolute -top-2 -right-2 w-6 h-6 border-t-2 border-r-2 border-blue-400 rounded-tr-md transition-all duration-300 group-hover:border-blue-300 group-hover:-top-3 group-hover:-right-3" />
              <div class="absolute -bottom-2 -left-2 w-6 h-6 border-b-2 border-l-2 border-blue-400 rounded-bl-md transition-all duration-300 group-hover:border-blue-300 group-hover:-bottom-3 group-hover:-left-3" />
              <div class="absolute -bottom-2 -right-2 w-6 h-6 border-b-2 border-r-2 border-blue-400 rounded-br-md transition-all duration-300 group-hover:border-blue-300 group-hover:-bottom-3 group-hover:-right-3" />

              <!-- QR image -->
              <div class="relative w-44 h-44 rounded-xl overflow-hidden shadow-2xl shadow-black/40">
                <img
                  :src="branch.qr"
                  :alt="`QR ${branch.location}`"
                  class="w-full h-full object-cover"
                  loading="lazy"
                  decoding="async"
                />
                <!-- Scan line animation -->
                <div class="qr-scanline absolute inset-0 pointer-events-none" />
              </div>

              <!-- Zalo badge -->
              <div class="absolute -bottom-3 -right-3 w-9 h-9 rounded-full bg-[#0068FF] shadow-lg shadow-blue-600/40 flex items-center justify-center border-2 border-[#060c1a]">
                <img :src="zaloLogo" alt="Zalo" class="w-5 h-5 object-contain" />
              </div>
            </div>

            <!-- Info -->
            <div class="flex flex-col items-center gap-1 flex-1 w-full">
              <!-- Status + branch -->
              <div class="flex items-center gap-2 mb-0.5">
                <span class="relative flex h-2 w-2">
                  <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-emerald-400 opacity-75" />
                  <span class="relative inline-flex rounded-full h-2 w-2 bg-emerald-400" />
                </span>
                <span class="text-[10px] font-bold uppercase tracking-[0.2em] text-slate-300">{{ branch.location }}</span>
              </div>

              <p class="text-xs text-slate-500 mb-3">{{ branch.address }}</p>

              <!-- Phone -->
              <a
                :href="`tel:${branch.phone.replace(/\s/g, '')}`"
                class="text-3xl font-extrabold text-white tabular-nums tracking-tight hover:text-blue-300 transition-colors duration-200 mb-4"
              >
                {{ branch.phone }}
              </a>

              <!-- Divider -->
              <div class="w-full h-px bg-gradient-to-r from-transparent via-white/10 to-transparent mb-4" />

              <!-- Buttons -->
              <div class="flex flex-col sm:flex-row gap-2.5 w-full">
                <a
                  :href="`tel:${branch.phone.replace(/\s/g, '')}`"
                  class="flex-1 flex items-center justify-center gap-2 px-4 py-2.5 rounded-xl bg-blue-600 hover:bg-blue-500 text-white text-sm font-bold shadow-lg shadow-blue-600/30 hover:shadow-blue-500/40 transition-all duration-200 hover:-translate-y-px active:translate-y-0"
                >
                  <svg class="w-3.5 h-3.5 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" />
                  </svg>
                  Gọi Ngay
                </a>
                <div class="flex-1 flex items-center justify-center gap-2 px-4 py-2.5 rounded-xl border border-white/10 text-slate-300 text-xs font-medium bg-white/[0.03]">
                  <img :src="zaloLogo" alt="Zalo" class="w-3.5 h-3.5 object-contain opacity-80" />
                  Quét QR → Zalo
                </div>
              </div>
            </div>

          </div>
        </div>
      </div>

      <!-- Bottom tagline -->
      <div
        :class="['mt-12 text-center', isVisible ? 'animate-fade-up' : 'opacity-0']"
        style="animation-delay: 0.38s"
      >
        <p class="text-slate-600 text-xs uppercase tracking-[0.2em] font-medium">
          Hỗ trợ tư vấn &nbsp;·&nbsp; Đặt hàng nhanh &nbsp;·&nbsp; Giao hàng tận nơi
        </p>
      </div>

    </div>
  </section>
</template>

<style scoped>
/* Scan line sweep */
@keyframes scan {
  0%   { transform: translateY(-100%); opacity: 0; }
  10%  { opacity: 1; }
  90%  { opacity: 1; }
  100% { transform: translateY(200%); opacity: 0; }
}

.qr-scanline::after {
  content: '';
  position: absolute;
  left: 0;
  right: 0;
  height: 2px;
  background: linear-gradient(90deg, transparent, rgba(96,165,250,0.8), transparent);
  box-shadow: 0 0 12px 4px rgba(96,165,250,0.4);
  animation: scan 2.8s ease-in-out infinite;
  animation-delay: var(--scan-delay, 0s);
  border-radius: 2px;
}

.group:nth-child(2) .qr-scanline::after {
  --scan-delay: 1.4s;
}
</style>
