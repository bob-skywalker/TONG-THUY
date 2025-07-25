<script setup>
// No props needed for this component yet
</script>

<template>
    <section id="home" class="pt-32 pb-20 md:pt-40 md:pb-28 gradient-bg text-white">
        <div class="px-4 sm:px-6 lg:px-8">
            <div class="lg:flex lg:justify-between lg:items-center">
                <div class="mb-12 lg:mb-0 lg:w-1/2 lg:pr-8">
                    <h1 class="text-4xl md:text-5xl font-bold leading-tight mb-6">
                        Chuyển Đổi Doanh Nghiệp Của Bạn Với
                        <br>
                        <span class="block py-4 text-yellow-300">Giải Pháp Số</span>
                    </h1>
                    <p class="text-lg opacity-90 mb-8">
                        Chúng tôi hỗ trợ các doanh nghiệp ở mọi quy mô phát triển nhanh hơn nhờ công nghệ tiên tiến và chiến lược đổi mới.
                    </p>
                    <div class="flex flex-col sm:flex-row space-y-4 sm:space-y-0 sm:space-x-4">
                        <button class="bg-white text-indigo-600 px-8 py-3 rounded-full font-bold hover:bg-gray-100 transition duration-300">
                            Bắt Đầu Ngay
                        </button>
                        <button class="border-2 border-white text-white px-8 py-3 rounded-full font-bold hover:bg-white hover:bg-opacity-10 transition duration-300">
                            Tìm Hiểu Thêm
                        </button>
                    </div>
                </div>
                <div class="relative lg:w-1/2 lg:pl-8">
                    <img src="../assets/hero-logo.jpg" alt="Hero Image" class="rounded-xl shadow-2xl animate-float">
                    <div class="absolute -bottom-6 -left-6 bg-white p-4 rounded-xl shadow-lg hidden md:block">
                        <div class="flex items-center">
                            <div class="bg-indigo-100 p-3 rounded-full mr-3">
                                <svg class="w-6 h-6 text-indigo-600" fill="currentColor" viewBox="0 0 20 20">
                                    <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
                                </svg>
                            </div>
                            <div>
                                <p class="font-bold text-gray-900">Được tin tưởng bởi</p>
                                <p class="text-gray-600">5000+ khách hàng</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>