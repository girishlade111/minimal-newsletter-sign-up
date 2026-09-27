# Minimal Newsletter Sign-Up

A cinematic, full-screen newsletter sign-up landing page for **"American Yeoman"** — a heritage publication celebrating local communities and food sovereignty. Built as a polished demo landing page with a full-bleed pastoral background, staggered entrance animations, and a glassmorphism email capture form with a success state.

## Features

- **Full-screen hero design** — immersive pastoral-landscape background image with a dark cinematic gradient overlay
- **Newsletter email capture** — floating pill-shaped form with backdrop-blur glassmorphism, email validation, and an animated success state on submit
- **Staggered entrance animations** — headline, description, and form fade/slide in with custom `fade-in-up` and `slow-pan` keyframes
- **Serif display typography** — Instrument Serif headline paired with Geist Sans body text via `next/font`
- **Dark mode theming** — `next-themes` provider with shadcn/ui token-based colors
- **shadcn/ui components** — button, input, and the full Radix UI primitive set wired in and ready to extend
- **Responsive** — scales from mobile to ultrawide (`text-4xl` up to `xl:text-9xl` headline)

## Tech Stack

- **Framework:** [Next.js 15](https://nextjs.org/) (App Router, static export via `output: "export"`)
- **Language:** TypeScript
- **Styling:** Tailwind CSS 4 + shadcn/ui + Radix UI primitives
- **Fonts:** Geist Sans, Geist Mono, Instrument Serif (`next/font`)
- **Animation:** Custom CSS keyframes (`animate-fade-in-up`, `animate-slow-pan`)
- **Theming:** next-themes

## Quick Start

### Prerequisites

- Node.js 18+ and npm/pnpm

### Install & Run

```bash
# install dependencies
pnpm install
# or: npm install

# start the dev server
pnpm dev
```

Open [http://localhost:3000/minimal-newsletter-sign-up](http://localhost:3000/minimal-newsletter-sign-up) in your browser.

### Build (static export)

```bash
pnpm build
```

This produces a fully static site in `out/`, ready to host anywhere (GitHub Pages, Cloudflare Pages, Netlify, Vercel).

## Project Structure

```
├── app/
│   ├── page.tsx          # Newsletter landing page (email form + success state)
│   ├── layout.tsx        # Root layout, fonts, metadata, theme provider
│   └── globals.css       # Tailwind + custom animation keyframes
├── components/
│   ├── ui/               # shadcn/ui primitives (button, input, ...)
│   └── theme-provider.tsx
├── lib/
│   └── utils.ts          # clsx + tailwind-merge helper
├── public/
│   └── images/pastoral-landscape.jpg   # Hero background image
├── next.config.mjs       # output: "export", images unoptimized
└── components.json       # shadcn/ui config
```

## Environment Variables

None. This demo does not call any backend or third-party API. The sign-up form currently simulates submission (logs the email to the console and shows a success state) — wire `handleSubmit` in `app/page.tsx` to your newsletter provider (Buttondown, ConvertKit, Mailchimp, etc.) to go live.

## Deployment Notes

- The site is a **static export** (`output: "export"` in `next.config.mjs`) — no server, no API routes, no server actions required.
- **GitHub Pages:** `basePath: "/minimal-newsletter-sign-up"` is set for the project-pages subpath (`https://girishlade111.github.io/minimal-newsletter-sign-up/`). The hero image URL in `app/page.tsx` is prefixed with the same subpath. **Remove `basePath` (and the image prefix) when deploying to a root domain or Vercel.**
- **Vercel:** deploy directly — no changes needed beyond removing `basePath` (originally generated on [v0.app](https://v0.app)).
- Images are marked `unoptimized: true` so `next/image` optimization is skipped during static export.

## Notes

- TypeScript and ESLint errors are ignored during builds (`ignoreBuildErrors` / `ignoreDuringBuilds`) — this matches the original v0.app project settings.
- `recharts`, `date-fns`, and other Radix-based packages come from the default v0 shadcn template; the landing page itself only uses a subset.

---

Built by Girish Lade — https://ladestack.in
