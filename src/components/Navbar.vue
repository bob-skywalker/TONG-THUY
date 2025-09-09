<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import zaloLogo from '../assets/Zalo-Logo.png'

const props = defineProps({
   brandLogo: {
    type: String,
    default: null
   },
   brandName: {
    type: String,
    default: 'TÒNG THUỶ'
   },
   logoSize: {
    type: String,
    default: 'gigantic'
   },
   navItems: {
    type: Array,
    default: () => [
        { name: 'Giới Thiệu', href: '#story'}, 
        { name: 'Sản Phẩm', href: '#products'},
        { name: 'Tin Tức', href: '#news'},
        { name: 'Liên Hệ', href: '#contact'},
    ]
   }
});

// Logo size classes (same as before)
const logoSizeClasses = {
  large: 'h-16 w-16 sm:h-20 sm:w-20 md:h-24 md:w-24',
  xl: 'h-20 w-20 sm:h-24 sm:w-24 md:h-28 md:w-28',
  xxl: 'h-24 w-24 sm:h-28 sm:w-28 md:h-32 md:w-32',
  massive: 'h-28 w-28 sm:h-32 sm:w-32 md:h-36 md:w-36',
  gigantic: 'h-32 w-32 sm:h-36 sm:w-36 md:h-40 md:w-40 lg:h-44 lg:w-44',
  colossal: 'h-36 w-36 sm:h-40 sm:w-40 md:h-44 md:w-44 lg:h-48 lg:w-48',
  titan: 'h-40 w-40 sm:h-44 sm:w-44 md:h-48 md:w-48 lg:h-52 lg:w-52 xl:h-56 xl:w-56'
}

// Social media icons (high quality SVGs)
const socialIcons = [
    {
        name: 'Facebook',
        icon: `<svg class="w-10 h-10 transition-all duration-300 ease-in-out" fill="currentColor" viewBox="0 0 24 24"><path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/></svg>`,
        url: 'https://www.facebook.com/share/1NtF39Gdm4/?mibextid=wwXIfr'
    },
    {
        name: 'Messenger',
        icon: `<svg class="w-10 h-10 transition-all duration-300 ease-in-out" fill="currentColor" viewBox="0 0 24 24"><path d="M12 0C5.373 0 0 4.975 0 11.111c0 3.497 1.745 6.616 4.472 8.652V24l4.086-2.242c1.09.301 2.246.464 3.442.464 6.627 0 12-4.974 12-11.111C24 4.975 18.627 0 12 0zm1.191 14.963l-3.055-3.26-5.963 3.26L10.732 8.1l3.13 3.26L19.764 8.1l-6.573 6.863z"/></svg>`,
        url: 'https://m.me/ton.thep.tong.thuy'
    },
    {
        name: 'Zalo',
        logoImage: zaloLogo,
        url: '#qr-section',
        isInternal: true
    },
    
]

// Reactive state for mobile menu
const isMobileMenuOpen = ref(false)

// Track current URL hash reactively
const currentHash = ref(window.location.hash)

// Update current hash when URL changes
const updateHash = () => {
    currentHash.value = window.location.hash
}

// Computed property to check if an item is active based on current URL hash
const isActiveItem = (itemName) => {
    const hashMap = {
        'Home': '',
        'Features': '#features',
        'Solutions': '#solutions', 
        'Testimonials': '#testimonials',
        'Contact': '#contact'
    }
    
    const itemHash = hashMap[itemName]
    return itemHash === currentHash.value || (itemName === 'Home' && (currentHash.value === '' || currentHash.value === '#'))
}

// Listen for hash changes
onMounted(() => {
    window.addEventListener('hashchange', updateHash)
    updateHash()
})

onUnmounted(() => {
    window.removeEventListener('hashchange', updateHash)
})

// Methods
const toggleMobileMenu = () => {
    isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const handleNavClick = (event, item) => {
    console.log('Navigating to:', item.name)
    isMobileMenuOpen.value = false 
}
</script>

<template>
    <nav class="bg-white shadow-lg border-b border-gray-200">
        <div class="px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-28 sm:h-32 md:h-36 lg:h-40 xl:h-44">
                
                <!-- GIGANTIC LOGO - ABSOLUTE FAR LEFT -->
                <div class="flex items-center">
                    <img 
                        v-if="brandLogo"
                        :src="brandLogo"
                        alt="Logo"
                        :class="[
                            'rounded-xl object-contain transition-all duration-500 hover:scale-110 drop-shadow-2xl hover:drop-shadow-3xl cursor-pointer',
                            logoSizeClasses[logoSize]
                        ]"
                    >
                </div>

                <!-- NAVIGATION + SOCIAL ICONS - ABSOLUTE FAR RIGHT -->
                <div class="hidden md:flex flex-col items-end space-y-4">
                    <!-- Navigation Items -->
                    <div class="flex items-center space-x-6 lg:space-x-8">
                        <a
                            v-for="item in navItems"
                            :key="item.name"
                            :href="item.href"
                            @click="handleNavClick($event, item)"
                            :class="[
                                'px-5 py-3 rounded-xl text-lg font-semibold transition-all duration-300 cursor-pointer transform hover:scale-105',
                                isActiveItem(item.name)
                                ? 'text-blue-600 bg-blue-50 shadow-lg'
                                : 'text-gray-700 hover:text-blue-600 hover:bg-gray-50 hover:shadow-md'
                            ]"
                        >
                            {{ item.name }}
                        </a>
                    </div>
                    
                    <!-- Social Media Icons -->
                    <div class="flex items-center space-x-4">
                        <a
                            v-for="social in socialIcons"
                            :key="social.name"
                            :href="social.url"
                            :target="social.isInternal ? '_self' : '_blank'"
                            :rel="social.isInternal ? '' : 'noopener noreferrer'"
                            class="social-elegant text-blue-600 hover:text-blue-800 p-3"
                            :title="social.name"
                        >
                            <!-- Use logo image if available, otherwise use SVG icon -->
                            <img 
                                v-if="social.logoImage" 
                                :src="social.logoImage" 
                                :alt="social.name + ' Logo'"
                                class="w-10 h-10 transition-all duration-300 ease-in-out object-contain"
                            >
                            <div v-else v-html="social.icon"></div>
                        </a>
                    </div>
                </div>

                <!-- Mobile menu button - ABSOLUTE FAR RIGHT -->
                <div class="md:hidden">
                    <button
                        @click="toggleMobileMenu"
                        class="inline-flex items-center justify-center p-4 rounded-xl text-gray-700 hover:text-blue-600 hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 transition-all duration-200"
                    >
                        <span class="sr-only">Open main menu</span>
                        <svg 
                            class="h-10 w-10" 
                            fill="none" 
                            viewBox="0 0 24 24" 
                            stroke="currentColor"
                        >
                            <path 
                                v-if="!isMobileMenuOpen"
                                stroke-linecap="round" 
                                stroke-linejoin="round" 
                                stroke-width="2" 
                                d="M4 6h16M4 12h16M4 18h16" 
                            />
                            <path 
                                v-else
                                stroke-linecap="round" 
                                stroke-linejoin="round" 
                                stroke-width="2" 
                                d="M6 18L18 6M6 6l12 12" 
                            />
                        </svg>
                    </button>
                </div>
            </div>

            <!-- Mobile Navigation Menu -->
            <div 
                v-show="isMobileMenuOpen"
                class="md:hidden py-8 border-t border-gray-200"
            >
                <div class="flex flex-col space-y-4">
                    <a
                        v-for="item in navItems"
                        :key="item.name"
                        :href="item.href"
                        @click="handleNavClick($event, item)"
                        :class="[
                            'px-6 py-4 rounded-xl text-xl font-semibold transition-all duration-200 cursor-pointer',
                            isActiveItem(item.name)
                            ? 'text-blue-600 bg-blue-50 shadow-lg'
                            : 'text-gray-700 hover:text-blue-600 hover:bg-gray-50'
                        ]"
                    >
                        {{ item.name }}
                    </a>
                    
                    <!-- Mobile Social Icons -->
                    <div class="flex justify-center space-x-6 pt-4 border-t border-gray-200 mt-4">
                        <a
                            v-for="social in socialIcons"
                            :key="social.name"
                            :href="social.url"
                            :target="social.isInternal ? '_self' : '_blank'"
                            :rel="social.isInternal ? '' : 'noopener noreferrer'"
                            class="social-elegant text-blue-600 hover:text-blue-800 p-3"
                            :title="social.name"
                        >
                            <!-- Use logo image if available, otherwise use SVG icon -->
                            <img 
                                v-if="social.logoImage" 
                                :src="social.logoImage" 
                                :alt="social.name + ' Logo'"
                                class="w-10 h-10 transition-all duration-300 ease-in-out object-contain"
                            >
                            <div v-else v-html="social.icon"></div>
                        </a>
                    </div>
                </div>
            </div>
        </div>
    </nav>
</template>

<style scoped>
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}

.social-pulse {
  animation: pulse-glow 2s ease-in-out infinite alternate;
}

@keyframes pulse-glow {
  0% { 
    transform: scale(1);
    filter: drop-shadow(0 0 5px rgba(59, 130, 246, 0.3));
  }
  100% { 
    transform: scale(1.1);
    filter: drop-shadow(0 0 15px rgba(59, 130, 246, 0.6));
  }
}
</style>
 