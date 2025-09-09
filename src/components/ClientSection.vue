<script setup>
import { ref, onMounted } from 'vue'
import hoaSenLogo from '../assets/hoasen.png'
import hoaphatLogo from '../assets/hoaphat.png'
import blueScopeLogo from '../assets/blueScope.png'
import tongDongALogo from '../assets/tonDongA.png'
import tonNamKimLogo from '../assets/tonNamKim.png'
import tonPominaLogo from '../assets/tonPomina.png'

const clients = [
    { name: 'BlueScope', logo: blueScopeLogo, bgColor: 'bg-gradient-to-br from-blue-50 to-blue-100 hover:from-blue-100 hover:to-blue-200' },
    { name: 'Hoa Sen', logo: hoaSenLogo, bgColor: 'bg-gradient-to-br from-green-50 to-green-100 hover:from-green-100 hover:to-green-200' },
    { name: 'Hoa phat', logo: hoaphatLogo, bgColor: 'bg-gradient-to-br from-red-50 to-red-100 hover:from-red-100 hover:to-red-200' },
    { name: 'Ton Dong A', logo: tongDongALogo, bgColor: 'bg-gradient-to-br from-purple-50 to-purple-100 hover:from-purple-100 hover:to-purple-200' },
    { name: 'Ton Nam Kim', logo: tonNamKimLogo, bgColor: 'bg-gradient-to-br from-orange-50 to-orange-100 hover:from-orange-100 hover:to-orange-200' },
    { name: 'Ton Pomina', logo: tonPominaLogo, bgColor: 'bg-gradient-to-br from-indigo-50 to-indigo-100 hover:from-indigo-100 hover:to-indigo-200' }
]

const isVisible = ref(false)

onMounted(() => {
  setTimeout(() => {
    isVisible.value = true
  }, 200)
})
</script>

<template>
    <section class="py-12 bg-gray-50 section-elegant">
        <div class="px-4 sm:px-6 lg:px-8">
            <p class="text-center text-gray-600 mb-8 text-2xl sm:text-3xl font-semibold text-gradient" 
               :class="{ 'animate-fade-up': isVisible }">
                Được các công ty hàng đầu thế giới tin tưởng
            </p>
            <div class="grid grid-cols-3 md:grid-cols-3 gap-8 max-w-4xl mx-auto" 
                 :class="{ 'animate-fade-up': isVisible }" 
                 style="animation-delay: 0.3s;">
                <div
                    v-for="(client, index) in clients"
                    :key="client.name"
                    class="hover-lift glass-effect p-8 rounded-xl bg-white shadow-sm flex items-center justify-center"
                    :style="`animation-delay: ${0.5 + index * 0.1}s`"
                >
                    <img 
                        :src="client.logo" 
                        :alt="client.name" 
                        class="w-full h-full object-fill opacity-90 hover:opacity-100 transition-all duration-300"
                    >
                </div>
            </div>
        </div>
    </section>
</template>