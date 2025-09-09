<script setup>
import { ref, onMounted } from 'vue'
import heroLogo from '../assets/hero-logo.jpg'

const isVisible = ref(false)

onMounted(() => {
  setTimeout(() => {
    isVisible.value = true
  }, 300)
})
</script>

<template>
    <section id="home" class="pt-32 pb-20 md:pt-40 md:pb-28 gradient-bg text-white relative overflow-hidden">
        <!-- Elegant floating elements -->
        <div class="absolute top-20 left-20 w-3 h-3 bg-white rounded-full opacity-20 animate-float" style="animation-delay: 0s;"></div>
        <div class="absolute top-40 right-32 w-2 h-2 bg-blue-200 rounded-full opacity-30 animate-float" style="animation-delay: 2s;"></div>
        <div class="absolute bottom-32 left-1/3 w-1 h-1 bg-purple-200 rounded-full opacity-25 animate-float" style="animation-delay: 4s;"></div>
        
        <div class="px-4 sm:px-6 lg:px-8 relative z-10">
            <div class="lg:flex lg:justify-between lg:items-center">
                <div class="mb-12 lg:mb-0 lg:w-1/2 lg:pr-8" :class="{ 'animate-fade-left': isVisible }">
                    <h1 class="text-4xl md:text-5xl font-bold leading-tight mb-6">
                        <span class="text-shadow-elegant">Lĩnh vực kinh doanh chính</span>
                        <br>
                    </h1>
                    <!-- Professional Services Grid -->
                    <div class="mb-8" :class="{ 'animate-fade-up': isVisible }" style="animation-delay: 0.3s;">
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                            <!-- Service 1 -->
                            <div class="flex items-start space-x-3 p-4 bg-white/10 rounded-lg backdrop-blur-sm border border-white/20 hover-lift">
                                <div class="bg-blue-500 p-2 rounded-lg flex-shrink-0">
                                    <svg class="w-5 h-5 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 21V5a2 2 0 00-2-2H7a2 2 0 00-2 2v16m14 0h2m-2 0h-5m-9 0H3m2 0h5M9 7h1m-1 4h1m4-4h1m-1 4h1m-5 10v-5a1 1 0 011-1h2a1 1 0 011 1v5m-4 0h4"></path>
                                    </svg>
                                </div>
                                <div>
                                    <h4 class="font-semibold text-white mb-1">Phân phối tôn cao cấp</h4>
                                    <p class="text-sm text-gray-200 opacity-90">Bluescope Zacs và các loại tôn chất lượng cao</p>
                                </div>
                            </div>

                            <!-- Service 2 -->
                            <div class="flex items-start space-x-3 p-4 bg-white/10 rounded-lg backdrop-blur-sm border border-white/20 hover-lift">
                                <div class="bg-green-500 p-2 rounded-lg flex-shrink-0">
                                    <svg class="w-5 h-5 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z"></path>
                                    </svg>
                                </div>
                                <div>
                                    <h4 class="font-semibold text-white mb-1">Vật liệu cách nhiệt</h4>
                                    <p class="text-sm text-gray-200 opacity-90">Tôn xốp PU, cách âm – cách nhiệt hiệu quả</p>
                                </div>
                            </div>

                            <!-- Service 3 -->
                            <div class="flex items-start space-x-3 p-4 bg-white/10 rounded-lg backdrop-blur-sm border border-white/20 hover-lift">
                                <div class="bg-purple-500 p-2 rounded-lg flex-shrink-0">
                                    <svg class="w-5 h-5 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19.428 15.428a2 2 0 00-1.022-.547l-2.387-.477a6 6 0 00-3.86.517l-.318.158a6 6 0 01-3.86.517L6.05 15.21a2 2 0 00-1.806.547M8 4h8l-1 1v5.172a2 2 0 00.586 1.414l5 5c1.26 1.26.367 3.414-1.415 3.414H4.828c-1.782 0-2.674-2.154-1.414-3.414l5-5A2 2 0 009 10.172V5L8 4z"></path>
                                    </svg>
                                </div>
                                <div>
                                    <h4 class="font-semibold text-white mb-1">Thi công xà gồ</h4>
                                    <p class="text-sm text-gray-200 opacity-90">Sản xuất và thi công thanh kèo mái ngói</p>
                                </div>
                            </div>

                            <!-- Service 4 -->
                            <div class="flex items-start space-x-3 p-4 bg-white/10 rounded-lg backdrop-blur-sm border border-white/20 hover-lift">
                                <div class="bg-yellow-500 p-2 rounded-lg flex-shrink-0">
                                    <svg class="w-5 h-5 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3.055 11H5a2 2 0 012 2v1a2 2 0 002 2 2 2 0 012 2v2.945M8 3.935V5.5A2.5 2.5 0 0010.5 8h.5a2 2 0 012 2 2 2 0 104 0 2 2 0 012-2h1.064M15 20.488V18a2 2 0 012-2h3.064M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path>
                                    </svg>
                                </div>
                                <div>
                                    <h4 class="font-semibold text-white mb-1">Vật tư nông nghiệp</h4>
                                    <p class="text-sm text-gray-200 opacity-90">Cung cấp vật tư nhà kính nông nghiệp</p>
                                </div>
                            </div>

                            <!-- Service 5 -->
                            <div class="flex items-start space-x-3 p-4 bg-white/10 rounded-lg backdrop-blur-sm border border-white/20 hover-lift">
                                <div class="bg-red-500 p-2 rounded-lg flex-shrink-0">
                                    <svg class="w-5 h-5 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.065-2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.608 2.296.07 2.572-1.065z"></path>
                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"></path>
                                    </svg>
                                </div>
                                <div>
                                    <h4 class="font-semibold text-white mb-1">Gia công chuyên nghiệp</h4>
                                    <p class="text-sm text-gray-200 opacity-90">Chấn diềm, máng xối theo yêu cầu</p>
                                </div>
                            </div>

                            <!-- Service 6 -->
                            <div class="flex items-start space-x-3 p-4 bg-white/10 rounded-lg backdrop-blur-sm border border-white/20 hover-lift">
                                <div class="bg-indigo-500 p-2 rounded-lg flex-shrink-0">
                                    <svg class="w-5 h-5 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 7v10c0 2.21 3.582 4 8 4s8-1.79 8-4V7M4 7c0 2.21 3.582 4 8 4s8-1.79 8-4M4 7c0-2.21 3.582-4 8-4s8 1.79 8 4m0 5c0 2.21-3.582 4-8 4s-8-1.79-8-4"></path>
                                    </svg>
                                </div>
                                <div>
                                    <h4 class="font-semibold text-white mb-1">Uốn sắt định hình</h4>
                                    <p class="text-sm text-gray-200 opacity-90">Các loại U, V, O theo thiết kế</p>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="flex flex-col sm:flex-row space-y-4 sm:space-y-0 sm:space-x-4" :class="{ 'animate-fade-up': isVisible }" style="animation-delay: 0.6s;">
                        <button class="border-2 border-white text-white px-8 py-3 rounded-full font-bold hover:bg-white hover:bg-opacity-10 transition duration-300 hover-lift glass-effect">
                            Xem Thêm
                        </button>
                    </div>
                </div>
                <div class="relative lg:w-1/2 lg:pl-8" :class="{ 'animate-fade-right': isVisible }" style="animation-delay: 0.4s;">
                    <div class="relative">
                        <img
                            v-if="heroLogo"
                            :src="heroLogo"
                            alt="Hero Image" 
                            class="rounded-xl shadow-2xl animate-float hover-lift transition-all duration-500 glass-effect"
                        >
                        <!-- Elegant info card -->
                        <div class="absolute -bottom-6 -left-6 bg-white p-6 rounded-xl shadow-lg hidden md:block card-hover glass-effect">
                            <div class="flex items-center">
                                <div class="bg-indigo-100 p-3 rounded-full mr-4">
                                    <svg class="w-6 h-6 text-indigo-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path>
                                    </svg>
                                </div>
                                <div>
                                    <p class="font-bold text-gray-900 text-gradient">Được tin dùng</p>
                                    <p class="text-gray-600 stats-elegant text-2xl">500+ khách hàng</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>