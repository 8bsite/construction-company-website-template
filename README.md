# Free HTML construction company website template with GSAP scroll animations — Ashlar Build

**One-page website for a construction company: a home renovation and extension contractor: a free HTML template in one file, with GSAP scroll animations, no build step, MIT license. Made by [8B](https://8b.com/), the AI website builder.**

[![License: MIT](https://img.shields.io/badge/license-MIT-blue)](LICENSE) ![one HTML file: no build](https://img.shields.io/badge/one%20HTML%20file-no%20build-orange) ![GSAP: ScrollTrigger](https://img.shields.io/badge/GSAP-ScrollTrigger-88ce02)

**[Live demo](https://8bsite.github.io/construction-company-website-template/)** · **[Use this template](https://github.com/new?template_name=construction-company-website-template&template_owner=8bsite)** · **[Download ZIP](https://github.com/8bsite/construction-company-website-template/archive/refs/heads/main.zip)**

<a href="https://8bsite.github.io/construction-company-website-template/"><img src="previews/desktop.png" alt="Ashlar Build, a free HTML template: first screen on a desktop" width="76.1%"></a> <a href="https://8bsite.github.io/construction-company-website-template/"><img src="previews/phone.png" alt="Ashlar Build, a free HTML template: first screen on a phone" width="21.9%"></a>

<p align="center"><a href="https://8bsite.github.io/construction-company-website-template/"><img src="previews/scroll.gif" alt="Ashlar Build, a free HTML template: scrolling through the first sections on a desktop" width="40%"></a><br><sub>Scroll animation</sub></p>

A one-page site for a Brooklyn builder that does kitchens, bathrooms, lofts, rear extensions and restoration, with services and prices, a survey, finished work, crew, reviews and a site-visit form. Strict black, white and grey with one red for measuring marks; a wall of grey blocks comes apart into the room photo, scattered photos settle into a contact sheet and the word "Fixed" condenses as you scroll.

Good for: builder, general contractor or renovation company; kitchen, bathroom or loft conversion specialist; architect or design-and-build practice; any trade business that quotes from a site visit. Free for personal and commercial use (MIT), made by [8B](https://8b.com/).

## Quick start

Pick one:

- **With an AI coding agent** (Claude Code, Codex, Cursor, Windsurf…). Download the files into your project (in Windows PowerShell type `curl.exe`):
  ```bash
  curl -LO https://raw.githubusercontent.com/8bsite/construction-company-website-template/main/index.html
  curl -LO https://raw.githubusercontent.com/8bsite/construction-company-website-template/main/AGENTS.md
  curl -LO https://raw.githubusercontent.com/8bsite/construction-company-website-template/main/LICENSE
  curl -LO https://raw.githubusercontent.com/8bsite/construction-company-website-template/main/CREDITS.md
  ```
  Then give your agent this prompt:
  ```text
  Read AGENTS.md, then edit index.html. Use this template as the base for a site for <your business: construction company, contractor or renovation firm; services, area, prices, team>. Keep the layout, the motion and the single-file format; replace the brand name, copy, photos (use your own projects and team), prices, links and contacts, and recolour it through the CSS variables if needed.
  ```
  Give the agent the downloaded file, not a link: an agent reads a link as a summary and would rebuild a different page.
- **No code.** Download the ZIP, unzip it, replace the contacts and texts in `index.html`, put `index.html` into an empty folder and drag that folder onto [Netlify Drop](https://app.netlify.com/drop). The page is online in a minute.
- **On GitHub.** Click **[Use this template](https://github.com/new?template_name=construction-company-website-template&template_owner=8bsite)** to get your own copy, then **Settings → Pages → Deploy from a branch → main**. Your site appears at `https://<you>.github.io/<repo>/`.

## What's on the page

- **Navigation** — top bar: wordmark, current chapter with previous/next arrows, Book a visit, Index overlay
- **Homes rebuilt in the right order.** — first screen: headline, lead, two buttons and a wall of grey blocks; second screen: room photo with a statement panel and three facts
- **Five kinds of job, one way of working** — list of services with duration and starting price beside a sticky photo frame (demo: kitchens, bathrooms, lofts, extensions, restoration)
- **A fixed price, from a measured survey.** — how quoting works: a measured photo with red dimension lines and four numbered notes
- **Rooms we handed back** — black gallery: twelve project photos with room and neighbourhood captions
- **Five materials we keep coming back to** — five material strips with a photo, name and use (demo: plaster, oak, marble, slate, steel)
- **Built in the order a house is built** — five work stages laid as blocks of a wall, each with a week range
- **Fixed** — guarantees: one huge condensed word and three written promises
- **The people who quote are the people on site** — team row: five portraits at varied heights with name and trade, Shuffle button
- **What people say after handover** — four client quotes on grey-to-black cards that stack as you scroll
- **Before you call** — questions and answers (native &lt;details&gt;)
- **Book a site visit** — site-visit request: address, phone, email, hours, a photo and a form (placeholders)
- **Footer** — black footer: big back-to-top link, address, contacts, section links, licence line, copyright and the Design: 8B credit

## Before you publish

- Replace everything marked `data-8b-placeholder` (social preview image, favicon, phone, email, form, social) and the invented demo facts — prices, dates, address. [AGENTS.md](AGENTS.md) lists them.
- The contact form does not send anything yet: connect it to a form service (Formspree, Netlify Forms) or remove it; [AGENTS.md](AGENTS.md) shows both.

## Customize

- **Colours and fonts**: CSS variables in the `:root` block at the top of `<head>`.
- **Text**: edit it in place. A big display line with `style="--len:N"` fills its width: set N to its new number of characters.
- **Photos**: replace `src`, delete `srcset` and `sizes` (they list Unsplash sizes) and update the `alt` texts.
- **Animations**: each section's animation is one `<script data-8b-part="scene:<id>">` block at the end of the file. For native scroll, delete the Lenis block in `page-init`.

## For developers

- **Stack.** HTML and CSS (custom properties, cascade layers) with GSAP 3.13.0, ScrollTrigger, Lenis 1.3.27 from jsDelivr. No build step, no framework, no npm. 107 KB.
- **Layout of the file.** `<head>`: CSS variables, shared classes, then one style block per section. Then the markup, one element per section with a one-line comment above it. End of `<body>`: small behaviour scripts, the libraries, smooth scroll (`page-init`), the effects, one animation script per section.
- **Browsers.** Chrome and Edge 108+, Safari 15.4+, Firefox 101+ (it uses cascade layers, small/dynamic viewport units).
- **Accessibility.** Motion runs only when the visitor's system allows it; with "reduce motion" the page is complete and still. FAQ answers use native `<details>` and open without JavaScript. Every photo has alt text.
- **External requests.** fonts.gstatic.com, images.unsplash.com, cdn.jsdelivr.net. No analytics, no cookies. To self-host everything (offline use, or Google Fonts and GDPR in the EU), download those files and change the URLs.
- **Licences of the parts.** GSAP is free, commercial use included, under its own standard licence (not MIT); Lenis is MIT; fonts are SIL OFL; photos are under the Unsplash License. See [CREDITS.md](CREDITS.md).

## FAQ

**Can I use it for a client or a commercial site?** Yes. The code is MIT: use it, change it, sell the site you build with it.

**Do I have to keep the "Design: 8B" link?** No. It is welcome, not required.

**Can I use it in React, Next.js, Astro or Vue?** Yes. Move each section's markup and style block into a component and run its animation script in `useGSAP()` (React) or `onMounted` (Vue); start Lenis once. Or keep it as a separate static landing page next to your app (`example.com` for the landing, `app.example.com` for the app).

**Why doesn't the contact form send?** It is a demo. Connect it to Formspree, Netlify Forms or your backend; AGENTS.md has the steps.

**Where are the photos from?** Unsplash; they load from Unsplash's servers. Replace them with your own when you can.

## More free templates

[More 8B templates on GitHub](https://github.com/8bsite) · [8b.com](https://8b.com/)

## License

The template code is MIT licensed — see [LICENSE](LICENSE). Photos, fonts and libraries keep their own licences — see [CREDITS.md](CREDITS.md).
