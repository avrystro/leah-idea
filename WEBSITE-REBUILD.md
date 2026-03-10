# JWB Website Rebuild - Research Notes

Status: Exploration. No decision made yet. Need Leah's input on pain points.

## Current State

- Site: johnwbrickfoundation.org
- Platform: WordPress with WordPress editor
- Unknown: hosting provider, theme, plugins, who manages content updates

## Can We Get the WordPress Files?

Yes. Multiple paths:

1. **WordPress built-in export** (Tools > Export) - dumps all pages, posts, media, menus as XML. Gives you the content.
2. **Scrape the live site** - Use Apify or similar to crawl every page, extract text + images + structure. No WordPress admin access needed.
3. **wp-content/uploads** - All media (images, PDFs) are in this directory. Downloadable if you have hosting/FTP access.
4. **Database export** - If you have hosting access, export the MySQL database for full content including drafts.

**Key insight:** If rebuilding from scratch, you only need the CONTENT (text, images, structure), not the WordPress theme files, plugins, or PHP code. The content is the gold. The container is throwaway.

## What Needs to Be Mapped Before Rebuilding

| Area | Question | Why It Matters |
|------|----------|---------------|
| Content management | Who updates the site? How often? | Non-technical editors need a CMS (headless WordPress, Sanity, Contentful). A pure static site locks them out. |
| Donations | What processor? (Stripe, PayPal, Classy, Network for Good) | Can't break donation flow. Must be migrated carefully. |
| Integrations | Email signup, event registration, forms | Each needs a replacement tool or rebuild |
| SEO | Current URL structure, Google ranking | 301 redirects are mandatory or they lose organic traffic. #1 thing nonprofits forget during redesigns. |
| Hosting + DNS | Where's the domain registered? Current hosting? | Need to plan DNS migration if moving off WordPress hosting |
| Accessibility | WCAG 2.1 AA compliance | Health-related nonprofits should meet this standard |
| Budget + timeline | Tweak vs full rebuild? | Very different scopes. A WordPress theme refresh is 10x faster than a ground-up rebuild. |

## Do They Actually Need to Leave WordPress?

Maybe not. WordPress with a modern theme builder can look just as good as a custom site. The question is:

- Are they limited by WordPress itself? (probably not - it can do almost anything)
- Are they limited by their current theme/design? (a new theme fixes this without a platform migration)
- Do they want something AI can maintain/generate? (this is the real reason to go custom)

**The quiz page we built can live on the existing WordPress site** - just embed the HTML in a custom page template or use an iframe. No full rebuild required for this feature.

## Fastest Path If They Do Rebuild

1. Scrape entire site with Apify (structured content extraction)
2. Map all integrations (donations, forms, email, events)
3. Build in Next.js + Tailwind (same stack as quiz)
4. Headless CMS for content management (Sanity or Contentful)
5. Deploy on Vercel
6. Set up 301 redirects for every old URL
7. Migrate DNS

## Open Question for Leah

**What's the actual pain point with the current site?** The answer determines whether this is a theme refresh (small), a design overhaul on WordPress (medium), or a full platform migration (large).

## Sources

| Type | Reference | What It Contributed |
|------|-----------|-------------------|
| Chat session | Session with Avry (2026-03-09) | Original question about WordPress migration |
