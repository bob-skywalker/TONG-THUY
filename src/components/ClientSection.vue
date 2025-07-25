<script setup>
import hoaSenLogo from '../assets/hoasen.png'
import hoaphatLogo from '../assets/hoaphat.png'
import blueScopeLogo from '../assets/blueScope.png'
import tongDongALogo from '../assets/tonDongA.png'
import tonNamKimLogo from '../assets/tonNamKim.png'
import tonPominaLogo from '../assets/tonPomina.png'

const clients = [
    { name: 'BlueScope', logo: blueScopeLogo },
    { name: 'Hoa Sen', logo: hoaSenLogo },
    { name: 'Hoa phat', logo: hoaphatLogo },
    { name: 'Ton Dong A', logo: tongDongALogo },
    { name: 'Apple', logo: tonNamKimLogo },
    { name: 'IBM', logo: tonPominaLogo }
]
</script>

<template>
    <section class="py-12 bg-gray-100">
        <div class="px-4 sm:px-6 lg:px-8">
            <p class="text-center text-gray-500 mb-8 text-3xl sm:text-2xl lg:text-4xl">Được các công ty hàng đầu thế giới tin tưởng</p>
            <!-- Changed from grid to flex -->
            <div class="flex flex-wrap justify-evenly items-center gap-8">
                <img 
                    v-for="client in clients"
                    :key="client.name"
                    :src="client.logo" 
                    :alt="client.name" 
                    class="h-28 w-28 object-fill opacity-100 hover:opacity-80 transition duration-300"
                >
            </div>
        </div>
    </section>
</template>