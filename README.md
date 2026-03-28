# Tòng Thuỷ — Steel Roofing Materials Website

<div align="center">

**A premium single-page landing website for Tòng Thuỷ** — a steel roofing materials distributor based in Lâm Đồng, Vietnam.

[![Live Site](https://img.shields.io/badge/Live%20Site-tong--thuy.web.app-blue?style=for-the-badge&logo=firebase)](https://tong-thuy.web.app)
[![Vue 3](https://img.shields.io/badge/Vue-3.x-4FC08D?style=for-the-badge&logo=vue.js&logoColor=white)](https://vuejs.org/)
[![Vite](https://img.shields.io/badge/Vite-7.x-646CFF?style=for-the-badge&logo=vite&logoColor=white)](https://vite.dev/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-3.x-38BDF8?style=for-the-badge&logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)
[![Firebase](https://img.shields.io/badge/Firebase-Hosting-FFCA28?style=for-the-badge&logo=firebase&logoColor=black)](https://firebase.google.com/)

</div>

---

## 🌐 Live Demo

**→ [https://tong-thuy.web.app](https://tong-thuy.web.app)**

---

## 📸 Section Overview

### Hero — Fullscreen Video Background
The landing hero features a fullscreen MP4 video background with a dark diagonal overlay, the company headline, dual CTA buttons, and an animated stats bar across the bottom showing key business metrics.

### Partner Brands — Infinite Marquee
A dark navy section displaying all 6 authorised distributor brand logos (BlueScope, Hoa Sen, Hòa Phát, Tôn Đông Á, Tôn Nam Kim, Tôn Pomina) in a seamless infinite scrolling marquee with edge fade gradients. Stats (6 brands, 10+ years, 100% genuine stock) are displayed below.

### Services — Glassmorphism Card Grid
6 dark glassmorphism cards on a `slate-950` background, each with a custom solid SVG icon representing the service:

| # | Service | Icon Style |
|---|---|---|
| 01 | Tôn Cao Cấp Bluescope | Corrugated roofing sheet profile |
| 02 | Tôn Xốp PU Cách Nhiệt | Sandwich panel cross-section with layers |
| 03 | Xà Gồ & Kèo Mái | C-channel purlin cross-section |
| 04 | Vật Tư Nhà Kính | Greenhouse arch silhouette |
| 05 | Gia Công Chuyên Nghiệp | Guillotine shear fabrication blade |
| 06 | Uốn Sắt Định Hình | U-shape bent steel bar |

Each card has a coloured accent bottom bar that slides in on hover (blue, emerald, violet, amber, rose, sky). A trust strip below shows 4 key business stats with blue gradient numbers.

### Video Gallery — Tabbed Product & Project Showcase
Two tabs — **Sản Phẩm** (B-series, 11 videos) and **Công Trình** (A-series, 9 videos). Each card is hover-to-play (muted). Clicking opens a full-screen modal with audio and a quote CTA button.

### Testimonials — Customer Reviews
3 customer review cards on a dark navy background with glassmorphism borders, star ratings, large decorative quote marks, tag pills, and author avatars.

### QR Contact — Zalo Scan Cards
Two side-by-side cards for the two branches with:
- **Animated corner bracket decorators** that expand outward on hover
- **Live scan-line animation** — a glowing blue beam sweeps down each QR code (staggered 1.4s between cards)
- Ping-animated live status dot
- Branch address, phone number (large, clickable), call button + Zalo hint

### Contact — Branch Info + Inquiry Form
Left panel: two branch location cards with address, phone, hours, and quick links to Facebook and Messenger. Right panel: a white card with a 3-field inquiry form (name, phone, message) that generates a `mailto:` on submit, with a 5-second success state.

### Footer — Links + CTA Strip
Top CTA strip ("Ready to start your project?") with buttons. Main grid: brand description, social links, product link list, branch addresses, phone numbers. Bottom bar: copyright + legal links.

---

## ✨ Features

- **Fullscreen video hero** — MP4 background, dark overlay, animated stats bar
- **HTTP Range video streaming** — Custom Vite middleware handles `206 Partial Content` for seek support
- **Infinite logo marquee** — CSS animation, pauses on hover, `prefers-reduced-motion` safe
- **Tabbed video gallery** — hover-to-play, click-to-modal with audio, tab transition animation
- **Glassmorphism UI** — `bg-white/[0.03]` + `border-white/[0.07]` + `backdrop-blur` across dark sections
- **QR scan-line animation** — glowing beam sweeps down each QR code via scoped CSS `@keyframes`
- **Dark-persistent navbar** — always dark, nav text always white — no colour flip on scroll
- **Intersection observer animations** — `fadeUp/Left/Right` with staggered `animation-delay`
- **Responsive mobile menu** — full-screen `Teleport` overlay with large nav links
- **Contact form** — `mailto:` composition with Vietnamese subject/body, success state
- **Floating mobile call button** — fixed bottom-right, blue glow, `active:scale-95`
- **Barlow + Barlow Condensed** — geometric square font system for body and display headings

---

## 🎨 Design System

### Colour Palette

| Token | Hex / Class | Usage |
|---|---|---|
| Background (primary) | `#070D1F` | Dark sections (Testimonials, Services) |
| Background (deep) | `#040912` | Footer |
| Background (QR) | `#060c1a` | QR section |
| Partners bg | `slate-950` | Client/Partners section |
| Blue accent | `#2563eb` | Buttons, labels, gradient |
| Blue light | `#60a5fa` | QR scan glow, gradient text |
| Text primary | `#ffffff` | Headings, key info |
| Text secondary | `slate-300` | Body descriptions on dark bg |
| Text muted | `slate-400` | Labels, addresses |

### Typography

| Role | Font | Weights |
|---|---|---|
| Body / UI | **Barlow** | 300 · 400 · 500 · 600 · 700 · 800 |
| Headings `h1`–`h4` | **Barlow Condensed** | 600 · 700 · 800 |

Barlow Condensed gives headings a geometric, square, high-impact style. Both loaded via Google Fonts.

### Global Utility Classes (`src/style.css`)

| Class | Description |
|---|---|
| `.text-gradient` | Blue gradient text (`#1d4ed8 → #3b82f6 → #60a5fa`) |
| `.text-gradient-light` | Light blue gradient for dark backgrounds |
| `.btn-primary` | Solid blue CTA button |
| `.btn-outline` | Frosted outline button |
| `.btn-ghost` | Subtle ghost button |
| `.section-label` | 11px uppercase blue overline with left bar |
| `.hero-overlay` | Diagonal dark gradient for video overlay |
| `.animate-fade-up/left/right` | Entrance animations (0.65s spring cubic-bezier) |
| `.animate-float` | 6s gentle float loop |
| `.animate-pulse-ring` | Blue ripple ring |
| `.video-card` | Scales `<video>` on hover |
| `.glass-card` | `bg-white/6 backdrop-blur-[16px]` base |
| `.marquee-track` | Infinite left-scroll (45s) |
| `.nav-link` | Underline slide-in on hover |

---

## 🏗️ Architecture

### Page Order (`App.vue`)

```
Navbar (fixed, z-50)
├── HeroSection          (#home)       — fullscreen video + stats bar
├── ShowreelSection                    — product showcase reel
├── ClientSection        (#about)      — partner marquee + 3 stats
├── ServicesSection      (#services)   — 6 glassmorphism service cards
├── ProductsSection      (#products)   — tabbed video gallery + modal
├── TestimonialsSection                — 3 customer reviews
├── QRSection            (#qr-section) — Zalo QR cards with scanner animation
├── ContactSection       (#contact)    — branch cards + inquiry form
└── Footer                             — links, CTA strip, legal
```

### Video Serving Architecture

```
/VIDEO/         ← raw MP4 files (NOT in /public, NOT bundled)
    1.MP4       ← hero background
    A1–A10.MP4  ← "Công Trình" gallery tab
    B1–B13.MP4  ← "Sản Phẩm" gallery tab

vite.config.js → custom dev middleware:
    GET /VIDEO/*
      → reads file stats
      → parses Range header
      → responds with 206 Partial Content + correct byte range
      → enables video seeking in the browser
```

All `src` attributes use **dynamic bindings** (`:src="'/VIDEO/B1.MP4'"`) to prevent Vite from processing/bundling the videos.

### IntersectionObserver Pattern

Every section uses this exact pattern:

```js
const isVisible = ref(false)
onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => { if (entry.isIntersecting) isVisible.value = true },
    { threshold: 0.08 }
  )
  observer.observe(document.querySelector('#section-id'))
})
```

Template binds: `:class="[isVisible ? 'animate-fade-up' : 'opacity-0']"` with staggered `:style="animation-delay: ${index * 0.07}s"`.

---

## 📁 Project Structure

```
TONG-THUY/
├── public/
├── src/
│   ├── assets/
│   │   ├── logo.png                  # Navbar logo
│   │   ├── blueScope.png             # Partner brand logos
│   │   ├── hoasen.png
│   │   ├── hoaphat.png
│   │   ├── tonDongA.png
│   │   ├── tonNamKim.png
│   │   ├── tonPomina.png
│   │   ├── Zalo-Logo.png             # Zalo icon
│   │   ├── Zalo-QRCode.jpg           # Branch 1 QR (Ka Đô)
│   │   ├── tonMatPuTongThuy.jpg      # Branch 2 QR (Đức Trọng)
│   │   ├── persona1.png              # Testimonial avatar
│   │   ├── persona2.png
│   │   └── persona3.jpg
│   ├── components/
│   │   ├── Navbar.vue                # Fixed nav, scroll-aware, mobile overlay
│   │   ├── HeroSection.vue           # Video hero, CTAs, stats bar
│   │   ├── ShowreelSection.vue       # Product showcase reel
│   │   ├── ClientSection.vue         # Partner marquee, stats
│   │   ├── ServicesSection.vue       # 6-card service grid + trust strip
│   │   ├── ProductsSection.vue       # Tabbed video gallery + modal
│   │   ├── TestimonialsSection.vue   # 3 customer reviews
│   │   ├── QRSection.vue             # Zalo QR cards + scan animation
│   │   ├── ContactSection.vue        # Branch info + inquiry form
│   │   └── Footer.vue                # Links, CTA strip, legal
│   ├── App.vue                       # Root component + floating call button
│   ├── main.js
│   └── style.css                     # Tailwind + global styles + animations
├── VIDEO/                            # Raw MP4 files (not in /public)
│   ├── 1.MP4
│   ├── A1.MP4 … A10.MP4
│   └── B1.MP4 … B13.MP4
├── vite.config.js                    # Custom video range-request middleware
├── tailwind.config.js
├── firebase.json                     # Firebase Hosting config
├── .firebaserc
└── package.json
```

---

## 🚀 Getting Started

### Prerequisites

- **Node.js** 18+
- **npm** 9+

### Install & Run

```bash
# 1. Clone
git clone https://github.com/bob-skywalker/TONG-THUY.git
cd TONG-THUY

# 2. Install dependencies
npm install

# 3. Start dev server
npm run dev
# → http://localhost:5173
```

### Other Commands

```bash
npm run build    # Production build → /dist
npm run preview  # Preview production build locally
```

> ⚠️ **Video files are not bundled.** The `/VIDEO/` folder must be present at the project root during development (handled by the custom Vite middleware). For production, the web server must serve `/VIDEO/**` at the same root path.

---

## 🚢 Deployment — Firebase Hosting

```bash
# 1. Build
npm run build

# 2. Deploy
firebase deploy --only hosting
```

**Live URL:** [https://tong-thuy.web.app](https://tong-thuy.web.app)
**Project Console:** [https://console.firebase.google.com/project/tong-thuy](https://console.firebase.google.com/project/tong-thuy)

---

## 📋 Component Reference

### `Navbar.vue`
- Fixed, `z-50`, transparent over hero
- `window.scrollY > 60` triggers `isScrolled` → `bg-[#070D1F]/95 backdrop-blur-xl`
- Text always white — no colour flip on scroll
- Mobile: `Teleport to="body"` full-screen overlay, `body.overflow = hidden` while open
- Scroll listener uses `{ passive: true }`

### `ProductsSection.vue`
- `activeTab` ref switches between `productVideos` (B-series) and `projectVideos` (A-series)
- `onVideoHover(event, bool)` uses `event.currentTarget.querySelector('video')` to play/pause
- Modal opened with `selectedVideo.value = video` + `document.body.style.overflow = 'hidden'`
- Modal video uses `autoplay` + `controls` with audio

### `QRSection.vue`
- Scoped CSS `@keyframes scan` animates a `::after` pseudo-element from `translateY(-100%)` to `translateY(200%)`
- Second card scan delayed via `--scan-delay: 1.4s` CSS custom property
- Corner brackets transition from `-2px` offset to `-3px` on group hover

### `ContactSection.vue`
- `handleSubmit()` builds `mailto:q463250938@gmail.com?subject=...&body=...`
- `submitted.value = true` shows success state, `setTimeout` resets after 5000ms
- Form fields: name, phone, message (all `required`)

---

## 📞 Business Information

| | Chi Nhánh Đức Trọng | Chi Nhánh Ka Đô |
|---|---|---|
| **Address** | Phú Thạnh, Hiệp Thạnh, Đức Trọng, Lâm Đồng | 40A Tân Lập, Xã Ka Đô, Lâm Đồng |
| **Phone** | [0947 196 779](tel:0947196779) | [0912 630 520](tel:0912630520) |
| **Hours** | T2–T7: 07:00–17:00 · CN: 07:00–12:00 | T2–T7: 07:00–17:00 · CN: 07:00–12:00 |

| Channel | Link |
|---|---|
| Facebook | [fb.com/share/1NtF39Gdm4](https://www.facebook.com/share/1NtF39Gdm4/) |
| Messenger | [m.me/ton.thep.tong.thuy](https://m.me/ton.thep.tong.thuy) |
| Zalo | Scan QR codes in the [#qr-section](https://tong-thuy.web.app/#qr-section) |

---

## 🛠️ Tech Stack

| Technology | Version | Role |
|---|---|---|
| [Vue 3](https://vuejs.org/) | 3.x | UI framework — Composition API, `<script setup>` |
| [Vite](https://vite.dev/) | 7.x | Build tool + dev server + custom video middleware |
| [Tailwind CSS](https://tailwindcss.com/) | 3.x | Utility-first styling |
| [Firebase Hosting](https://firebase.google.com/) | — | CDN, HTTPS, global edge deployment |
| [Google Fonts](https://fonts.google.com/) | — | Barlow + Barlow Condensed (geometric typeface) |

No test framework. No CMS. No i18n library. All content is hardcoded in Vietnamese directly in each component.

---

## 📄 License

Private project. All rights reserved — **Công Ty TNHH Tôn Thép Tòng Thuỷ**.
