# 🎟️ Evento: High-Performance Event Landing Page

![Status](https://img.shields.io/badge/Status-Production%20Ready-success?style=for-the-badge)
![Vue.js](https://img.shields.io/badge/vuejs-%2335495e.svg?style=for-the-badge&logo=vuedotjs&logoColor=%234FC08D)
![Vite](https://img.shields.io/badge/vite-%23646CFF.svg?style=for-the-badge&logo=vite&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/tailwindcss-%2338B2AC.svg?style=for-the-badge&logo=tailwind-css&logoColor=white)
![Motion](https://img.shields.io/badge/Motion--V-%23000000.svg?style=for-the-badge&logo=framer&logoColor=white)

A high-impact, editorial-style landing page designed for professional conferences and large-scale events. This project focuses on delivering a premium user experience through fluid typography, spring-physics animations, and a high-contrast aesthetic rooted in strict design principles.

---

## 🚀 Features

* **Dynamic Hero Experience:** A high-energy entrance featuring staggered spring animations for typography and floating abstract geometric shapes.
* **Live Event Countdown:** A real-time reactive timer built with Vue's reactivity system to create immediate attendee urgency.
* **3D Perspective UI Elements:** An innovative event info section that uses CSS 3D perspective and negative margins to create an overlapping, tactile layout.
* **Spotlight Speaker Gallery:** A flush, editorial-style grid with a "Spotlight" hover effect that dims the background to focus entirely on individual speakers.
* **Adaptive Logo Carousel:** A horizontal-scrolling partner section that utilizes native CSS snap-scrolling to handle an unlimited number of logos gracefully.
* **Intelligent Sticky Navigation:** A scroll-aware navbar that transitions from a transparent layout to a frosted-glass fixed header as the user navigates.

---

## 🛠️ Tech Stack

* **Frontend Framework:** Vue.js 3 (Composition API)
* **Styling:** Tailwind CSS v4 (CSS-first configuration)
* **Animation Engine:** `motion-v` (Vue port of Framer Motion)
* **Iconography:** Lucide Icons (`lucide-vue-next`)
* **Build Tool:** Vite

---

## 🧠 Engineering Highlights

* **Mathematical Spacing (Golden Range):** Every gap, padding, and margin utility is strictly constrained to multiples of 4 or 8 (the Golden Range), ensuring perfect mathematical rhythm throughout the layout.
* **60-30-10 Color Architecture:** Implements a strict color distribution—60% Deep Purple (`#0f0c29`), 30% Surface White/Muted Gray, and 10% Vibrant Crimson (`#F9004D`) for high-conversion CTAs.
* **Fluid Typography Systems:** Utilizing `clamp()` functions within the Tailwind v4 theme, the font sizes transition smoothly across device sizes without the need for excessive media query overrides.
* **Component-Driven Animation:** Animations are extracted into script-setup logic, utilizing high-stiffness spring physics rather than standard linear transitions for a "buttery" premium feel.

---

## 📁 Folder Structure

```text
├── public/
│   └── images/            # Static assets and background textures
├── src/
│   ├── components/        # Reusable Vue components (Hero, Counter, Speakers)
│   ├── assets/            # Global styles and Tailwind v4 directives
│   ├── App.vue            # Main application orchestrator
│   └── main.js            # Vue entry point and plugin registration
├── package.json
└── vite.config.js         # Vite configuration
```

---

## Getting Started

### 1. Clone the repository
git clone [https://github.com/K01J10W19/EventoLandingPage.git](https://github.com/K01J10W19/EventoLandingPage.git)
cd EventoLandingPage

### 2. Install dependencies
npm install

### 3. Start development server (Laboratory Mode)
npm run dev

### 4. Build for production (Factory Check)
npm run build

---

## Responsive Strategy

### Achieving a flawless look at any resolution:

* **Breakpoint Precision**: The project follows a strict five-tier breakpoint strategy 
  (390px, 768px, 1024px, 1280px, 1536px) to ensure specific optimization for 
  modern mobile devices.
* **Height-Aware Layouts**: To prevent element collision on shorter viewports 
  (like a 1024x600 screen), the Hero section utilizes asymmetrical vertical 
  padding and hard minimum heights, protecting the overlapping 3D information 
  tab.
* **Mobile-First Navigation**: On screens smaller than 1024px, the navigation links 
  transition into a frosted-glass backdrop-blur dropdown to maintain usability 
  without cluttering the UI.