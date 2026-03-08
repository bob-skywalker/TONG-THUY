<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'

const activeTab = ref('projects')
const selectedVideo = ref(null)

const productVideos = [
  { id: 'B1',  src: '/VIDEO/B1.MP4',  title: 'Đội Ngũ Tòng Thuỷ',        desc: 'Đội ngũ tận tâm — phục vụ khách hàng 24/7',              tag: 'Đội Ngũ' },
  { id: 'B2',  src: '/VIDEO/B2.MP4',  title: 'Hội Thảo Tôn Zacs',        desc: 'Chương trình đào tạo kỹ thuật viên lắp đặt chuyên nghiệp', tag: 'Đào Tạo' },
  { id: 'B3',  src: '/VIDEO/B3.MP4',  title: 'Chương Trình Ưu Đãi',      desc: 'Tặng quà tri ân — hội thảo nhà thầu đẳng cấp Tôn Zacs',  tag: 'Sự Kiện' },
  { id: 'B4',  src: '/VIDEO/B4.MP4',  title: 'Gia Công Xà Gồ',           desc: 'Sản xuất xà gồ C, Z thép nguội tại xưởng theo đơn hàng', tag: 'Gia Công' },
  { id: 'B6',  src: '/VIDEO/B6.MP4',  title: 'Tôn Lợp Bluescope',        desc: 'Tấm lợp sóng vuông cao cấp — bề mặt bóng, bền màu lâu năm', tag: 'Tôn Lợp' },
  { id: 'B7',  src: '/VIDEO/B7.MP4',  title: 'Chứng Nhận Đại Lý',        desc: 'Trao chứng nhận đại lý chính hãng Bluescope Zacs uy tín', tag: 'Chứng Nhận' },
  { id: 'B9',  src: '/VIDEO/B9.MP4',  title: 'Showroom Tòng Thuỷ',       desc: 'Cửa hàng đại lý Tôn Bluescope Zacs tại Đơn Dương, Lâm Đồng', tag: 'Cửa Hàng' },
  { id: 'B10', src: '/VIDEO/B10.MP4', title: 'Roadshow Tôn Zacs',        desc: 'Sự kiện giới thiệu sản phẩm lưu động khắp khu vực Tây Nguyên', tag: 'Sự Kiện' },
  { id: 'B11', src: '/VIDEO/B11.MP4', title: 'Hội Nghị Khách Hàng',      desc: 'Hội nghị nhà thầu Tòng Thuỷ — hàng trăm đại biểu tham dự', tag: 'Hội Nghị' },
  { id: 'B12', src: '/VIDEO/B12.MP4', title: 'Xe Lưu Động Tôn Zacs',     desc: 'Trung tâm đào tạo di động — mang sản phẩm đến tận công trình', tag: 'Lưu Động' },
  { id: 'B13', src: '/VIDEO/B13.MP4', title: 'Lễ Trao Thưởng',           desc: 'Vinh danh nhà thầu xuất sắc — quà tặng chính hãng Tôn Zacs', tag: 'Trao Thưởng' },
]

const projectVideos = [
  { id: 'A1',  src: '/VIDEO/A1.MP4',  title: 'Nhà Máy Sản Xuất',    desc: 'Xưởng cán tôn hiện đại của Công Ty Tôn Thép Tòng Thuỷ',       tag: 'Nhà Máy' },
  { id: 'A2',  src: '/VIDEO/A2.MP4',  title: 'Dây Chuyền Tôn PU',   desc: 'Máy sản xuất tôn xốp PU cách nhiệt — sản lượng lớn, ổn định', tag: 'Sản Xuất' },
  { id: 'A3',  src: '/VIDEO/A3.MP4',  title: 'Máy Cán Xà Gồ',      desc: 'Dây chuyền cán xà gồ C, Z hiện đại — đặt hàng theo kích thước', tag: 'Gia Công' },
  { id: 'A4',  src: '/VIDEO/A4.MP4',  title: 'Văn Phòng Tòng Thuỷ', desc: 'Trụ sở công ty — chất lượng hàng đầu, màu sắc phong phú',     tag: 'Văn Phòng' },
  { id: 'A5',  src: '/VIDEO/A5.MP4',  title: 'Thương Hiệu Tòng Thuỷ', desc: 'Công ty TNHH Tôn Thép Tòng Thuỷ — uy tín hơn 10 năm',      tag: 'Thương Hiệu' },
  { id: 'A6',  src: '/VIDEO/A6.MP4',  title: 'Thiết Bị Nhà Máy',    desc: 'Máy móc công nghệ cao tại Nhà Máy Tôn Tòng Thuỷ',             tag: 'Thiết Bị' },
  { id: 'A7',  src: '/VIDEO/A7.MP4',  title: 'Chi Nhánh Đức Trọng', desc: 'Đại lý Tôn Bluescope Zacs tại Phú Thạnh, Hiệp Thạnh, Đức Trọng', tag: 'Chi Nhánh' },
  { id: 'A9',  src: '/VIDEO/A9.MP4',  title: 'Dây Chuyền Tự Động',  desc: 'Hệ thống máy CNC điều khiển kỹ thuật số — độ chính xác cao',  tag: 'Tự Động Hóa' },
  { id: 'A10', src: '/VIDEO/A10.MP4', title: 'Kho Nguyên Liệu',     desc: 'Kho tôn cuộn đa màu sắc — xanh, trắng, đỏ, vàng, xám sẵn hàng', tag: 'Kho Hàng' },
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

const handleKeydown = (e) => {
  if (e.key === 'Escape') closeModal()
}

const isVisible = ref(false)

onMounted(() => {
  window.addEventListener('keydown', handleKeydown)
  const observer = new IntersectionObserver(
    ([entry]) => { if (entry.isIntersecting) isVisible.value = true },
    { threshold: 0.05 }
  )
  const el = document.querySelector('#products')
  if (el) observer.observe(el)
})

onUnmounted(() => {
  window.removeEventListener('keydown', handleKeydown)
  document.body.style.overflow = ''
})
</script>

<template>
  <section id="products" class="py-24 bg-slate-950">
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
        <p class="text-slate-300 max-w-xl mx-auto">
          Khám phá danh mục sản phẩm và các công trình thực tế chúng tôi đã thực hiện trên khắp khu vực Lâm Đồng.
        </p>
      </div>

      <!-- Tabs -->
      <div :class="['flex justify-center mb-10', isVisible ? 'animate-fade-up' : 'opacity-0']" style="animation-delay: 0.1s">
        <div class="inline-flex bg-slate-800 rounded-xl p-1 gap-1">
          <button
            v-for="tab in [
              { key: 'products', label: 'Sản Phẩm', icon: '📦' },
              { key: 'projects', label: 'Công Trình', icon: '🏗️' },
            ]"
            :key="tab.key"
            @click="activeTab = tab.key"
            :class="[
              'px-6 py-2.5 rounded-lg text-sm font-semibold transition-all duration-200',
              activeTab === tab.key
                ? 'bg-blue-600 text-white shadow-lg shadow-blue-500/20'
                : 'text-slate-300 hover:text-white',
            ]"
          >
            <span class="mr-1.5">{{ tab.icon }}</span>{{ tab.label }}
          </button>
        </div>
      </div>

      <!-- Video Grid -->
      <Transition
        enter-active-class="transition duration-300 ease-out"
        enter-from-class="opacity-0 translate-y-4"
        enter-to-class="opacity-100 translate-y-0"
        leave-active-class="transition duration-150 ease-in"
        leave-from-class="opacity-100"
        leave-to-class="opacity-0"
        mode="out-in"
      >
        <div
          :key="activeTab"
          class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-5"
        >
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
              <p class="text-slate-300 text-sm">{{ video.desc }}</p>
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
                <p class="text-slate-300 mt-1">{{ selectedVideo.desc }}</p>
              </div>
              <a href="#contact" class="btn-primary text-sm flex-shrink-0 ml-6" @click="closeModal">
                Yêu Cầu Báo Giá
              </a>
            </div>
          </div>
        </div>
      </Transition>
    </Teleport>
  </section>
</template>
