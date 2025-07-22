<script setup>
import { ref } from 'vue'

const props = defineProps({
   brandLogo: {
    type: String,
    default: null
   },
   // Logo size control - NOW WITH EVEN BIGGER OPTIONS!
   logoSize: {
    type: String,
    default: 'gigantic' // options: 'large', 'xl', 'xxl', 'massive', 'gigantic', 'colossal', 'titan'
   },
   navItems: {
    type: Array,
    default: () => [
        { name: 'Trang Chủ', href: '#', active: true},
        { name: 'Giới Thiệu', href: '#about', active: false },
        { name: 'Sản Phẩm', href: '#services', active: false },
        { name: 'Liên Hệ', href: '#contact', active: false },
    ]
   }
});

// ABSOLUTELY MASSIVE logo sizes! 🚀
const logoSizeClasses = {
  large: 'h-16 w-16 sm:h-20 sm:w-20 md:h-24 md:w-24',
  xl: 'h-20 w-20 sm:h-24 sm:w-24 md:h-28 md:w-28',
  xxl: 'h-24 w-24 sm:h-28 sm:w-28 md:h-32 md:w-32',
  massive: 'h-28 w-28 sm:h-32 sm:w-32 md:h-36 md:w-36',
  gigantic: 'h-32 w-32 sm:h-36 sm:w-36 md:h-40 md:w-40 lg:h-44 lg:w-44',
  colossal: 'h-36 w-36 sm:h-40 sm:w-40 md:h-44 md:w-44 lg:h-48 lg:w-48',
  titan: 'h-40 w-40 sm:h-44 sm:w-44 md:h-48 md:w-48 lg:h-52 lg:w-52 xl:h-56 xl:w-56'
}

// Reactive state for mobile menu
const isMobileMenuOpen = ref(false)

// Track which nav item is currently active
const activeNavItem = ref(props.navItems.find(item => item.active)?.name || 'Home')

// Computed property to check if an item is active
const isActiveItem = (itemName) => {
    return activeNavItem.value === itemName
}

// Methods
const toggleMobileMenu = () => {
    isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const handleNavClick = (event, item) => {
    event.preventDefault()
    console.log('Navigating to:', item.name)
    
    activeNavItem.value = item.name
    isMobileMenuOpen.value = false 
}
</script>

<template>
    <nav class="bg-white shadow-lg border-b border-gray-200">
        <!-- REMOVED max-w-7xl mx-auto to go full width edge-to-edge -->
        <div class="px-4 sm:px-6 lg:px-8">
            <!-- EVEN BIGGER navbar height for GIGANTIC logos -->
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

                <!-- NAVIGATION - ABSOLUTE FAR RIGHT -->
                <div class="hidden md:flex items-center space-x-6 lg:space-x-8">
                    <a
                        v-for="item in navItems"
                        :key="item.name"
                        :href="item.href"
                        @click="handleNavClick($event, item)"
                        :class="[
                            'px-5 py-4 rounded-xl text-xl font-semibold transition-all duration-300 cursor-pointer transform hover:scale-105',
                            isActiveItem(item.name)
                            ? 'text-blue-600 bg-blue-50 shadow-lg'
                            : 'text-gray-700 hover:text-blue-600 hover:bg-gray-50 hover:shadow-md'
                        ]"
                    >
                        {{ item.name }}
                    </a>
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
</style>
 