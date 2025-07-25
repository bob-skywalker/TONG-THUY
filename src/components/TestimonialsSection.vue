<script setup>
import persona1 from '../assets/persona1.png'
import persona2 from '../assets/persona2.png'
import persona3 from '../assets/persona3.jpg'

const testimonials = [
    {
        name: 'Thanh Nguyen',
        position: 'Real Customer',
        avatar: persona1,
        text: 'Đối với người khó tính như tôi thì chắc có mỗi chỗ này đáp ứng được nhu cầu từ chất lượng cho đến giá thành. Đó là giờ làm kho với nhà xưởng toàn lấy hàng của Tòng Thuỷ.',
        rating: 5
    },
    {
        name: 'Phuong Tran',
        position: 'Real Customer',
        avatar: persona2,
        text: 'Nhà mình ở Đức Trọng, vùng này mưa nắng thất thường nên chọn tôn PU mua ở đây là chuẩn bài. Chống ồn khi trời mưa rất tốt, không bị ù tai như tôn thường. Ai ở khu vực cao nguyên thì nên chọn loại này 👍',
        rating: 5
    },
    {
        name: 'Bob Tran',
        position: 'Real Customer',
        avatar: persona3,
        text: 'Dịch vụ tuyệt vời! Mình thật sự rất hài lòng với cách nhân viên chăm sóc khách hàng – nhiệt tình, chu đáo và thân thiện hết mức! Rất đáng để trải nghiệm!',
        rating: 5
    }
]
</script>

<template>
    <section id="testimonials" class="py-20 bg-white">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-16">
                <span class="text-indigo-600 font-bold">CHỨNG NHẬN</span>
                <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mt-2 mb-4">Những gì khách hàng của chúng tôi nói</h2>
                <p class="text-gray-600 max-w-2xl mx-auto">Don't just take our word for it. Here's what our clients have to say about our services.</p>
            </div>
            
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                <div 
                    v-for="testimonial in testimonials"
                    :key="testimonial.name"
                    class="bg-gray-50 p-8 rounded-xl testimonial-card"
                >
                    <div class="flex items-center mb-6">
                        <div class="flex-shrink-0">
                            <img class="h-12 w-12 rounded-full" :src="testimonial.avatar" :alt="testimonial.name">
                        </div>
                        <div class="ml-4">
                            <h4 class="text-lg font-medium text-gray-900">{{ testimonial.name }}</h4>
                            <p class="text-indigo-600">{{ testimonial.position }}</p>
                        </div>
                    </div>
                    <p class="text-gray-600 italic">"{{ testimonial.text }}"</p>
                    <div class="mt-4 flex text-yellow-400">
                        <span v-for="i in Math.floor(testimonial.rating)" :key="i" class="text-xl">⭐</span>
                        <span v-if="testimonial.rating % 1 !== 0" class="text-xl">✨</span>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>