# 🌍 Solvara Safaris

> A luxury safari booking and discovery web platform built with **React 19**, **Vite 8**,
> **Tailwind CSS**, and **Framer Motion** — deployed on Vercel.

[![React](https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=white)](https://react.dev/)
[![Vite](https://img.shields.io/badge/Vite-8-646CFF?logo=vite&logoColor=white)](https://vitejs.dev/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3-38B2AC?logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)
[![Framer Motion](https://img.shields.io/badge/Framer_Motion-12-black?logo=framer&logoColor=white)](https://www.framer.com/motion/)
[![React Router](https://img.shields.io/badge/React_Router-7-CA4245?logo=react-router&logoColor=white)](https://reactrouter.com/)
[![Live Demo](https://img.shields.io/badge/Live%20Demo-Vercel-000000?logo=vercel&logoColor=white)](https://solvara-safaris.vercel.app/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

## 📋 Table of Contents

- [About the Project](#-about-the-project)
- [Live Demo](#-live-demo)
- [Screenshots](#-screenshots)
- [Features](#-features)
- [Tech Stack](#️-tech-stack)
- [Architecture & Design](#️-architecture--design)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Running Locally](#running-locally)
  - [Building for Production](#building-for-production)
  - [Preview Production Build](#preview-production-build)
  - [Linting](#linting)
- [Environment & Configuration](#️-environment--configuration)
- [Deployment on Vercel](#️-deployment-on-vercel)
- [Key Dependencies Explained](#-key-dependencies-explained)
- [Design Decisions](#-design-decisions)
- [Future Improvements](#-future-improvements)
- [Author](#-author)
- [License](#-license)

---

## 🦁 About the Project

**Solvara Safaris** is a premium, fully responsive front-end web application built to
showcase and promote luxury African safari experiences. It targets high-net-worth
travellers seeking curated, once-in-a-lifetime wildlife journeys.

The site is engineered for maximum visual impact — cinematic hero sections, smooth
scroll-based animations, and elegant destination cards — while keeping the codebase
clean, component-driven, and easily maintainable.

This project was developed as a personal side project to sharpen skills in:

- Modern React patterns (React 19 with concurrent features)
- Utility-first CSS design with Tailwind CSS
- Production-grade animation with Framer Motion
- Single Page Application routing and deployment

---

## 🌐 Live Demo

🔗 **[https://solvara-safaris.vercel.app](https://solvara-safaris.vercel.app)**

The application is deployed on **Vercel** and served via a global CDN with automatic
HTTPS, instant cache invalidation, and full SPA routing support.

---

## 📸 Screenshots

> Add screenshots of your pages here by uploading images to the repo and linking them below.

| Home / Hero | Safari Packages | Destination Detail |
|---|---|---|
| `![Home](./public/screenshots/home.png)` | `![Packages](./public/screenshots/packages.png)` | `![Detail](./public/screenshots/detail.png)` |

---

## ✨ Features

### User-Facing
- **Cinematic Hero Section** — Full-viewport landing with animated headline, subtext,
  and a prominent call-to-action button
- **Safari Package Listings** — Curated cards showcasing destinations, duration,
  pricing tiers, inclusions, and difficulty ratings
- **Destination Detail Pages** — Rich individual pages per safari destination with
  imagery, itinerary breakdown, highlights, and booking prompts
- **Smooth Page Transitions** — Framer Motion-powered enter/exit animations on every
  route change, providing a premium app-like feel
- **Scroll-Triggered Animations** — Elements animate into view as the user scrolls,
  using Framer Motion's `whileInView` and viewport detection
- **Fully Responsive Layout** — Mobile-first design using Tailwind CSS breakpoints;
  tested across mobile, tablet, and desktop viewports
- **Consistent Icon Language** — Lucide React icons used throughout for a unified,
  lightweight, and tree-shakeable icon system

### Technical
- **React Router DOM v7** — Client-side routing with ``,
  ``, and `` components for a seamless SPA experience
- **Vercel SPA Rewrites** — `vercel.json` configured to serve `index.html` for
  all routes, enabling direct deep-link access without 404 errors
- **Class Utility Merging** — `clsx` and `tailwind-merge` used together to safely
  compose conditional Tailwind classes without specificity conflicts
- **ESLint 9 (Flat Config)** — Modern ESLint flat config with React Hooks and
  React Refresh plugins for clean, rule-enforced code

---

## 🛠️ Tech Stack

| Category           | Technology          | Version  | Purpose                                      |
|--------------------|---------------------|----------|----------------------------------------------|
| UI Framework       | React               | 19.x     | Component tree, state, concurrent rendering  |
| Build Tool         | Vite                | 8.x      | Dev server with HMR, optimised production build |
| Styling            | Tailwind CSS        | 3.x      | Utility-first responsive styling             |
| Animation          | Framer Motion       | 12.x     | Page transitions, scroll animations          |
| Routing            | React Router DOM    | 7.x      | Client-side multi-page navigation            |
| Icons              | Lucide React        | 1.x      | Lightweight, tree-shakeable icon library     |
| Class Utilities    | clsx                | 2.x      | Conditional class composition                |
| Class Utilities    | tailwind-merge      | 3.x      | Tailwind class conflict resolution           |
| CSS Processor      | PostCSS + Autoprefixer | Latest | Cross-browser CSS compatibility              |
| Linting            | ESLint              | 9.x      | Code quality and consistency                 |
| Deployment         | Vercel              | —        | Hosting, CDN, CI/CD, HTTPS                   |
| Language           | JavaScript (JSX)    | ES2022+  | 95.5% of codebase                            |

---

## 🏗️ Architecture & Design

### Application Type
Single Page Application (SPA). React renders the entire UI client-side. Vite
produces a single optimised `dist/index.html` bundle. Vercel serves this file for
every route via `vercel.json` rewrites, and React Router handles navigation in-browser.

### Component Philosophy
- **Pages** live in `src/pages/` — one file per route, each is a standalone React
  component that composes smaller UI components
- **Shared components** live in `src/components/` — Navbar, Footer, cards, buttons,
  and other reusable building blocks
- **Assets** (images, SVGs) live in `src/assets/` or `public/` depending on whether
  they need to be processed by Vite or served as-is

### Styling Strategy
Tailwind CSS utility classes are applied directly in JSX. Complex or repeated class
combinations are extracted into component-level variables using `clsx` + `tailwind-merge`
to avoid class conflicts and maintain readability.

### Animation Strategy
Framer Motion `` wrappers are used at the page level for route transitions
and at the component level for scroll-triggered reveals. The `AnimatePresence`
component manages unmount animations during route changes.

---

## 📁 Project Structure

```
Gaurav-Solvara-Project/
│
├── public/                        # Static assets served as-is by Vite
│   ├── favicon.svg                # Browser tab icon
│   └── screenshots/               # (Recommended) Add page screenshots here
│
├── solvara-safaris/               # Additional static asset resources
│
├── src/                           # All application source code
│   ├── main.jsx                   # React app entry point — mounts  to #root
│   ├── App.jsx                    # Root component: router setup, layout shell
│   │
│   ├── components/                # Reusable UI building blocks
│   │   ├── Navbar.jsx             # Top navigation bar with links and mobile menu
│   │   ├── Footer.jsx             # Site footer with links and contact info
│   │   ├── SafariCard.jsx         # Card component for listing safari packages
│   │   ├── HeroSection.jsx        # Animated full-viewport hero banner
│   │   └── ...                    # Other shared components
│   │
│   ├── pages/                     # One component per route
│   │   ├── Home.jsx               # Landing page — hero, featured packages, CTA
│   │   ├── Destinations.jsx       # All destinations listing page
│   │   ├── DestinationDetail.jsx  # Individual destination page (dynamic route)
│   │   ├── Packages.jsx           # Full safari packages catalogue
│   │   ├── About.jsx              # About Solvara Safaris page
│   │   ├── Contact.jsx            # Contact / enquiry page
│   │   └── NotFound.jsx           # 404 fallback page
│   │
│   └── assets/                    # Images and other Vite-processed static files
│       └── images/
│
├── index.html                     # Vite SPA shell — single HTML entry point
├── package.json                   # Project metadata, scripts, dependencies
├── package-lock.json              # Exact dependency lock file
├── vite.config.js                 # Vite configuration (plugins, aliases, build)
├── tailwind.config.js             # Tailwind CSS theme and content paths config
├── postcss.config.js              # PostCSS setup (Tailwind + Autoprefixer)
├── eslint.config.js               # ESLint flat config (React Hooks + Refresh)
├── vercel.json                    # Vercel SPA routing rewrites
├── .gitignore                     # Git ignore rules (node_modules, dist, etc.)
└── README.md                      # This file
```

---

## 🚀 Getting Started

### Prerequisites

Ensure the following are installed on your local machine:

| Tool    | Minimum Version | Check Command       | Download                          |
|---------|-----------------|---------------------|-----------------------------------|
| Node.js | v18.0.0+        | `node --version`    | https://nodejs.org/               |
| npm     | v9.0.0+         | `npm --version`     | Bundled with Node.js              |
| Git     | Any             | `git --version`     | https://git-scm.com/              |

> **Tip:** Use [nvm](https://github.com/nvm-sh/nvm) to manage multiple Node.js
> versions on your machine. Run `nvm use 20` to switch to Node 20.

---

### Installation

**1. Clone the repository**

```bash
git clone https://github.com/Gtawde953/Gaurav-Solvara-Project.git
```

**2. Navigate into the project directory**

```bash
cd Gaurav-Solvara-Project
```

**3. Install all dependencies**

```bash
npm install
```

This installs both `dependencies` (React, Framer Motion, etc.) and `devDependencies`
(Vite, Tailwind, ESLint, etc.) as defined in `package.json`.

---

### Running Locally

Start the Vite development server:

```bash
npm run dev
```

Vite will start the dev server at:

```
http://localhost:5173
```

The dev server features:
- **Hot Module Replacement (HMR)** — changes to JSX/CSS instantly reflect in the
  browser without a full page reload
- **Fast cold start** — Vite uses native ES modules; no bundling step on startup
- **Error overlay** — runtime and build errors display directly in the browser

---

### Building for Production

Generate an optimised production bundle:

```bash
npm run build
```

Vite will:
1. Tree-shake unused code and dependencies
2. Minify JavaScript and CSS
3. Apply asset fingerprinting (content hashes in filenames for cache busting)
4. Output everything to the `dist/` directory

Output structure:
```
dist/
├── index.html
├── assets/
│   ├── index-[hash].js      # Bundled JS (minified)
│   └── index-[hash].css     # Bundled CSS (minified)
└── [other static assets]
```

---

### Preview Production Build

To test the production build locally before deploying:

```bash
npm run preview
```

This starts a local static server serving the `dist/` folder, simulating what
Vercel will serve in production.

```
http://localhost:4173
```

---

### Linting

Run ESLint across all source files:

```bash
npm run lint
```

The ESLint configuration (`eslint.config.js`) enforces:
- React Hooks rules (`eslint-plugin-react-hooks`)
- React Refresh compatibility (`eslint-plugin-react-refresh`)
- General JS best practices (`@eslint/js` recommended)

---

## ⚙️ Environment & Configuration

### Tailwind CSS (`tailwind.config.js`)
Tailwind scans all files in `./src/**/*.{js,jsx}` and `./index.html` to determine
which utility classes to include in the final CSS bundle. Unused classes are
automatically purged in production, keeping CSS output minimal.

### Vite (`vite.config.js`)
Uses `@vitejs/plugin-react` (with Oxc transform) for fast JSX compilation and
React Fast Refresh during development.

### PostCSS (`postcss.config.js`)
Runs Tailwind CSS as a PostCSS plugin and applies Autoprefixer to ensure
cross-browser CSS compatibility (vendor prefixes added automatically).

### ESLint (`eslint.config.js`)
Uses the new flat config format introduced in ESLint 9. Configured with browser
globals and React-specific rules for hooks and refresh behaviour.

---

## ☁️ Deployment on Vercel

### Live URL
🔗 **[https://solvara-safaris.vercel.app](https://solvara-safaris.vercel.app)**

### Why Vercel?
Vercel is the ideal platform for Vite/React SPAs — zero configuration required,
global CDN, automatic HTTPS, and Git-triggered deployments.

### SPA Routing Configuration
The `vercel.json` file tells Vercel to serve `index.html` for every incoming URL:

```json
{
  "rewrites": [
    { "source": "/(.*)", "destination": "/index.html" }
  ]
}
```

**Why this is needed:** Without it, navigating directly to a deep link like
`/destinations/kenya` would cause Vercel to look for a file at that path on the
server. Since no such file exists (it's a React route, not a real file), Vercel
would return a `404`. The rewrite rule forwards all requests to `index.html`, where
React Router takes over and renders the correct component client-side.

### Deploying Your Own Fork

**Option A — Vercel Dashboard (Recommended)**

1. Fork this repository to your GitHub account
2. Go to [vercel.com](https://vercel.com/) → "Add New Project"
3. Import your forked GitHub repository
4. Vercel auto-detects Vite — no build settings needed
5. Click **Deploy**

Every subsequent push to `main` triggers an automatic production deployment.
Pull requests get automatic preview deployments with unique URLs.

**Option B — Vercel CLI**

```bash
npm install -g vercel
vercel login
vercel --prod
```

---

## 📦 Key Dependencies Explained

| Package | Why It's Used |
|---|---|
| `react@19` | Latest stable React with concurrent rendering, automatic batching, and `use()` hook |
| `react-dom@19` | DOM renderer for React — required alongside `react` |
| `react-router-dom@7` | Declarative client-side routing with ``, ``, ``, `useNavigate`, `useParams` |
| `framer-motion@12` | Production-grade animation library — page transitions, scroll reveals, gesture animations |
| `lucide-react@1` | Lightweight, tree-shakeable icon library with 1000+ icons as React components |
| `clsx@2` | Utility for composing conditional class name strings cleanly |
| `tailwind-merge@3` | Intelligently merges Tailwind CSS classes, resolving conflicts (e.g., `p-4` vs `p-8`) |
| `tailwindcss@3` | Utility-first CSS framework — generates atomic CSS classes from JSX |
| `vite@8` | Next-generation frontend build tool — instant dev server, optimised production builds |
| `@vitejs/plugin-react@6` | Official Vite plugin for React — JSX transform via Oxc, Fast Refresh |
| `postcss@8` | CSS transformation pipeline (required by Tailwind) |
| `autoprefixer@10` | PostCSS plugin that adds vendor prefixes for cross-browser CSS compatibility |

---

## 🎨 Design Decisions

**React 19** was chosen to leverage the latest concurrent rendering improvements and
automatic batching — ensuring the UI stays responsive even during heavy animation sequences.

**Vite 8** over Create React App or Webpack because of its instant dev server startup
(native ES modules, no bundling on cold start) and significantly faster production builds.

**Tailwind CSS** over component libraries (MUI, Chakra, etc.) to maintain complete
design freedom without fighting against predefined component styles. The luxury safari
aesthetic requires precise control over every visual element.

**Framer Motion** over CSS animations or GSAP because of its React-native API —
`` wraps any component and animations are declared declaratively via props,
keeping animation logic co-located with component structure.

**React Router DOM v7** provides the most mature, production-tested client-side routing
solution for React SPAs, with full support for nested routes, dynamic segments, and
programmatic navigation.

**Vercel** over Netlify or GitHub Pages because of its first-class Vite support, edge
network performance, instant rollbacks, and tight GitHub integration.

---

## 🔮 Future Improvements

- [ ] Add a **booking enquiry form** with client-side validation and email integration
      (e.g. EmailJS or Resend)
- [ ] Integrate a **headless CMS** (Sanity.io or Contentful) for dynamic safari package
      data — eliminating hardcoded content from JSX
- [ ] Add **TypeScript** for type safety across props, route params, and API responses
- [ ] Implement **lazy loading** of route components with `React.lazy()` +
      `` for faster initial load times
- [ ] Add a **blog / travel journal section** with markdown-based articles
- [ ] Integrate **Google Analytics** or Plausible for visitor tracking
- [ ] Write **unit tests** with Vitest + React Testing Library for core components
- [ ] Add **PWA support** (service worker, offline caching, installable on mobile)
- [ ] Optimise images with **WebP format** and lazy loading (`loading="lazy"`)

---

## 👤 Author

**Gaurav Tawde**
Senior SRE & Cloud Infrastructure Engineer | MSc Information Systems Management

- 🐙 GitHub: [@Gtawde953](https://github.com/Gtawde953)
- 💼 LinkedIn: [linkedin.com/in/gaurav-tawde](https://linkedin.com/in/gaurav-tawde)
- 🌍 Based in Dublin / Galway, Ireland

---

## 📄 License

This project is licensed under the **MIT License**.

```
MIT License

Copyright (c) 2025 Gaurav Tawde

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
```

---

> *Built with ❤️ as a personal frontend project. If you found this useful, consider
> leaving a ⭐ on the repo!*
