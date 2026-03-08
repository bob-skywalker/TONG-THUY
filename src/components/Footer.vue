<script setup>
import logoImage from '../assets/logo.png'
import zaloLogo  from '../assets/Zalo-Logo.png'

const links = {
  services: [
    { label: 'Tôn Bluescope Zacs',    href: '#products' },
    { label: 'Tôn Xốp PU Cách Nhiệt', href: '#products' },
    { label: 'Xà Gồ & Kèo Mái',      href: '#services' },
    { label: 'Vật Tư Nhà Kính',       href: '#services' },
    { label: 'Gia Công Chuyên Nghiệp', href: '#services' },
  ],
  branches: [
    { label: 'Chi Nhánh Đức Trọng', sub: 'Phú Thạnh, Hiệp Thạnh' },
    { label: 'Chi Nhánh Ka Đô',     sub: '40A Tân Lập, Xã Ka Đô' },
  ],
}

const social = [
  {
    name: 'Facebook', url: 'https://www.facebook.com/share/1NtF39Gdm4/?mibextid=wwXIfr',
    icon: `<svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24"><path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/></svg>`,
  },
  {
    name: 'Messenger', url: 'https://m.me/ton.thep.tong.thuy',
    icon: `<svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24"><path d="M12 0C5.373 0 0 4.975 0 11.111c0 3.497 1.745 6.616 4.472 8.652V24l4.086-2.242c1.09.301 2.246.464 3.442.464 6.627 0 12-4.974 12-11.111C24 4.975 18.627 0 12 0zm1.191 14.963l-3.055-3.26-5.963 3.26L10.732 8.1l3.13 3.26L19.764 8.1l-6.573 6.863z"/></svg>`,
  },
  { name: 'Zalo', url: '#qr-section', logoImage: zaloLogo },
]
</script>

<template>
  <footer class="bg-[#040912]">

    <!-- CTA Strip -->
    <div class="border-b border-white/[0.06]">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12 flex flex-col sm:flex-row items-center justify-between gap-6">
        <div>
          <p class="text-white font-extrabold text-xl sm:text-2xl leading-tight mb-1">
            Sẵn sàng bắt đầu dự án của bạn?
          </p>
          <p class="text-slate-300 text-sm">Nhận báo giá miễn phí — phản hồi trong 30 phút.</p>
        </div>
        <div class="flex flex-wrap gap-3 flex-shrink-0">
          <a href="#contact" class="btn-primary text-sm px-6 py-3 rounded-xl">Liên Hệ Ngay</a>
          <a href="tel:0947196779" class="btn-ghost text-sm px-6 py-3 rounded-xl">0947 196 779</a>
        </div>
      </div>
    </div>

    <!-- Main Footer -->
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-14">
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-10">

        <!-- Brand -->
        <div class="lg:col-span-2">
          <div class="flex items-center gap-3 mb-5">
            <img :src="logoImage" alt="Logo" class="w-12 h-12 object-contain" />
            <div>
              <p class="text-white font-extrabold text-lg leading-none tracking-wide">TÒNG THUỶ</p>
              <p class="text-slate-400 text-xs tracking-wider mt-0.5">Vật Liệu Xây Dựng</p>
            </div>
          </div>
          <p class="text-slate-300 text-sm leading-relaxed mb-7 max-w-sm">
            Chuyên phân phối tôn cao cấp Bluescope, tôn xốp PU cách nhiệt, xà gồ thép và các giải pháp vật liệu mái hoàn chỉnh cho khu vực Lâm Đồng và Tây Nguyên.
          </p>
          <div class="flex gap-2">
            <a
              v-for="s in social" :key="s.name" :href="s.url" :title="s.name" target="_blank"
              class="w-9 h-9 rounded-lg bg-white/[0.05] hover:bg-blue-600 text-slate-300 hover:text-white flex items-center justify-center transition-all duration-200"
            >
              <img v-if="s.logoImage" :src="s.logoImage" :alt="s.name" class="w-4 h-4 object-contain brightness-0 invert opacity-50" />
              <span v-else v-html="s.icon" />
            </a>
          </div>
        </div>

        <!-- Products -->
        <div>
          <p class="text-white font-bold text-xs uppercase tracking-[0.15em] mb-5">Sản Phẩm</p>
          <ul class="space-y-3">
            <li v-for="link in links.services" :key="link.label">
              <a :href="link.href" class="text-slate-300 hover:text-white text-sm transition-colors flex items-center gap-2 group">
                <span class="w-1 h-1 bg-blue-600 rounded-full group-hover:bg-blue-400 transition-colors" />
                {{ link.label }}
              </a>
            </li>
          </ul>
        </div>

        <!-- Branches -->
        <div>
          <p class="text-white font-bold text-xs uppercase tracking-[0.15em] mb-5">Chi Nhánh</p>
          <div class="space-y-5 mb-5">
            <div v-for="branch in links.branches" :key="branch.label">
              <p class="text-white text-sm font-semibold mb-0.5">{{ branch.label }}</p>
              <p class="text-slate-400 text-xs">{{ branch.sub }}</p>
            </div>
          </div>
          <p class="text-white font-bold text-xs uppercase tracking-[0.15em] mb-3">Điện Thoại</p>
          <a href="tel:0947196779" class="text-blue-400 hover:text-blue-300 text-sm block mb-1 transition-colors font-medium">0947 196 779</a>
          <a href="tel:0912630520" class="text-blue-400 hover:text-blue-300 text-sm block transition-colors font-medium">0912 630 520</a>
        </div>

      </div>
    </div>

    <!-- Bottom bar -->
    <div class="border-t border-white/[0.05]">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-5 flex flex-col sm:flex-row items-center justify-between gap-3">
        <p class="text-slate-400 text-xs">© 2025 TÒNG THUỶ. All rights reserved.</p>
        <div class="flex gap-6">
          <a href="#" class="text-slate-400 hover:text-white text-xs transition-colors">Chính Sách Bảo Mật</a>
          <a href="#" class="text-slate-400 hover:text-white text-xs transition-colors">Điều Khoản Dịch Vụ</a>
        </div>
      </div>
    </div>

  </footer>
</template>
