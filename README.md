# Wellness with Lindz — Astro rebuild

A static, subscription-free rebuild of wellnesswithlindz.co.za, built with [Astro](https://astro.build).
This is a **preview build** — see the project scope doc for context: it's meant to be deployed to a
staging URL and reviewed before any decision is made about replacing the WordPress site.

## Stack

- **Astro** (static site generator) — no server, no database, no per-plugin subscriptions.
- **Content collections** (Markdown files in `src/content/`) for blog posts, team bios, and testimonials —
  adding content means adding a new `.md` file, not writing code.
- Plain CSS with design tokens in `src/styles/global.css` — no framework dependency.
- Forms currently point at Formspree placeholder URLs (`REPLACE_WITH_FORM_ID`) — swap in a real
  Formspree (or similar) endpoint before launch. Free tier is enough for this traffic level.

## Getting started

```bash
npm install
npm run dev       # local dev server, usually http://localhost:4321
npm run build      # production build to ./dist
npm run preview    # preview the production build locally
```

## Adding content

- **New blog post** → add a Markdown file to `src/content/blog/`, e.g. `src/content/blog/my-post.md`,
  with frontmatter `title`, `description`, `pubDate`, optional `draft: true` to hide it.
- **New team member** → add a file to `src/content/team/` with `name`, `role`, `order`.
- **New testimonial** → add a file to `src/content/testimonials/` with `author`, `order`.
- **Announcement banner text** → edit the `messages` array directly in
  `src/components/AnnouncementBar.astro`.

## Still to do before launch

- [ ] Replace all placeholder copy (About, Team bios, Services descriptions) with real content from Lindiwe.
- [ ] Replace placeholder team photo blocks with real photos.
- [ ] Wire the two forms in `src/pages/contact.astro` to a real Formspree (or equivalent) endpoint.
- [ ] Write a real privacy policy in `src/pages/privacy.astro` (POPIA-compliant).
- [ ] Confirm business email (e.g. hello@wellnesswithlindz.co.za) is unaffected by any hosting change.
- [ ] Add real Open Graph share image (`public/og-image.svg` is a placeholder).
- [ ] Deploy to a staging URL (Cloudflare Pages / Netlify / Vercel free tier all work well with Astro)
      for Lindiwe to review before any DNS cutover.

## Deploying

This is a static site — `npm run build` produces a `dist/` folder that can be deployed to any static
host. Cloudflare Pages, Netlify, and Vercel all have free tiers well within this site's expected traffic
and all deploy directly from a git repository with zero config beyond build command (`npm run build`)
and output directory (`dist`).
