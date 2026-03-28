<script setup>
import { ref, onMounted } from 'vue'
import persona1 from '../assets/persona1.png'
import persona2 from '../assets/persona2.png'
import persona3 from '../assets/persona3.jpg'

const isVisible = ref(false)

const testimonials = [
  {
    name: 'Hương Nguyễn',
    location: 'Ka Đô, Lâm Đồng',
    avatar: persona1,
    text: 'Đối với người khó tính như tôi thì chắc có mỗi chỗ này đáp ứng được nhu cầu từ chất lượng cho đến giá thành. Đó là giờ làm kho với nhà xưởng toàn lấy hàng của Tòng Thuỷ.',
    rating: 5,
    tag: 'Kho & Nhà Xưởng',
  },
  {
    name: 'Phương Trần',
    location: 'Đức Trọng, Lâm Đồng',
    avatar: persona2,
    text: 'Nhà mình ở Đức Trọng, vùng này mưa nắng thất thường nên chọn tôn PU mua ở đây là chuẩn bài. Chống ồn khi trời mưa rất tốt, không bị ù tai như tôn thường.',
    rating: 5,
    tag: 'Tôn PU Cách Nhiệt',
  },
  {
    name: 'Trung Tín',
    location: 'Đà Lạt, Lâm Đồng',
    avatar: persona3,
    text: 'Sản phẩm chất lượng! Mình thật sự rất hài lòng với cách nhân viên chăm sóc khách hàng — nhiệt tình, chu đáo và thân thiện hết mức.',
    rating: 5,
    tag: 'Khách Hàng Thân Thiết',
  },
]

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => { if (entry.isIntersecting) isVisible.value = true },
    { threshold: 0.08 }
  )
  const el = document.querySelector('#testimonials')
  if (el) observer.observe(el)
})
</script>

<template>
  <section id="testimonials" class="relative py-24 md:py-32 bg-[#0d1526] overflow-hidden">

    <!-- Ambient glows -->
    <div class="pointer-events-none absolute inset-0">
      <div class="absolute top-0 left-1/4 w-[500px] h-[500px] rounded-full bg-blue-700/10 blur-[100px]" />
      <div class="absolute bottom-0 right-1/4 w-[350px] h-[350px] rounded-full bg-blue-900/15 blur-[80px]" />
    </div>

    <div class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">

      <!-- Header -->
      <div :class="['text-center mb-16 md:mb-20', isVisible ? 'animate-fade-up' : 'opacity-0']">
        <div class="inline-flex items-center gap-3 mb-5">
          <span class="block w-8 h-0.5 bg-blue-400 rounded-full" />
          <span class="text-[11px] font-bold uppercase tracking-[0.2em] text-blue-400">Đánh Giá</span>
          <span class="block w-8 h-0.5 bg-blue-400 rounded-full" />
        </div>
        <h2 class="text-3xl sm:text-4xl md:text-5xl font-extrabold text-white leading-[1.1] mb-5">
          Khách Hàng Nói Gì<br />
          <span class="text-gradient-light">Về Chúng Tôi?</span>
        </h2>
        <p class="text-slate-200 max-w-md mx-auto text-lg font-medium leading-relaxed">
          Hơn 500 khách hàng trên khắp Lâm Đồng và Tây Nguyên tin tưởng Tòng Thuỷ.
        </p>
      </div>

      <!-- Cards -->
      <div class="grid grid-cols-1 md:grid-cols-3 gap-5">
        <div
          v-for="(t, index) in testimonials"
          :key="t.name"
          :class="[
            'group relative p-8 rounded-2xl border border-white/[0.07] bg-white/[0.035] backdrop-blur-sm hover:border-white/[0.14] hover:bg-white/[0.06] transition-all duration-350 overflow-hidden',
            isVisible ? 'animate-fade-up' : 'opacity-0',
          ]"
          :style="`animation-delay: ${index * 0.1}s`"
        >
          <!-- Giant quote decoration -->
          <div class="absolute -top-4 -right-2 text-[9rem] font-serif text-white/[0.03] leading-none select-none pointer-events-none group-hover:text-white/[0.06] transition-colors duration-300">"</div>

          <!-- Tag pill -->
          <span class="inline-flex items-center gap-1.5 px-2.5 py-1 rounded-full border border-blue-500/25 bg-blue-500/10 text-blue-300 text-[10px] font-bold tracking-wider uppercase mb-5">
            <span class="w-1 h-1 rounded-full bg-blue-400" />
            {{ t.tag }}
          </span>

          <!-- Stars -->
          <div class="flex gap-1 mb-4">
            <svg v-for="i in t.rating" :key="i" class="w-4 h-4 text-amber-400" fill="currentColor" viewBox="0 0 20 20">
              <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
            </svg>
          </div>

          <!-- Quote -->
          <blockquote class="text-slate-200 text-[14px] leading-relaxed mb-8">
            "{{ t.text }}"
          </blockquote>

          <!-- Author -->
          <div class="flex items-center gap-3 pt-5 border-t border-white/[0.07]">
            <img :src="t.avatar" :alt="t.name" class="w-10 h-10 rounded-full object-cover ring-1 ring-white/15 flex-shrink-0" />
            <div>
              <p class="font-bold text-white text-sm leading-none mb-1">{{ t.name }}</p>
              <p class="text-slate-400 text-xs">{{ t.location }}</p>
            </div>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>
