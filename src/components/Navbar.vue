<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

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
        { name: 'Home', href: '#home'},
        { name: 'Features', href: '#features'},
        { name: 'Solutions', href: '#solutions'},
        { name: 'Testimonials', href: '#testimonials'},
        { name: 'Contact', href: '#contact'},
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
        url: 'https://facebook.com'
    },
    {
        name: 'Instagram',
        icon: `<svg class="w-10 h-10 transition-all duration-300 ease-in-out" fill="currentColor" viewBox="0 0 24 24"><path d="M12.017 0C8.396 0 7.989.013 7.041.048 6.094.082 5.48.204 4.94.388a5.486 5.486 0 00-1.988 1.292 5.479 5.479 0 00-1.292 1.988C1.472 4.208 1.35 4.822 1.316 5.769.281 6.717.268 7.124.268 10.745c0 3.622.013 4.029.048 4.976.034.947.156 1.561.34 2.101a5.487 5.487 0 001.292 1.988 5.487 5.487 0 001.988 1.292c.54.184 1.154.306 2.101.34.947.035 1.354.048 4.976.048 3.622 0 4.029-.013 4.976-.048.947-.034 1.561-.156 2.101-.34a5.487 5.487 0 001.988-1.292 5.479 5.479 0 001.292-1.988c.184-.54.306-1.154.34-2.101.035-.947.048-1.354.048-4.976 0-3.622-.013-4.029-.048-4.976-.034-.947-.156-1.561-.34-2.101a5.487 5.487 0 00-1.292-1.988A5.487 5.487 0 0019.078.388c-.54-.184-1.154-.306-2.101-.34C16.029.013 15.622.001 12.017.001zM12.017 2.163c3.556 0 3.98.013 5.385.066.662.03 1.022.138 1.262.23.317.123.543.27.78.507.237.237.384.463.507.78.092.24.2.6.23 1.262.053 1.405.066 1.829.066 5.385 0 3.556-.013 3.98-.066 5.385-.03.662-.138 1.022-.23 1.262-.123.317-.27.543-.507.78-.237.237-.463.384-.78.507-.24.092-.6.2-1.262.23-1.405.053-1.829.066-5.385.066-3.556 0-3.98-.013-5.385-.066-.662-.03-1.022-.138-1.262-.23a2.097 2.097 0 01-.78-.507 2.097 2.097 0 01-.507-.78c-.092-.24-.2-.6-.23-1.262-.053-1.405-.066-1.829-.066-5.385 0-3.556.013-3.98.066-5.385.03-.662.138-1.022.23-1.262.123-.317.27-.543.507-.78.237-.237.463-.384.78-.507.24-.092.6-.2 1.262-.23 1.405-.053 1.829-.066 5.385-.066zm0 3.678a6.162 6.162 0 100 12.324 6.162 6.162 0 000-12.324zM12.017 16a4 4 0 110-8 4 4 0 010 8zm7.846-10.405a1.441 1.441 0 01-2.88 0 1.441 1.441 0 012.88 0z"/></svg>`,
        url: 'https://instagram.com'
    }
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
                            target="_blank"
                            rel="noopener noreferrer"
                            class="text-gray-600 hover:text-blue-600 transition-all duration-300 p-2 rounded-lg hover:bg-blue-50 hover:shadow-md transform hover:scale-125 hover:rotate-12 hover:-translate-y-2"
                            v-html="social.icon"
                            :title="social.name"
                        >
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
                            target="_blank"
                            rel="noopener noreferrer"
                            class="text-gray-600 hover:text-blue-600 transition-all duration-300 p-3 rounded-lg hover:bg-blue-50 social-pulse"
                            v-html="social.icon"
                            :title="social.name"
                        >
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
 