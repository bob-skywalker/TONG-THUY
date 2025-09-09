<script setup>
const footerLinks = {
    company: ['Giới Thiệu', 'Dịch Vụ', 'Sản Phẩm', 'Liên Hệ'],
    services: ['Tôn Lạnh', 'Tôn Màu', 'Tôn Cuộn', 'Gia Công'],
    support: ['Hỗ Trợ', 'Bảo Hành', 'Vận Chuyển', 'Thanh Toán'],
    contact: ['0947 196 779', '0912 630 520', 'info@tongthuy.vn', 'Đức Trọng - Lâm Đồng']
}

const socialLinks = [
    { 
        name: 'Facebook', 
        icon: `<svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/></svg>`
    },
    { 
        name: 'Instagram', 
        icon: `<svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M12.017 0C8.396 0 7.989.013 7.041.048 6.094.082 5.48.204 4.94.388a5.486 5.486 0 00-1.988 1.292 5.479 5.479 0 00-1.292 1.988C1.472 4.208 1.35 4.822 1.316 5.769.281 6.717.268 7.124.268 10.745c0 3.622.013 4.029.048 4.976.034.947.156 1.561.34 2.101a5.487 5.487 0 001.292 1.988 5.487 5.487 0 001.988 1.292c.54.184 1.154.306 2.101.34.947.035 1.354.048 4.976.048 3.622 0 4.029-.013 4.976-.048.947-.034 1.561-.156 2.101-.34a5.487 5.487 0 001.988-1.292 5.479 5.479 0 001.292-1.988c.184-.54.306-1.154.34-2.101.035-.947.048-1.354.048-4.976 0-3.622-.013-4.029-.048-4.976-.034-.947-.156-1.561-.34-2.101a5.487 5.487 0 00-1.292-1.988A5.487 5.487 0 0019.078.388c-.54-.184-1.154-.306-2.101-.34C16.029.013 15.622.001 12.017.001zM12.017 2.163c3.556 0 3.98.013 5.385.066.662.03 1.022.138 1.262.23.317.123.543.27.78.507.237.237.384.463.507.78.092.24.2.6.23 1.262.053 1.405.066 1.829.066 5.385 0 3.556-.013 3.98-.066 5.385-.03.662-.138 1.022-.23 1.262-.123.317-.27.543-.507.78-.237.237-.463.384-.78.507-.24.092-.6.2-1.262.23-1.405.053-1.829.066-5.385.066-3.556 0-3.98-.013-5.385-.066-.662-.03-1.022-.138-1.262-.23a2.097 2.097 0 01-.78-.507 2.097 2.097 0 01-.507-.78c-.092-.24-.2-.6-.23-1.262-.053-1.405-.066-1.829-.066-5.385 0-3.556.013-3.98.066-5.385.03-.662.138-1.022.23-1.262.123-.317.27-.543.507-.78.237-.237.463-.384.78-.507.24-.092.6-.2 1.262-.23 1.405-.053 1.829-.066 5.385-.066zm0 3.678a6.162 6.162 0 100 12.324 6.162 6.162 0 000-12.324zM12.017 16a4 4 0 110-8 4 4 0 010 8zm7.846-10.405a1.441 1.441 0 01-2.88 0 1.441 1.441 0 012.88 0z"/></svg>`
    },
    { 
        name: 'LinkedIn', 
        icon: `<svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>`
    }
]
</script>

<template>
    <footer class="bg-gradient-to-r from-gray-900 to-gray-800 text-white pt-16 pb-8">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <!-- Main Footer Content - Now fills all 4 columns -->
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
                
                <!-- Company Info -->
                <div class="lg:col-span-1">
                    <div class="flex items-center mb-4">
                        <span class="text-2xl mr-2">🏭</span>
                        <h3 class="text-2xl font-bold text-gradient">TÒNG THUỶ</h3>
                    </div>
                    <p class="text-gray-300 mb-6 text-sm leading-relaxed">
                        Chuyên cung cấp sản phẩm tôn chất lượng cao cho xây dựng và công nghiệp.
                    </p>
                    <div class="flex space-x-3">
                        <a 
                            v-for="social in socialLinks"
                            :key="social.name"
                            href="#" 
                            class="social-elegant text-gray-400 hover:text-white p-2 rounded-lg hover:bg-gray-700 transition duration-300"
                            v-html="social.icon"
                        >
                        </a>
                    </div>
                </div>
                
                <!-- Company Links -->
                <div>
                    <h4 class="text-lg font-semibold mb-6 text-gradient">Công ty</h4>
                    <ul class="space-y-3">
                        <li v-for="link in footerLinks.company" :key="link">
                            <a href="#" class="text-gray-300 hover:text-white transition duration-300 hover-lift">{{ link }}</a>
                        </li>
                    </ul>
                </div>

                <!-- Services -->
                <div>
                    <h4 class="text-lg font-semibold mb-6 text-gradient">Sản phẩm</h4>
                    <ul class="space-y-3">
                        <li v-for="service in footerLinks.services" :key="service">
                            <div class="text-gray-300 hover:text-white transition duration-300 hover-lift">{{ service }}</div>
                        </li>
                    </ul>
                </div>

                <!-- Contact Info -->
                <div>
                    <h4 class="text-lg font-semibold mb-6 text-gradient">Liên hệ</h4>
                    <ul class="space-y-3">
                        <li v-for="contact in footerLinks.contact" :key="contact">
                            <div class="text-gray-300 text-sm">{{ contact }}</div>
                        </li>
                    </ul>
                </div>
            </div>
            
            <!-- Bottom Bar -->
            <div class="border-t border-gray-700 mt-12 pt-8 flex flex-col md:flex-row justify-between items-center">
                <p class="text-gray-400 mb-4 md:mb-0">© 2025 TÒNG THUỶ. All rights reserved.</p>
                <div class="flex flex-wrap space-x-6 text-sm">
                    <a href="#" class="text-gray-400 hover:text-white transition duration-300">Chính sách bảo mật</a>
                    <a href="#" class="text-gray-400 hover:text-white transition duration-300">Điều khoản dịch vụ</a>
                    <a href="#" class="text-gray-400 hover:text-white transition duration-300">Cookies</a>
                </div>
            </div>
        </div>
    </footer>
</template>