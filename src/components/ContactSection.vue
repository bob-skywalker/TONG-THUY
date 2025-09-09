<script setup>
import { ref, onMounted } from 'vue'

const form = ref({
    name: '',
    email: '',
    subject: '',
    message: ''
})

const isVisible = ref(false)

const locations = [
    {
        title: 'Địa chỉ 1',
        address: 'Phú Thạnh, Hiệp Thạnh',
        city: 'Đức Trọng',
        phone: '0947 196 779',
        hours: ['Thứ Hai - Thứ Bảy: 07:00 - 17:00', 'Chủ nhật: 07:00 - 12:00'],
        icon: '📍'
    },
    {
        title: 'Địa chỉ 2', 
        address: '40A Tân Lập, Xã Ka Đô',
        city: 'Tỉnh Lâm Đồng',
        phone: '0912 630 520',
        hours: ['Thứ Hai - Thứ Bảy: 07:00 - 17:00', 'Chủ nhật: 07:00 - 12:00'],
        icon: '📍'
    }
]

onMounted(() => {
  setTimeout(() => {
    isVisible.value = true
  }, 300)
})

const handleSubmit = () => {
    alert(`Thank you, ${form.value.name}! Your message has been received. We'll get back to you soon.`)
    form.value = { name: '', email: '', subject: '', message: '' }
}
</script>

<template>
    <section id="contact" class="py-20 bg-gray-50 section-elegant">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <!-- Header -->
            <div class="text-center mb-16" :class="{ 'animate-fade-up': isVisible }">
                <span class="text-indigo-600 font-bold text-gradient">LIÊN HỆ VỚI CHÚNG TÔI</span>
                <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mt-2 mb-4 text-shadow-elegant">Thông Tin Liên Hệ</h2>
                <p class="text-gray-600 max-w-2xl mx-auto">Hãy liên hệ với chúng tôi để được tư vấn và hỗ trợ tốt nhất cho doanh nghiệp của bạn.</p>
            </div>

            <!-- Two-Column Address Layout -->
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 mb-16" :class="{ 'animate-fade-up': isVisible }" style="animation-delay: 0.3s;">
                <div 
                    v-for="(location, index) in locations"
                    :key="location.title"
                    class="card-hover glass-effect bg-white p-8 rounded-xl shadow-lg border border-gray-100"
                    :style="`animation-delay: ${0.5 + index * 0.2}s`"
                >
                    <!-- Location Header -->
                    <div class="flex items-center mb-6 pb-4 border-b border-gray-100">
                        <div class="bg-gray-100 p-3 rounded-lg mr-4">
                            <span class="text-lg text-gray-700">{{ location.icon }}</span>
                        </div>
                        <div>
                            <h3 class="text-xl font-semibold text-gray-900">{{ location.title }}</h3>
                            <p class="text-sm text-gray-500">Chi nhánh</p>
                        </div>
                    </div>

                    <!-- Address Info -->
                    <div class="space-y-4">
                        <!-- Address -->
                        <div class="flex items-start">
                            <div class="bg-indigo-100 p-2 rounded-lg mr-3 mt-1">
                                <svg class="w-4 h-4 text-indigo-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"></path>
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"></path>
                                </svg>
                            </div>
                            <div>
                                <h4 class="font-semibold text-gray-900">Địa chỉ</h4>
                                <p class="text-gray-600">{{ location.address }}</p>
                                <p class="text-gray-600">{{ location.city }}</p>
                            </div>
                        </div>

                        <!-- Phone -->
                        <div class="flex items-start">
                            <div class="bg-green-100 p-2 rounded-lg mr-3 mt-1">
                                <svg class="w-4 h-4 text-green-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"></path>
                                </svg>
                            </div>
                            <div>
                                <h4 class="font-semibold text-gray-900">Số điện thoại</h4>
                                <p class="text-gray-600 font-mono">{{ location.phone }}</p>
                            </div>
                        </div>

                        <!-- Hours -->
                        <div class="flex items-start">
                            <div class="bg-orange-100 p-2 rounded-lg mr-3 mt-1">
                                <svg class="w-4 h-4 text-orange-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"></path>
                                </svg>
                            </div>
                            <div>
                                <h4 class="font-semibold text-gray-900">Giờ làm việc</h4>
                                <p v-for="hour in location.hours" :key="hour" class="text-gray-600 text-sm">{{ hour }}</p>
                            </div>
                        </div>
                    </div>

                    <!-- Contact Button -->
                    <div class="mt-6">
                        <a :href="`tel:${location.phone}`" 
                           class="btn-elegant w-full px-6 py-3 text-center rounded-lg font-semibold inline-block">
                            Gọi ngay
                        </a>
                    </div>
                </div>
            </div>


        </div>
    </section>
</template>