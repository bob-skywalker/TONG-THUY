<script setup>
import { ref } from 'vue'

const form = ref({
    name: '',
    email: '',
    subject: '',
    message: ''
})

const handleSubmit = () => {
    alert(`Thank you, ${form.value.name}! Your message has been received. We'll get back to you soon.`)
    // Reset form
    form.value = { name: '', email: '', subject: '', message: '' }
}
</script>

<template>
    <section id="contact" class="py-20 bg-white">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="lg:grid lg:grid-cols-2 lg:gap-12 items-center">
                <div class="mb-12 lg:mb-0">
                    <span class="text-indigo-600 font-bold">CONTACT US</span>
                    <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mt-2 mb-6">Get In Touch</h2>
                    <p class="text-gray-600 mb-8">Have questions or want to learn more? Our team is here to help you with any inquiries you may have.</p>
                    
                    <div class="space-y-6">
                        <div class="flex">
                            <div class="flex-shrink-0">
                                <div class="flex items-center justify-center h-12 w-12 rounded-md bg-indigo-100 text-indigo-600">
                                    <span>📍</span>
                                </div>
                            </div>
                            <div class="ml-4">
                                <h4 class="text-lg font-medium text-gray-900">Our Location</h4>
                                <p class="text-gray-600 mt-1">123 Business Ave, Suite 500<br>San Francisco, CA 94107</p>
                            </div>
                        </div>
                        
                        <div class="flex">
                            <div class="flex-shrink-0">
                                <div class="flex items-center justify-center h-12 w-12 rounded-md bg-indigo-100 text-indigo-600">
                                    <span>📞</span>
                                </div>
                            </div>
                            <div class="ml-4">
                                <h4 class="text-lg font-medium text-gray-900">Phone Number</h4>
                                <p class="text-gray-600 mt-1">+1 (555) 123-4567<br>Mon-Fri, 9am-5pm PST</p>
                            </div>
                        </div>
                        
                        <div class="flex">
                            <div class="flex-shrink-0">
                                <div class="flex items-center justify-center h-12 w-12 rounded-md bg-indigo-100 text-indigo-600">
                                    <span>✉️</span>
                                </div>
                            </div>
                            <div class="ml-4">
                                <h4 class="text-lg font-medium text-gray-900">Email Address</h4>
                                <p class="text-gray-600 mt-1">info@nexus.com<br>support@nexus.com</p>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="bg-gray-50 p-8 rounded-xl shadow-lg">
                    <h3 class="text-2xl font-bold text-gray-900 mb-6">Send Us a Message</h3>
                    <form @submit.prevent="handleSubmit">
                        <div class="mb-6">
                            <label for="name" class="block text-sm font-medium text-gray-700 mb-2">Full Name</label>
                            <input 
                                v-model="form.name"
                                type="text" 
                                id="name" 
                                class="w-full px-4 py-3 rounded-lg border border-gray-300 focus:ring-2 focus:ring-indigo-600 focus:border-transparent" 
                                placeholder="John Doe" 
                                required
                            >
                        </div>
                        <div class="mb-6">
                            <label for="email" class="block text-sm font-medium text-gray-700 mb-2">Email Address</label>
                            <input 
                                v-model="form.email"
                                type="email" 
                                id="email" 
                                class="w-full px-4 py-3 rounded-lg border border-gray-300 focus:ring-2 focus:ring-indigo-600 focus:border-transparent" 
                                placeholder="john@example.com" 
                                required
                            >
                        </div>
                        <div class="mb-6">
                            <label for="subject" class="block text-sm font-medium text-gray-700 mb-2">Subject</label>
                            <input 
                                v-model="form.subject"
                                type="text" 
                                id="subject" 
                                class="w-full px-4 py-3 rounded-lg border border-gray-300 focus:ring-2 focus:ring-indigo-600 focus:border-transparent" 
                                placeholder="How can we help?" 
                                required
                            >
                        </div>
                        <div class="mb-6">
                            <label for="message" class="block text-sm font-medium text-gray-700 mb-2">Message</label>
                            <textarea 
                                v-model="form.message"
                                id="message" 
                                rows="4" 
                                class="w-full px-4 py-3 rounded-lg border border-gray-300 focus:ring-2 focus:ring-indigo-600 focus:border-transparent" 
                                placeholder="Your message here..." 
                                required
                            ></textarea>
                        </div>
                        <button type="submit" class="gradient-bg text-white px-6 py-3 rounded-lg font-bold hover:opacity-90 transition duration-300 w-full">
                            Send Message
                        </button>
                    </form>
                </div>
            </div>
        </div>
    </section>
</template>