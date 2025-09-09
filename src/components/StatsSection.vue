<script setup>
import { ref, onMounted } from 'vue'

const stats = [
    { number: '500+', label: 'Happy Clients' },
    { number: '99.9%', label: 'Uptime' },
    { number: '24/7', label: 'Support' },
    { number: '10x', label: 'Faster Growth' }
]

const isVisible = ref(false)

onMounted(() => {
  setTimeout(() => {
    isVisible.value = true
  }, 500)
})
</script>

<template>
    <section class="py-16 gradient-bg text-white relative overflow-hidden section-elegant">
        <!-- Subtle decorative elements -->
        <div class="absolute top-8 right-8 w-2 h-2 bg-white rounded-full opacity-20 animate-float"></div>
        <div class="absolute bottom-8 left-8 w-1 h-1 bg-blue-200 rounded-full opacity-30 animate-float" style="animation-delay: 2s;"></div>
        
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
            <div class="grid grid-cols-1 md:grid-cols-4 gap-8 text-center">
                <div 
                    v-for="(stat, index) in stats"
                    :key="stat.label"
                    class="p-6 hover-lift glass-effect rounded-xl"
                    :class="{ 'animate-fade-up': isVisible }"
                    :style="`animation-delay: ${index * 0.15}s`"
                >
                    <div class="stats-elegant text-4xl font-bold mb-2 text-shadow-elegant">
                        {{ stat.number }}
                    </div>
                    <div class="text-lg opacity-90 text-shadow-elegant">{{ stat.label }}</div>
                </div>
            </div>
        </div>
    </section>
</template>