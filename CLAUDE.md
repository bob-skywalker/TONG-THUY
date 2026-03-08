# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm run dev      # Start dev server (Vite, usually http://localhost:5173)
npm run build    # Production build
npm run preview  # Preview production build locally
```

No test framework is configured.

## Architecture

This is a **single-page Vietnamese landing website** for Tòng Thuỷ — a steel roofing materials distributor based in Lâm Đồng, Vietnam.

**Stack:** Vue 3 (Composition API, `<script setup>`) + Vite 7 + Tailwind CSS v3

### Video Serving

Raw MP4 videos live in `/VIDEO/` at the project root (not in `public/`). `vite.config.js` registers a custom dev-server middleware that:
- Intercepts requests to `/VIDEO/*`
- Handles HTTP range requests (essential for video seeking)
- Streams files directly from the filesystem

All video `src` attributes use **dynamic bindings** (`:src="'/VIDEO/B1.MP4'"`) not static (`src="..."`) — this prevents Vite from bundling videos into `dist/`. For production, the `/VIDEO/` directory must be served by the web server at the same path.

### Page Structure

`src/App.vue` composes these sections in order:

```
Navbar → HeroSection → ClientSection → ServicesSection → ProductsSection
→ TestimonialsSection → QRSection → ContactSection → Footer
```

Nav anchor IDs: `#home`, `#about`, `#services`, `#products`, `#testimonials`, `#qr-section`, `#contact`

### Key Components

**Navbar** (`Navbar.vue`) — Fixed, transparent over hero, turns white/solid after scrolling 60px. Uses scroll event listener with `passive: true`.

**HeroSection** (`HeroSection.vue`) — Fullscreen video background (`/VIDEO/1.MP4`), dark hero overlay gradient, headline + CTA buttons + stats bar at bottom.

**ProductsSection** (`ProductsSection.vue`) — Tabbed video gallery. Two tabs: "Sản Phẩm" (B-series: B1–B13) and "Công Trình" (A-series: A1–A10). Videos hover-to-play (muted). Click opens a modal with audio via `<Teleport to="body">`. Uses `onVideoHover(event, bool)` with `event.currentTarget.querySelector('video')` to play/pause.

**ServicesSection** (`ServicesSection.vue`) — 6 service cards for the company's offerings.

**QRSection** (`QRSection.vue`) — Two Zalo QR code cards (one per branch).

**ContactSection** (`ContactSection.vue`) — Two branch location cards + quick inquiry form with success state.

### Global Styles (`src/style.css`)

Custom utility classes used throughout:
- `.btn-primary` / `.btn-outline` — CTA buttons
- `.section-label` — small overline label above section headings
- `.text-gradient` / `.text-gradient-light` — blue gradient text
- `.hero-overlay` — diagonal dark gradient for the hero video overlay
- `.animate-fade-up`, `.animate-fade-left`, `.animate-fade-right` — entrance animations triggered by `isVisible` ref (set via IntersectionObserver)
- `.hover-lift`, `.card-hover` — translate-Y hover effect
- `.video-card` — wrapper class that scales the inner `<video>` on hover

Font: Poppins (Google Fonts, weights 300–800).

### Content

All content is hardcoded in Vietnamese directly in each component — no CMS or i18n. Business details:
- Two branches: Đức Trọng (`0947 196 779`) and Ka Đô/Đơn Dương (`0912 630 520`)
- Facebook: `https://www.facebook.com/share/1NtF39Gdm4/`
- Messenger: `https://m.me/ton.thep.tong.thuy`
- Zalo: via QR codes in `src/assets/Zalo-QRCode.jpg` and `src/assets/tonMatPuTongThuy.jpg`

### Assets (`src/assets/`)

- `logo.png` — navbar logo; `hero-logo.jpg` — no longer used
- `Zalo-Logo.png`, `Zalo-QRCode.jpg`, `tonMatPuTongThuy.jpg` — Zalo/QR assets
- `blueScope.png`, `hoasen.png`, `hoaphat.png`, `tonDongA.png`, `tonNamKim.png`, `tonPomina.png` — partner logos (shown grayscale → color on hover in ClientSection)
- `persona1.png`, `persona2.png`, `persona3.jpg` — testimonial avatars
