<script setup>
const solutions = [
    {
        title: 'Enterprise Solutions',
        description: 'Scalable solutions for large organizations with complex needs.'
    },
    {
        title: 'SMB Packages',
        description: 'Affordable solutions designed for small and medium businesses.'
    },
    {
        title: 'Startup Programs',
        description: 'Special packages to help startups get off the ground quickly.'
    }
]
</script>

<template>
        <section id="solutions" class="py-20 bg-gray-100">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="lg:grid lg:grid-cols-2 lg:gap-12 items-center">
                <div class="mb-12 lg:mb-0">
                    <span class="text-indigo-600 font-bold">OUR SOLUTIONS</span>
                    <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mt-2 mb-6">Tailored Solutions for Your Business Needs</h2>
                    <p class="text-gray-600 mb-8">We understand that every business is unique. That's why we offer customized solutions designed specifically for your requirements and goals.</p>
                    
                    <div class="space-y-6">
                        <div 
                            v-for="solution in solutions"
                            :key="solution.title"
                            class="flex"
                        >
                            <div class="flex-shrink-0">
                                <div class="flex items-center justify-center h-12 w-12 rounded-md bg-indigo-600 text-white">
                                    <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 20 20">
                                        <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
                                    </svg>
                                </div>
                            </div>
                            <div class="ml-4">
                                <h4 class="text-lg font-medium text-gray-900">{{ solution.title }}</h4>
                                <p class="text-gray-600 mt-1">{{ solution.description }}</p>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="relative">
                    <img src="https://images.unsplash.com/photo-1551288049-bebda4e38f71?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80" alt="Solutions Image" class="rounded-xl shadow-xl">
                    <div class="absolute -bottom-6 -right-6 bg-indigo-600 text-white p-6 rounded-xl shadow-lg hidden md:block max-w-xs">
                        <h4 class="font-bold text-lg mb-2">Ready to transform your business?</h4>
                        <p class="text-sm opacity-90">Schedule a free consultation with our experts today.</p>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>