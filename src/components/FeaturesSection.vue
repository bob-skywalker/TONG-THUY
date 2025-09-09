<script setup>
const features = [
    {
        icon: '⚡',
        title: 'Lightning Fast',
        description: 'Our platform is optimized for speed, ensuring your users get the best experience possible.'
    },
    {
        icon: '🛡️',
        title: 'Secure & Reliable',
        description: 'Enterprise-grade security to protect your data with 99.9% uptime guarantee.'
    },
    {
        icon: '📈',
        title: 'Advanced Analytics',
        description: 'Get actionable insights with our powerful analytics dashboard.'
    },
    {
        icon: '📱',
        title: 'Mobile Optimized',
        description: 'Fully responsive design that works perfectly on all devices and screen sizes.'
    }
]
</script>

<template>
    <section id="features" class="py-20 bg-white">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-16">
                <span class="text-indigo-600 font-bold">TẠI SAO CHỌN CHÚNG TÔI
                </span>
                <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mt-2 mb-4">Những Tính Năng Vượt Trội</h2>
                <p class="text-gray-600 max-w-2xl mx-auto">Chúng tôi mang đến những giải pháp sáng tạo và hiệu quả nhất, cùng với chất lượng vật liệu cao cấp, bền bỉ theo thời gian.</p>
            </div>
            
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-2 gap-8">
                <div 
                    v-for="feature in features"
                    :key="feature.title"
                    class="bg-white p-8 rounded-xl shadow-lg card-hover transition duration-300"
                >
                    <div class="bg-indigo-100 w-16 h-16 rounded-full flex items-center justify-center mb-6">
                        <span class="text-2xl">{{ feature.icon }}</span>
                    </div>
                    <h3 class="text-xl font-bold text-gray-900 mb-3">{{ feature.title }}</h3>
                    <p class="text-gray-600">{{ feature.description }}</p>
                </div>
            </div>
        </div>
    </section>
</template>