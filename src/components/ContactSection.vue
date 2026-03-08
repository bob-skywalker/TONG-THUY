<script setup>
import { ref, onMounted } from 'vue'

const isVisible = ref(false)

const locations = [
  {
    label: 'Chi Nhánh 1',
    address: 'Phú Thạnh, Hiệp Thạnh',
    city: 'Đức Trọng, Lâm Đồng',
    phone: '0947 196 779',
    hours: 'T2–T7: 07:00–17:00 · CN: 07:00–12:00',
  },
  {
    label: 'Chi Nhánh 2',
    address: '40A Tân Lập, Xã Ka Đô',
    city: 'Lâm Đồng',
    phone: '0912 630 520',
    hours: 'T2–T7: 07:00–17:00 · CN: 07:00–12:00',
  },
]

const quickLinks = [
  {
    label: 'Tôn Thép Tòng Thuỷ',
    sub: 'Facebook Page',
    url: 'https://www.facebook.com/share/1NtF39Gdm4/?mibextid=wwXIfr',
    icon: `<svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/></svg>`,
    bg: 'bg-blue-600',
  },
  {
    label: 'Chat Trực Tiếp',
    sub: 'Messenger',
    url: 'https://m.me/ton.thep.tong.thuy',
    icon: `<svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M12 0C5.373 0 0 4.975 0 11.111c0 3.497 1.745 6.616 4.472 8.652V24l4.086-2.242c1.09.301 2.246.464 3.442.464 6.627 0 12-4.974 12-11.111C24 4.975 18.627 0 12 0zm1.191 14.963l-3.055-3.26-5.963 3.26L10.732 8.1l3.13 3.26L19.764 8.1l-6.573 6.863z"/></svg>`,
    bg: 'bg-purple-600',
  },
]

const form = ref({ name: '', phone: '', message: '' })
const submitted = ref(false)

const handleSubmit = () => {
  const subject = encodeURIComponent(`Yêu Cầu Báo Giá - ${form.value.name}`)
  const body = encodeURIComponent(
    `Họ tên: ${form.value.name}\nSố điện thoại: ${form.value.phone}\n\nNội dung:\n${form.value.message}`
  )
  window.location.href = `mailto:q463250938@gmail.com?subject=${subject}&body=${body}`
  submitted.value = true
  form.value = { name: '', phone: '', message: '' }
  setTimeout(() => { submitted.value = false }, 5000)
}

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => { if (entry.isIntersecting) isVisible.value = true },
    { threshold: 0.08 }
  )
  const el = document.querySelector('#contact')
  if (el) observer.observe(el)
})
</script>

<template>
  <section id="contact" class="relative bg-[#070D1F] overflow-hidden">

    <!-- Ambient glow -->
    <div class="pointer-events-none absolute inset-0">
      <div class="absolute bottom-0 right-0 w-[600px] h-[400px] bg-blue-900/15 blur-[100px] rounded-full" />
    </div>

    <div class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-24 md:py-32">
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-16 lg:gap-24 items-start">

        <!-- Left: Info -->
        <div :class="[isVisible ? 'animate-fade-left' : 'opacity-0']" style="animation-delay: 0.05s">
          <!-- Section label -->
          <div class="flex items-center gap-3 mb-6">
            <span class="block w-8 h-0.5 bg-blue-400 rounded-full" />
            <span class="text-[11px] font-bold uppercase tracking-[0.2em] text-blue-400">Liên Hệ</span>
          </div>

          <h2 class="text-3xl sm:text-4xl md:text-5xl font-extrabold text-white leading-[1.1] mb-5">
            Sẵn Sàng<br />
            <span class="text-gradient-light">Tư Vấn Ngay</span>
          </h2>
          <p class="text-slate-300 text-sm sm:text-base leading-relaxed mb-10 max-w-sm">
            Đội ngũ chuyên nghiệp của chúng tôi sẵn sàng báo giá nhanh chóng, chính xác cho mọi công trình.
          </p>

          <!-- Branch cards -->
          <div class="space-y-4 mb-8">
            <div
              v-for="loc in locations" :key="loc.label"
              class="group flex items-start gap-4 p-5 rounded-2xl border border-white/[0.07] bg-white/[0.03] hover:border-white/[0.12] hover:bg-white/[0.06] transition-all duration-300"
            >
              <div class="flex-shrink-0 w-10 h-10 bg-blue-600/20 rounded-xl flex items-center justify-center text-blue-400">
                <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" />
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" />
                </svg>
              </div>
              <div class="flex-1 min-w-0">
                <span class="text-[10px] font-bold text-blue-400 uppercase tracking-wider">{{ loc.label }}</span>
                <p class="font-semibold text-white text-sm mt-0.5">{{ loc.address }}</p>
                <p class="text-slate-400 text-xs mb-2">{{ loc.city }}</p>
                <div class="flex flex-wrap items-center gap-x-3 gap-y-1">
                  <a :href="`tel:${loc.phone.replace(/\s/g, '')}`" class="text-blue-400 hover:text-blue-300 font-bold text-sm transition-colors">{{ loc.phone }}</a>
                  <span class="text-slate-400 text-xs">{{ loc.hours }}</span>
                </div>
              </div>
            </div>
          </div>

          <!-- Social links -->
          <div class="flex flex-col sm:flex-row gap-3">
            <a v-for="link in quickLinks" :key="link.label"
              :href="link.url" target="_blank" rel="noopener noreferrer"
              class="flex items-center gap-3 p-3.5 rounded-xl border border-white/[0.07] bg-white/[0.03] hover:border-white/[0.14] hover:bg-white/[0.06] transition-all duration-200 flex-1"
            >
              <div :class="['w-8 h-8 rounded-lg flex items-center justify-center text-white flex-shrink-0', link.bg]" v-html="link.icon" />
              <div class="min-w-0">
                <p class="text-white text-xs font-bold leading-none mb-0.5">{{ link.label }}</p>
                <p class="text-slate-400 text-[10px]">{{ link.sub }}</p>
              </div>
            </a>
          </div>
        </div>

        <!-- Right: Form -->
        <div :class="[isVisible ? 'animate-fade-right' : 'opacity-0']" style="animation-delay: 0.15s">
          <div class="bg-white rounded-3xl p-8 md:p-10 shadow-2xl shadow-black/40">

            <Transition
              enter-active-class="transition duration-300 ease-out"
              enter-from-class="opacity-0 scale-95"
              enter-to-class="opacity-100 scale-100"
            >
              <div v-if="submitted" class="flex flex-col items-center py-12 text-center">
                <div class="w-16 h-16 bg-green-100 rounded-full flex items-center justify-center mb-4">
                  <svg class="w-8 h-8 text-green-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                  </svg>
                </div>
                <p class="text-xl font-bold text-slate-900 mb-2">Cảm ơn bạn!</p>
                <p class="text-slate-500 text-sm">Chúng tôi sẽ liên hệ lại trong thời gian sớm nhất.</p>
              </div>
            </Transition>

            <template v-if="!submitted">
              <div class="mb-8">
                <h3 class="text-2xl font-extrabold text-slate-900 mb-1">Gửi Yêu Cầu Báo Giá</h3>
                <p class="text-slate-500 text-sm">Phản hồi trong vòng 30 phút trong giờ làm việc.</p>
              </div>

              <form @submit.prevent="handleSubmit" class="space-y-4">
                <div>
                  <label class="block text-[12px] font-bold text-slate-600 uppercase tracking-wider mb-2">Họ và tên</label>
                  <input
                    v-model="form.name" type="text" required placeholder="Nguyễn Văn A"
                    class="w-full px-4 py-3.5 bg-slate-50 border border-slate-200 rounded-xl text-slate-900 placeholder-slate-400 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent focus:bg-white transition-all text-sm"
                  />
                </div>
                <div>
                  <label class="block text-[12px] font-bold text-slate-600 uppercase tracking-wider mb-2">Số điện thoại</label>
                  <input
                    v-model="form.phone" type="tel" required placeholder="0912 345 678"
                    class="w-full px-4 py-3.5 bg-slate-50 border border-slate-200 rounded-xl text-slate-900 placeholder-slate-400 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent focus:bg-white transition-all text-sm"
                  />
                </div>
                <div>
                  <label class="block text-[12px] font-bold text-slate-600 uppercase tracking-wider mb-2">Nội dung cần tư vấn</label>
                  <textarea
                    v-model="form.message" rows="4" required
                    placeholder="Loại tôn, diện tích, công trình..."
                    class="w-full px-4 py-3.5 bg-slate-50 border border-slate-200 rounded-xl text-slate-900 placeholder-slate-400 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent focus:bg-white transition-all resize-none text-sm"
                  />
                </div>
                <button type="submit" class="btn-primary w-full py-4 text-[15px] rounded-xl mt-2">
                  Gửi Yêu Cầu
                </button>
                <p class="text-center text-xs text-slate-400 pt-1">
                  Hoặc gọi trực tiếp:
                  <a href="tel:0947196779" class="font-bold text-blue-600 hover:underline">0947 196 779</a>
                </p>
              </form>
            </template>
          </div>
        </div>

      </div>
    </div>
  </section>
</template>
