<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'
import imgDanDung from '../assets/Công trình dân dụng.png'
import imgThuongMai from '../assets/Công trình thương mại.png'
import imgNhaXuong from '../assets/Nhà xưởng công nghiệp.png'

const activeTab = ref('products')
const selectedVideo = ref(null)

const congTrinhCards = [
  {
    tag: 'Dân Dụng',
    title: 'Công Trình Dân Dụng',
    desc: 'Ứng dụng vật liệu tôn,sắt, thép trong các công trình nhà ở giúp tăng độ chắc chắn, tuổi thọ lâu dài và đáp ứng linh hoạt nhiều phong cách thiết kế.',
    img: imgDanDung,
  },
  {
    tag: 'Thương Mại',
    title: 'Công Trình Thương Mại',
    desc: 'Các công trình showroom, văn phòng và khu dịch vụ được thi công với tính thẩm mỹ cao, kết hợp độ bền của vật liệu, góp phần nâng cao hình ảnh thương hiệu.',
    img: imgThuongMai,
  },
  {
    tag: 'Công Nghiệp',
    title: 'Nhà Xưởng Công Nghiệp',
    desc: 'Hệ thống nhà xưởng được thi công bằng kết cấu thép chất lượng cao, đảm bảo độ bền vững, khả năng chịu lực tốt và tối ưu chi phí cho doanh nghiệp sản xuất.',
    img: imgNhaXuong,
  },
]

const productVideos = []

const projectVideos = [
  { id: 'A1',  src: '/VIDEO/A1.MP4',  title: 'Nhà Máy Sản Xuất',    desc: 'Xưởng cán tôn hiện đại của Công Ty Tôn Thép Tòng Thuỷ',       tag: 'Nhà Máy' },
  { id: 'A2',  src: '/VIDEO/A2.MP4',  title: 'Dây Chuyền Tôn PU',   desc: 'Máy sản xuất tôn xốp PU cách nhiệt — sản lượng lớn, ổn định', tag: 'Sản Xuất' },
  { id: 'A3',  src: '/VIDEO/A3.MP4',  title: 'Máy Cán Xà Gồ',      desc: 'Dây chuyền cán xà gồ C, Z hiện đại — đặt hàng theo kích thước', tag: 'Gia Công' },
  { id: 'A6',  src: '/VIDEO/A6.MP4',  title: 'Thiết Bị Nhà Máy',    desc: 'Máy móc công nghệ cao tại Nhà Máy Tôn Tòng Thuỷ',             tag: 'Thiết Bị' },
]

const activeVideos = computed(() =>
  activeTab.value === 'products' ? productVideos : projectVideos
)

const openModal = (video) => {
  selectedVideo.value = video
  document.body.style.overflow = 'hidden'
}

const closeModal = () => {
  selectedVideo.value = null
  document.body.style.overflow = ''
}

const onVideoHover = (event, isEnter) => {
  const video = event.currentTarget.querySelector('video')
  if (!video) return
  if (isEnter) {
    video.play().catch(() => {})
  } else {
    video.pause()
    video.currentTime = 0
  }
}

const selectedCard = ref(null)
const openCard = (card) => {
  selectedCard.value = card
  document.body.style.overflow = 'hidden'
}
const closeCard = () => {
  selectedCard.value = null
  document.body.style.overflow = ''
}

const handleKeydown = (e) => {
  if (e.key === 'Escape') { closeModal(); closeCard() }
}

const isVisible = ref(false)

const onSetTab = (e) => { activeTab.value = e.detail }

onMounted(() => {
  window.addEventListener('keydown', handleKeydown)
  window.addEventListener('set-products-tab', onSetTab)
  const observer = new IntersectionObserver(
    ([entry]) => { if (entry.isIntersecting) isVisible.value = true },
    { threshold: 0.05 }
  )
  const el = document.querySelector('#products')
  if (el) observer.observe(el)
})

onUnmounted(() => {
  window.removeEventListener('keydown', handleKeydown)
  window.removeEventListener('set-products-tab', onSetTab)
  document.body.style.overflow = ''
})
</script>

<template>
  <section id="products" class="py-24 bg-slate-900">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">

      <!-- Header -->
      <div :class="['text-center mb-12', isVisible ? 'animate-fade-up' : 'opacity-0']">
        <p class="section-label justify-center" style="color: #60a5fa; --tw-text-opacity: 1;">
          <span class="w-8 h-px bg-blue-400 inline-block" />
          Danh Mục
        </p>
        <h2 class="text-3xl md:text-4xl font-extrabold text-white mb-4">
          Sản Phẩm & Công Trình
          <br />
          <span class="text-gradient-light">Tiêu Biểu</span>
        </h2>
        <p class="text-slate-200 max-w-xl mx-auto text-lg font-medium font-medium leading-relaxed">
          Khám phá danh mục sản phẩm và các công trình thực tế chúng tôi đã thực hiện trên khắp khu vực Lâm Đồng.
        </p>
      </div>

      <!-- Tabs -->
      <div :class="['flex justify-center mb-10', isVisible ? 'animate-fade-up' : 'opacity-0']" style="animation-delay: 0.1s">
        <div class="inline-flex bg-slate-800 rounded-xl p-1 gap-1">
          <button
            v-for="tab in [
              { key: 'products', label: 'Công Trình', icon: '🏗️' },
              { key: 'projects', label: 'Sản Xuất', icon: ' 📦' },
            ]"
            :key="tab.key"
            @click="activeTab = tab.key"
            :class="[
              'px-6 py-2.5 rounded-lg text-sm font-semibold transition-all duration-200',
              activeTab === tab.key
                ? 'bg-blue-600 text-white shadow-lg shadow-blue-500/20'
                : 'text-slate-200 hover:text-white',
            ]"
          >
            <span class="mr-1.5">{{ tab.icon }}</span>{{ tab.label }}
          </button>
        </div>
      </div>

      <!-- Công Trình static cards -->
      <Transition
        enter-active-class="transition duration-300 ease-out"
        enter-from-class="opacity-0 translate-y-4"
        enter-to-class="opacity-100 translate-y-0"
        leave-active-class="transition duration-150 ease-in"
        leave-from-class="opacity-100"
        leave-to-class="opacity-0"
        mode="out-in"
      >
        <div v-if="activeTab === 'products'" key="cong-trinh" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-5">
          <div
            v-for="(card, index) in congTrinhCards"
            :key="card.tag"
            class="group rounded-2xl bg-slate-900 cursor-pointer shadow-lg hover:shadow-2xl hover:shadow-blue-900/30 transition-all duration-400 hover:-translate-y-1 overflow-hidden"
            :class="isVisible ? 'animate-fade-up' : 'opacity-0'"
            :style="`animation-delay: ${index * 0.1}s`"
            @click="openCard(card)"
          >
            <!-- Image -->
            <div class="relative overflow-hidden" style="height: 340px;">
              <img :src="card.img" :alt="card.title" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500" />

              <!-- Gradient overlay -->
              <div class="absolute inset-0 bg-gradient-to-t from-slate-950 via-slate-950/30 to-transparent" />

              <!-- Tag -->
              <div class="absolute top-3 left-3">
                <span class="bg-blue-600/90 backdrop-blur-sm text-white text-xs font-semibold px-2.5 py-1 rounded-full">
                  {{ card.tag }}
                </span>
              </div>
            </div>

            <!-- Title & description below image -->
            <div class="p-5">
              <h3 class="text-white font-bold text-base mb-1">{{ card.title }}</h3>
              <p class="text-slate-300 text-base leading-relaxed font-medium">{{ card.desc }}</p>
            </div>

          </div>
        </div>

        <!-- Video Grid (Sản Xuất tab) -->
        <div v-else key="san-xuat" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-5">
          <div
            v-for="(video, index) in activeVideos"
            :key="video.id"
            class="video-card group relative rounded-2xl overflow-hidden bg-slate-900 cursor-pointer shadow-lg hover:shadow-2xl hover:shadow-blue-900/30 transition-all duration-400 hover:-translate-y-1"
            :class="isVisible ? 'animate-fade-up' : 'opacity-0'"
            :style="`animation-delay: ${index * 0.06}s`"
            @mouseenter="onVideoHover($event, true)"
            @mouseleave="onVideoHover($event, false)"
            @click="openModal(video)"
          >
            <!-- Video -->
            <div class="aspect-video overflow-hidden bg-slate-800">
              <video
                class="w-full h-full object-cover"
                muted loop playsinline preload="metadata"
                @loadedmetadata="e => { e.target.currentTime = 0.1 }"
              >
                <source :src="video.src" type="video/mp4" />
              </video>
            </div>

            <!-- Hover Overlay -->
            <div class="absolute inset-0 bg-gradient-to-t from-slate-950 via-slate-950/20 to-transparent opacity-70 group-hover:opacity-90 transition-opacity duration-300" />

            <!-- Play button -->
            <div class="absolute inset-0 flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity duration-300">
              <div class="w-14 h-14 rounded-full bg-white/15 backdrop-blur-md border border-white/30 flex items-center justify-center">
                <svg class="w-6 h-6 text-white ml-1" fill="currentColor" viewBox="0 0 24 24">
                  <path d="M8 5v14l11-7z" />
                </svg>
              </div>
            </div>

            <!-- Tag -->
            <div class="absolute top-3 left-3">
              <span class="bg-blue-600/90 backdrop-blur-sm text-white text-xs font-semibold px-2.5 py-1 rounded-full">
                {{ video.tag }}
              </span>
            </div>

            <!-- Info -->
            <div class="absolute bottom-0 left-0 right-0 p-5 translate-y-1 group-hover:translate-y-0 transition-transform duration-300">
              <h3 class="text-white font-bold text-base mb-0.5">{{ video.title }}</h3>
              <p class="text-slate-200 text-base font-medium">{{ video.desc }}</p>
            </div>
          </div>
        </div>
      </Transition>

    </div>

    <!-- Video Modal -->
    <Teleport to="body">
      <Transition
        enter-active-class="transition duration-200 ease-out"
        enter-from-class="opacity-0 scale-95"
        enter-to-class="opacity-100 scale-100"
        leave-active-class="transition duration-150 ease-in"
        leave-from-class="opacity-100 scale-100"
        leave-to-class="opacity-0 scale-95"
      >
        <div
          v-if="selectedVideo"
          class="fixed inset-0 z-50 flex items-center justify-center bg-black/95 p-4"
          @click.self="closeModal"
        >
          <div class="relative w-full max-w-5xl">
            <!-- Close button -->
            <button
              class="absolute -top-12 right-0 text-white/70 hover:text-white transition-colors p-2"
              @click="closeModal"
            >
              <svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
              </svg>
            </button>

            <!-- Video Player -->
            <video
              class="w-full rounded-2xl shadow-2xl"
              controls
              autoplay
              :src="selectedVideo.src"
            />

            <!-- Info below video -->
            <div class="mt-5 flex items-start justify-between">
              <div>
                <span class="inline-block bg-blue-600 text-white text-xs font-semibold px-3 py-1 rounded-full mb-2">
                  {{ selectedVideo.tag }}
                </span>
                <h3 class="text-white text-xl font-bold">{{ selectedVideo.title }}</h3>
                <p class="text-slate-200 mt-1">{{ selectedVideo.desc }}</p>
              </div>
              <a href="#contact" class="btn-primary text-sm flex-shrink-0 ml-6" @click="closeModal">
                Yêu Cầu Báo Giá
              </a>
            </div>
          </div>
        </div>
      </Transition>
    </Teleport>

    <!-- Image Modal -->
    <Teleport to="body">
      <Transition
        enter-active-class="transition duration-200 ease-out"
        enter-from-class="opacity-0 scale-95"
        enter-to-class="opacity-100 scale-100"
        leave-active-class="transition duration-150 ease-in"
        leave-from-class="opacity-100 scale-100"
        leave-to-class="opacity-0 scale-95"
      >
        <div
          v-if="selectedCard"
          class="fixed inset-0 z-50 flex flex-col bg-black/95 overflow-y-auto"
          @click.self="closeCard"
        >
          <!-- Close button -->
          <button
            class="sticky top-4 self-end mr-4 z-10 text-white/70 hover:text-white transition-colors p-2"
            @click="closeCard"
          >
            <svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>

          <div class="flex-1 flex flex-col items-center justify-center p-4 pb-10 w-full max-w-5xl mx-auto">
            <!-- Full image -->
            <div class="w-full rounded-2xl overflow-hidden shadow-2xl">
              <img
                :src="selectedCard.img"
                :alt="selectedCard.title"
                class="w-full h-auto object-contain"
              />
            </div>

            <!-- Info below image -->
            <div class="mt-5 w-full flex items-start justify-between gap-4">
              <div>
                <span class="inline-block bg-blue-600 text-white text-xs font-semibold px-3 py-1 rounded-full mb-2">
                  {{ selectedCard.tag }}
                </span>
                <h3 class="text-white text-xl font-bold">{{ selectedCard.title }}</h3>
                <p class="text-slate-200 mt-1">{{ selectedCard.desc }}</p>
              </div>
              <a href="#contact" class="btn-primary text-sm flex-shrink-0" @click="closeCard">
                Yêu Cầu Báo Giá
              </a>
            </div>
          </div>
        </div>
      </Transition>
    </Teleport>
  </section>
</template>
