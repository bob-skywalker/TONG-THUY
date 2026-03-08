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
  },
  {
    name: 'Phương Trần',
    location: 'Đức Trọng, Lâm Đồng',
    avatar: persona2,
    text: 'Nhà mình ở Đức Trọng, vùng này mưa nắng thất thường nên chọn tôn PU mua ở đây là chuẩn bài. Chống ồn khi trời mưa rất tốt, không bị ù tai như tôn thường. Ai ở khu vực cao nguyên thì nên chọn loại này.',
    rating: 5,
  },
  {
    name: 'Trung Tín',
    location: 'Đà Lạt, Lâm Đồng',
    avatar: persona3,
    text: 'Sản phẩm chất lượng! Mình thật sự rất hài lòng với cách nhân viên chăm sóc khách hàng — nhiệt tình, chu đáo và thân thiện hết mức. Rất đáng để trải nghiệm!',
    rating: 5,
  },
]

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => { if (entry.isIntersecting) isVisible.value = true },
    { threshold: 0.1 }
  )
  const el = document.querySelector('#testimonials')
  if (el) observer.observe(el)
})
</script>

<template>
  <section id="testimonials" class="py-24 bg-white">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">

      <!-- Header -->
      <div :class="['text-center mb-16', isVisible ? 'animate-fade-up' : 'opacity-0']">
        <p class="section-label justify-center">Đánh Giá</p>
        <h2 class="text-3xl md:text-4xl font-extrabold text-slate-900 mb-4">
          Khách Hàng Nói Gì<br />
          <span class="text-gradient">Về Chúng Tôi?</span>
        </h2>
        <p class="text-slate-500 max-w-lg mx-auto">
          Hơn 500 khách hàng đã tin tưởng và sử dụng sản phẩm của Tòng Thuỷ trên khắp khu vực Lâm Đồng và Tây Nguyên.
        </p>
      </div>

      <!-- Cards -->
      <div class="grid grid-cols-1 md:grid-cols-3 gap-7">
        <div
          v-for="(t, index) in testimonials"
          :key="t.name"
          :class="[
            'testimonial-card bg-slate-50 border border-slate-100 rounded-2xl p-8',
            isVisible ? 'animate-fade-up' : 'opacity-0',
          ]"
          :style="`animation-delay: ${index * 0.12}s`"
        >
          <!-- Stars -->
          <div class="flex gap-1 mb-5">
            <svg v-for="i in t.rating" :key="i" class="w-5 h-5 text-amber-400" fill="currentColor" viewBox="0 0 20 20">
              <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
            </svg>
          </div>

          <!-- Quote -->
          <blockquote class="text-slate-700 leading-relaxed mb-8 relative">
            <span class="absolute -top-2 -left-1 text-5xl text-blue-100 font-serif leading-none select-none">"</span>
            <span class="relative">{{ t.text }}</span>
          </blockquote>

          <!-- Author -->
          <div class="flex items-center gap-4 pt-5 border-t border-slate-100">
            <img
              :src="t.avatar"
              :alt="t.name"
              class="w-12 h-12 rounded-full object-cover ring-2 ring-blue-100"
            />
            <div>
              <p class="font-bold text-slate-900">{{ t.name }}</p>
              <p class="text-sm text-slate-500">{{ t.location }}</p>
            </div>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>
