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
    { threshold: 0.1 }
  )
  const el = document.querySelector('#contact')
  if (el) observer.observe(el)
})
</script>

<template>
  <section id="contact" class="py-24 bg-white">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">

      <!-- Header -->
      <div :class="['text-center mb-16', isVisible ? 'animate-fade-up' : 'opacity-0']">
        <p class="section-label justify-center">Liên Hệ</p>
        <h2 class="text-3xl md:text-4xl font-extrabold text-slate-900 mb-4">
          Gặp Gỡ & <span class="text-gradient">Trao Đổi</span>
        </h2>
        <p class="text-slate-500 max-w-md mx-auto">
          Đội ngũ của chúng tôi sẵn sàng tư vấn và báo giá nhanh chóng, chính xác nhất cho công trình của bạn.
        </p>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12">

        <!-- Left: Contact info -->
        <div :class="[isVisible ? 'animate-fade-left' : 'opacity-0']" style="animation-delay: 0.1s">

          <!-- Location cards -->
          <div class="space-y-5 mb-10">
            <div
              v-for="loc in locations"
              :key="loc.label"
              class="flex items-start gap-5 p-6 bg-slate-50 rounded-2xl border border-slate-100 hover:border-blue-100 hover:shadow-sm transition-all duration-200"
            >
              <div class="flex-shrink-0 w-12 h-12 bg-blue-100 rounded-xl flex items-center justify-center text-blue-600">
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" />
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" />
                </svg>
              </div>
              <div class="flex-1">
                <span class="inline-block text-xs font-bold text-blue-600 uppercase tracking-wider mb-1">{{ loc.label }}</span>
                <p class="font-semibold text-slate-900">{{ loc.address }}</p>
                <p class="text-slate-500 text-sm mb-2">{{ loc.city }}</p>
                <div class="flex flex-wrap gap-x-4 gap-y-1 text-sm">
                  <a :href="`tel:${loc.phone.replace(/\s/g, '')}`" class="font-semibold text-blue-600 hover:text-blue-700">
                    {{ loc.phone }}
                  </a>
                  <span class="text-slate-400">{{ loc.hours }}</span>
                </div>
              </div>
            </div>
          </div>

          <!-- Quick contact -->
          <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
            <a
              href="https://www.facebook.com/share/1NtF39Gdm4/?mibextid=wwXIfr"
              target="_blank"
              class="flex items-center gap-3 p-4 bg-blue-50 rounded-xl border border-blue-100 hover:bg-blue-100 transition-colors"
            >
              <div class="w-10 h-10 bg-blue-600 rounded-lg flex items-center justify-center text-white">
                <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/></svg>
              </div>
              <div>
                <p class="text-xs text-slate-500 font-medium">Facebook</p>
                <p class="text-sm font-bold text-slate-800">Tôn Thép Tòng Thuỷ</p>
              </div>
            </a>

            <a
              href="https://m.me/ton.thep.tong.thuy"
              target="_blank"
              class="flex items-center gap-3 p-4 bg-purple-50 rounded-xl border border-purple-100 hover:bg-purple-100 transition-colors"
            >
              <div class="w-10 h-10 bg-purple-600 rounded-lg flex items-center justify-center text-white">
                <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M12 0C5.373 0 0 4.975 0 11.111c0 3.497 1.745 6.616 4.472 8.652V24l4.086-2.242c1.09.301 2.246.464 3.442.464 6.627 0 12-4.974 12-11.111C24 4.975 18.627 0 12 0zm1.191 14.963l-3.055-3.26-5.963 3.26L10.732 8.1l3.13 3.26L19.764 8.1l-6.573 6.863z"/></svg>
              </div>
              <div>
                <p class="text-xs text-slate-500 font-medium">Messenger</p>
                <p class="text-sm font-bold text-slate-800">Chat Trực Tiếp</p>
              </div>
            </a>
          </div>
        </div>

        <!-- Right: Quick form -->
        <div :class="[isVisible ? 'animate-fade-right' : 'opacity-0']" style="animation-delay: 0.2s">
          <div class="bg-slate-50 rounded-2xl border border-slate-100 p-8">
            <h3 class="text-xl font-bold text-slate-900 mb-6">Gửi Yêu Cầu Báo Giá</h3>

            <Transition
              enter-active-class="transition duration-300 ease-out"
              enter-from-class="opacity-0 scale-95"
              enter-to-class="opacity-100 scale-100"
            >
              <div v-if="submitted" class="flex flex-col items-center py-10 text-center">
                <div class="w-16 h-16 bg-green-100 rounded-full flex items-center justify-center mb-4">
                  <svg class="w-8 h-8 text-green-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                  </svg>
                </div>
                <p class="text-lg font-bold text-slate-900 mb-1">Cảm ơn bạn!</p>
                <p class="text-slate-500 text-sm">Chúng tôi sẽ liên hệ lại trong thời gian sớm nhất.</p>
              </div>
            </Transition>

            <form v-if="!submitted" @submit.prevent="handleSubmit" class="space-y-5">
              <div>
                <label class="block text-sm font-semibold text-slate-700 mb-1.5">Họ và tên</label>
                <input
                  v-model="form.name"
                  type="text"
                  required
                  placeholder="Nguyễn Văn A"
                  class="w-full px-4 py-3 bg-white border border-slate-200 rounded-xl text-slate-900 placeholder-slate-400 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent transition-shadow text-sm"
                />
              </div>

              <div>
                <label class="block text-sm font-semibold text-slate-700 mb-1.5">Số điện thoại</label>
                <input
                  v-model="form.phone"
                  type="tel"
                  required
                  placeholder="0912 345 678"
                  class="w-full px-4 py-3 bg-white border border-slate-200 rounded-xl text-slate-900 placeholder-slate-400 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent transition-shadow text-sm"
                />
              </div>

              <div>
                <label class="block text-sm font-semibold text-slate-700 mb-1.5">Nội dung cần tư vấn</label>
                <textarea
                  v-model="form.message"
                  rows="4"
                  required
                  placeholder="Vui lòng mô tả nhu cầu của bạn (loại tôn, diện tích, công trình...)"
                  class="w-full px-4 py-3 bg-white border border-slate-200 rounded-xl text-slate-900 placeholder-slate-400 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent transition-shadow resize-none text-sm"
                />
              </div>

              <button type="submit" class="btn-primary w-full py-3.5 text-base">
                Gửi Yêu Cầu
              </button>

              <p class="text-center text-xs text-slate-400">
                Hoặc gọi trực tiếp:
                <a href="tel:0947196779" class="font-semibold text-blue-600 hover:underline">0947 196 779</a>
              </p>
            </form>
          </div>
        </div>

      </div>
    </div>
  </section>
</template>
