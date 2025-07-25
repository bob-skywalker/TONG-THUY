<script setup>
const stats = [
    { number: '500+', label: 'Happy Clients' },
    { number: '99.9%', label: 'Uptime' },
    { number: '24/7', label: 'Support' },
    { number: '10x', label: 'Faster Growth' }
]
</script>

<template>
    <section class="py-16 gradient-bg text-white">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="grid grid-cols-1 md:grid-cols-4 gap-8 text-center">
                <div 
                    v-for="stat in stats"
                    :key="stat.label"
                    class="p-6"
                >
                    <div class="text-4xl font-bold mb-2">{{ stat.number }}</div>
                    <div class="text-lg opacity-90">{{ stat.label }}</div>
                </div>
            </div>
        </div>
    </section>
</template>