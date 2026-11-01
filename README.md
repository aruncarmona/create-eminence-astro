# Eminence Astro

An opinionated Astro starter for Cloudflare Workers, with the setup and conventions to start building your website without any hassles.

Eminence Astro combines a standard Astro project with consistent tooling, accessible defaults, and a defined project struture to ensure consistency and DX. Use the creator to set up your project, then work directly with Astro.

## Features

- **Astro and TypeScript:** strict checking, source aliases, and pnpm.
- **Cloudflare Workers:** adapter, binding types, and local production preview.
- **Tailwind CSS:** accessible layouts, a default font, and light/dark/system themes.
- **Svelte:** interactive islands where needed.
- **Formatting and tests:** Prettier, component tests, browser checks, and CI.
- **SEO:** Eminence Astro Suite, page metadata, icons, canonical URLs, sitemap, and robots configuration.
- **Localization:** optional Paraglide support, with English as the primary language and Spanish as the second by default.
- **Error pages:** localized 404 and 500 pages.
- **Email:** Resend hosted templates and a helper that selects the email language from the website locale.
- **Configuration:** environment and secret examples for local development, preview, and production.

## Conventions

Routes live in `src/pages/`, layouts in `src/layouts/`, and reusable components in `src/components/`. Group page-specific sections under `src/components/sections/<page>/`.

Pages compose layouts and sections. Keep reusable logic outside route files, use Astro for ordinary content, and hydrate Svelte only when browser interactivity is needed.

The default stack is Astro, Cloudflare Workers, Tailwind, Svelte, and pnpm. The creator asks about Git and multilingual support; choosing single language leaves out Paraglide and language navigation.

## Documentation

See the [wiki](https://github.com/aruncarmona/create-eminence-astro/wiki) for setup, commands, customization, and a guide to each feature.
