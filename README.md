# Space Tourism

> A modern, interactive space tourism website built with Nuxt 4 and Tailwind CSS 4

[![Live Demo](https://img.shields.io/badge/demo-live-brightgreen)](https://space-tourism-nine-lyart.vercel.app/)
[![GitHub](https://img.shields.io/badge/github-repo-blue)](https://github.com/kachi33/space-tourism)

![Space Tourism Preview](./preview.jpg)

## Overview

Space Tourism is a multi-page web application that takes users on an immersive journey through space exploration. Explore potential destinations, meet crew members, and discover the cutting-edge technology that makes space travel possible.

## Features

- **Interactive Destination Browser** - Explore detailed information about Moon, Mars, Europa, and Titan with dynamic content switching
- **Crew Profiles** - Meet the team of space pioneers including Douglas Hurley, Mark Shuttleworth, Anousheh Ansari, and Victor Glover
- **Technology Showcase** - Discover the launch vehicles, spaceports, and space capsules that power space tourism
- **Smooth Page Transitions** - Seamless navigation experience with animated page transitions
- **Fully Responsive Design** - Optimized layouts for mobile, tablet, and desktop devices
- **Custom Typography** - Beautiful typography using Bellefair and Barlow font families
- **Dynamic Backgrounds** - Page-specific immersive background imagery

## Tech Stack

- **[Nuxt 4](https://nuxt.com/)** - The Vue framework for modern web applications
- **[Vue 3](https://vuejs.org/)** - Progressive JavaScript framework with Composition API
- **[Tailwind CSS 4](https://tailwindcss.com/)** - Utility-first CSS framework
- **Server-Side Rendering (SSR)** - Built-in SSR for optimal performance and SEO
- **Vite** - Next-generation frontend tooling

## Getting Started

### Prerequisites

- Node.js 18+
- npm or yarn

### Installation

1. Clone the repository
```bash
git clone https://github.com/kachi33/space-tourism.git
cd space-tourism
```

2. Install dependencies
```bash
npm install
```

3. Start the development server
```bash
npm run dev
```

The application will be available at `http://localhost:3000`

### Build for Production

```bash
# Build the application
npm run build

# Preview the production build
npm run preview

# Generate static site
npm run generate
```

## Project Structure

```
space-tourism/
├── app/
│   ├── pages/           # Application pages (Home, Destination, Crew, Technology)
│   ├── components/      # Reusable Vue components
│   ├── layouts/         # Layout templates
│   └── app.vue          # Root application component
├── public/              # Static assets (fonts, images, backgrounds)
├── src/                 # Styles and configuration
└── nuxt.config.ts       # Nuxt configuration
```

## Design Highlights

### Responsive Breakpoints
- **Mobile**: Optimized for small screens
- **Tablet (md)**: Enhanced layouts for medium devices
- **Desktop (lg)**: Full immersive experience for large screens

### Typography
- **Bellefair** - Display font for headings and large text
- **Barlow** - Primary body text
- **Barlow Condensed** - Navigation and UI elements

### Color Scheme
- Deep space backgrounds
- Light blue accents for text (`#D0D6F9`)
- White highlights for emphasis
- Subtle gray borders and dividers

## Key Learnings

- **Reactive State Management** - Implementing dynamic content switching with Vue's `ref()` and `computed()`
- **Component Lifecycle** - Using `onMounted()` for client-side operations and proper SSR handling
- **Template Conditionals** - Leveraging `v-if`, `v-for`, and dynamic classes with `:class`
- **Mobile-First Development** - Building responsive layouts from mobile up to desktop
- **Performance Optimization** - Balancing aesthetics with performance through optimized assets and lazy loading

## Author

**Kachi Ezeah**

- Frontend Mentor: [@kachi33](https://www.frontendmentor.io/profile/kachi33)
- LinkedIn: [Kachi Ezeah](https://www.linkedin.com/in/kachi33-ezeah/)
- GitHub: [@kachi33](https://github.com/kachi33)

## Acknowledgments

This project is a solution to the [Space Tourism Website Challenge](https://www.frontendmentor.io/challenges/space-tourism-multipage-website-gRWj1URZ3) by Frontend Mentor.
