<script setup>
import { ref, onMounted } from 'vue'
import zaloQRImage from '../assets/Zalo-QRCode.jpg'
import zaloQRImage2 from '../assets/tonMatPuTongThuy.jpg'
import zaloLogo from '../assets/Zalo-Logo.png'

const isVisible = ref(false)

onMounted(() => {
  setTimeout(() => {
    isVisible.value = true
  }, 300)
})

// Dual Location Zalo QR codes
const zaloQR = {
  title: '0912 630 520',
  location: 'Chi Nhánh Đơn Dương',
  description: 'Quét mã để chat trực tiếp qua Zalo - Chi Nhánh 1',
  qrImage: zaloQRImage,
  logoImage: zaloLogo,
  fallbackText: 'ZALO QR',
  color: 'from-blue-500 to-blue-600'
}

const zaloQR2 = {
  title: '0947 196 779',
  location: 'Chi Nhánh Đức Trọng', 
  description: 'Quét mã để chat trực tiếp qua Zalo - Chi Nhánh 2',
  qrImage: zaloQRImage2,
  logoImage: zaloLogo,
  fallbackText: "ZALO QR",
  color: 'from-purple-500 to-purple-600'
}
</script>

<template>
  <section id="qr-section" class="py-20 md:py-28 bg-gradient-to-br from-gray-50 to-white relative overflow-hidden section-elegant">
    <!-- Elegant floating elements -->
    <div class="absolute top-20 left-20 w-4 h-4 bg-blue-300 rounded-full opacity-20 animate-float" style="animation-delay: 0s;"></div>
    <div class="absolute top-40 right-32 w-3 h-3 bg-purple-300 rounded-full opacity-30 animate-float" style="animation-delay: 2s;"></div>
    <div class="absolute bottom-32 left-1/4 w-2 h-2 bg-green-300 rounded-full opacity-25 animate-float" style="animation-delay: 4s;"></div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
      <!-- Section Header -->
      <div class="text-center mb-16" :class="{ 'animate-fade-up': isVisible }">
        <div class="inline-flex items-center justify-center w-16 h-16 bg-gradient-to-r from-blue-500 to-purple-600 rounded-full mb-6">
          <svg class="w-8 h-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4.354a4 4 0 110 5.292M15 21H3v-1a6 6 0 0112 0v1zm0 0h6v-1a6 6 0 00-9-5.197m13.5-9a2.25 2.25 0 11-4.5 0 2.25 2.25 0 014.5 0z"></path>
          </svg>
        </div>
        <h2 class="text-4xl md:text-5xl font-bold mb-6">
          <span class="text-gradient text-shadow-elegant">Kết nối nhanh</span>
        </h2>
        <p class="text-xl text-gray-600 max-w-3xl mx-auto leading-relaxed">
          Quét mã QR để liên hệ trực tiếp hoặc lưu thông tin của chúng tôi
        </p>
      </div>

      <!-- Dynamic 2-QR Side by Side Layout -->
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 max-w-7xl mx-auto">
        <!-- First QR Card -->
        <div 
          class="group w-full"
          :class="{ 'animate-fade-up': isVisible }"
          style="animation-delay: 0.2s;"
        >
          <!-- QR Card -->
          <div class="card-hover glass-effect bg-white p-8 lg:p-10 rounded-3xl shadow-lg hover:shadow-2xl transition-all duration-500 text-center h-full flex flex-col justify-between">
            <!-- Zalo Logo Header -->
            <div class="inline-flex items-center justify-center w-16 h-16 lg:w-20 lg:h-20 bg-white rounded-full mb-6 group-hover:scale-110 transition-transform duration-300 shadow-lg border-2 border-blue-100 mx-auto">
              <img 
                :src="zaloQR.logoImage" 
                alt="Zalo Logo"
                class="w-10 h-10 lg:w-12 lg:h-12 object-contain"
              >
            </div>

            <!-- QR Code Display -->
            <div class="relative mb-6 flex-grow flex items-center justify-center">
              <div class="text-center">
                <!-- Dynamically Sized Zalo QR Code -->
                <img 
                  :src="zaloQR.qrImage" 
                  :alt="`${zaloQR.title} QR Code`"
                  class="mx-auto rounded-2xl shadow-lg transition-transform duration-300 hover:scale-105 w-full max-w-xs lg:max-w-sm h-auto object-contain"
                >
                <!-- QR Code Label -->
                <div class="mt-4 text-center">
                  <div class="inline-flex items-center space-x-2 bg-blue-100 px-3 py-2 rounded-full">
                    <div class="w-2 h-2 lg:w-3 lg:h-3 bg-blue-500 rounded-full animate-pulse"></div>
                    <span class="text-blue-700 font-semibold text-xs lg:text-sm">Quét để kết nối</span>
                  </div>
                </div>
              </div>
            </div>

            <!-- Content -->
            <div class="mt-auto">
              <!-- Location Badge -->
              <div class="inline-flex items-center space-x-2 bg-blue-100 px-4 py-2 rounded-full mb-4">
                <svg class="w-4 h-4 text-blue-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"></path>
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"></path>
                </svg>
                <span class="text-blue-700 font-semibold text-sm">{{ zaloQR.location }}</span>
              </div>
              <h3 class="text-2xl lg:text-3xl font-bold text-gray-900 mb-3 text-gradient">{{ zaloQR.title }}</h3>
              <p class="text-lg lg:text-xl text-gray-600 mb-6 leading-relaxed">{{ zaloQR.description }}</p>
              
              <!-- Action Button -->
              <button :class="`btn-elegant py-3 px-8 lg:py-4 lg:px-10 text-base lg:text-lg bg-gradient-to-r ${zaloQR.color} text-white font-semibold rounded-2xl hover:shadow-lg transition-all duration-300 w-full max-w-xs mx-auto`">
                Quét mã ngay
              </button>
            </div>
          </div>
        </div>

        <!-- Second QR Card -->
        <div 
          class="group w-full"
          :class="{ 'animate-fade-up': isVisible }"
          style="animation-delay: 0.4s;"
        >
          <!-- QR Card -->
          <div class="card-hover glass-effect bg-white p-8 lg:p-10 rounded-3xl shadow-lg hover:shadow-2xl transition-all duration-500 text-center h-full flex flex-col justify-between">
            <!-- Zalo Logo Header -->
            <div class="inline-flex items-center justify-center w-16 h-16 lg:w-20 lg:h-20 bg-white rounded-full mb-6 group-hover:scale-110 transition-transform duration-300 shadow-lg border-2 border-blue-100 mx-auto">
              <img 
                :src="zaloQR2.logoImage" 
                alt="Zalo Logo"
                class="w-10 h-10 lg:w-12 lg:h-12 object-contain"
              >
            </div>

            <!-- QR Code Display -->
            <div class="relative mb-6 flex-grow flex items-center justify-center">
              <div class="text-center">
                <!-- Dynamically Sized Zalo QR Code -->
                <img 
                  :src="zaloQR2.qrImage" 
                  :alt="`${zaloQR2.title} QR Code`"
                  class="mx-auto rounded-2xl shadow-lg transition-transform duration-300 hover:scale-105 w-full max-w-xs lg:max-w-sm h-auto object-contain"
                >
                <!-- QR Code Label -->
                <div class="mt-4 text-center">
                  <div class="inline-flex items-center space-x-2 bg-purple-100 px-3 py-2 rounded-full">
                    <div class="w-2 h-2 lg:w-3 lg:h-3 bg-purple-500 rounded-full animate-pulse"></div>
                    <span class="text-purple-700 font-semibold text-xs lg:text-sm">Quét để kết nối</span>
                  </div>
                </div>
              </div>
            </div>

            <!-- Content -->
            <div class="mt-auto">
              <!-- Location Badge -->
              <div class="inline-flex items-center space-x-2 bg-purple-100 px-4 py-2 rounded-full mb-4">
                <svg class="w-4 h-4 text-purple-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"></path>
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"></path>
                </svg>
                <span class="text-purple-700 font-semibold text-sm">{{ zaloQR2.location }}</span>
              </div>
              <h3 class="text-2xl lg:text-3xl font-bold text-gray-900 mb-3 text-gradient">{{ zaloQR2.title }}</h3>
              <p class="text-lg lg:text-xl text-gray-600 mb-6 leading-relaxed">{{ zaloQR2.description }}</p>
              
              <!-- Action Button -->
              <button :class="`btn-elegant py-3 px-8 lg:py-4 lg:px-10 text-base lg:text-lg bg-gradient-to-r ${zaloQR2.color} text-white font-semibold rounded-2xl hover:shadow-lg transition-all duration-300 w-full max-w-xs mx-auto`">
                Quét mã ngay
              </button>
            </div>
          </div>
        </div>
      </div>

      <!-- Instructions -->
      <div class="mt-16 text-center" :class="{ 'animate-fade-up': isVisible }" style="animation-delay: 0.6s;">
        <div class="bg-blue-50 rounded-2xl p-8 glass-effect">
          <h3 class="text-2xl font-bold text-gray-900 mb-4 text-gradient">Cách sử dụng</h3>
          <div class="grid grid-cols-1 md:grid-cols-3 gap-6 text-left">
            <div class="flex items-start space-x-4">
              <div class="bg-blue-500 text-white rounded-full w-8 h-8 flex items-center justify-center font-bold flex-shrink-0">1</div>
              <div>
                <h4 class="font-semibold text-gray-900 mb-1">Mở ứng dụng camera</h4>
                <p class="text-gray-600 text-sm">Sử dụng camera điện thoại hoặc ứng dụng quét QR</p>
              </div>
            </div>
            <div class="flex items-start space-x-4">
              <div class="bg-green-500 text-white rounded-full w-8 h-8 flex items-center justify-center font-bold flex-shrink-0">2</div>
              <div>
                <h4 class="font-semibold text-gray-900 mb-1">Quét mã QR</h4>
                <p class="text-gray-600 text-sm">Hướng camera vào mã QR và chờ tự động nhận diện</p>
              </div>
            </div>
            <div class="flex items-start space-x-4">
              <div class="bg-purple-500 text-white rounded-full w-8 h-8 flex items-center justify-center font-bold flex-shrink-0">3</div>
              <div>
                <h4 class="font-semibold text-gray-900 mb-1">Kết nối ngay</h4>
                <p class="text-gray-600 text-sm">Nhấn vào link hiển thị để kết nối trực tiếp</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* Component-specific styles if needed */
</style>
