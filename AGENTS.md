# Ashlar Build — notes for AI coding agents

One HTML file: markup, inline CSS and inline scripts; GSAP with ScrollTrigger, Lenis smooth scroll, all from jsDelivr. No build step, no framework.

## Files
Work from the files: a page read through a link comes back as a summary, and a page rebuilt from it would differ.
```bash
curl -LO https://raw.githubusercontent.com/8bsite/construction-company-website-template/main/index.html
curl -LO https://raw.githubusercontent.com/8bsite/construction-company-website-template/main/AGENTS.md
curl -LO https://raw.githubusercontent.com/8bsite/construction-company-website-template/main/LICENSE
curl -LO https://raw.githubusercontent.com/8bsite/construction-company-website-template/main/CREDITS.md
```
In Windows PowerShell type `curl.exe`. Publish `index.html` with LICENSE and CREDITS.md; this file, README.md and `previews/` are not part of the site.

## Do not break
- Keep it one file unless the user asks otherwise; no framework or bundler for copy, colour or photo changes.
- Keep the ids and the `data-8b-section` / `data-8b-motion` attributes. Each section has its styles in `<style data-8b-part="section:<id>">` and its animation, if any, in `<script data-8b-part="scene:<id>">`.
- The scripts find these classes and attributes; when you change a section's markup, keep them or update the script:
  - `section-script:nav`: `.nav__bar` `.nav__num` `.nav__label` `.index` `.nav__index` `.index__close` `data-8b-section` `.chapter` `.chapter__num` `.chapter__label` `data-step`
  - `section-script:opening`: `.wall`
  - `section-script:crew`: `.crew__shuffle` `.crew__status` `data-message`
  - `section-script:contact`: `.contact__form` `.contact__status`
  - `scene:opening`: `.opening__first` `.opening__ground` `.wall` `.wall__joints` `.wall__level` `.wall__course` `.opening__room` `.opening__copy` `.opening__panel` `.wall__block`
  - `scene:services-index`: `.services__frame` `.services__list` `.svc`
  - `scene:work-gather`: `.work__sheet` `.work__item`
  - `scene:materials-fan`: `.materials__strips` `.mat` `.mat__tone`
  - `scene:process-courses`: `.process__wall`
  - `scene:promise-stack`: `.promise__type` `.promise__word` `.promise__copy` `.promise__rule` `.promise__list`
  - `scene:reviews-stack`: `.review` `.review__body`
  - `scene:contact-lines`: `.contact__title` `.contact__line--a` `.contact__line--b` `.contact__sheet`
- Colours, fonts, radii and shadows are CSS variables in the `:root` block (`data-8b-part="tokens"`); change them there and keep body text at 4.5:1 contrast or more.
- Animations run only when the visitor allows motion (`prefers-reduced-motion: no-preference`); the page must stay readable without them.
- A display line with `style="--len:N"` is sized to fill its width: N is its number of characters, spaces included (`Fixed` → 5).
- Keep the header comment and `<meta name="generator">`. Keep the "Design: 8B" footer link unless the site owner asks to remove it.

## Replace before publishing
- Everything marked `data-8b-placeholder` (og-image, favicon, phone, email, form, social); remove the attribute once the real value is in. With no real value: no preview image — delete the `og:image` tag and set `twitter:card` to `summary`; no phone, email or address — remove that link or row.
- "Book a visit" (nav) and "Book a site visit" (first screen): link to #contact now; point them to your booking or calendar URL if you use one (or keep the anchor to the form).
- **The form sends nothing.** `section-script:contact` checks the fields and shows a thank-you message without sending. Pick one:
  - Formspree: set `action="https://formspree.io/f/<id>"` on the form; in the script, before the thank-you message, `await fetch(form.action, { method: 'POST', body: new FormData(form), headers: { Accept: 'application/json' } })` and show it only if the response is ok.
  - Netlify Forms (site on Netlify): add `name="contact" data-netlify="true"` and `<input type="hidden" name="form-name" value="contact">`; send with `fetch('/', { method: 'POST', headers: { 'Content-Type': 'application/x-www-form-urlencoded' }, body: new URLSearchParams(new FormData(form)) })`.
  - No form service: remove the `<form>` together with the script that handles it (it would fail without the form) and keep the email link.
- Invented demo facts (ask the user for the real ones; do not make up prices, dates or addresses):
  - Company history and size: "since 2009" (opening lead and facts), "Fourteen builders" (opening statement) and "Fourteen of us, all on payroll" (crew), own carpenters, electricians and plumbers on payroll (opening), cabinetry made "in our own shop in Gowanus" (services).
  - Licence and insurance: "Licensed home improvement contractor, New York City" (opening), "NYC license 0000000. Insured to $2,000,000." (footer; the licence number was replaced with zeros).
  - Place: Brooklyn, NY (index overlay, opening, title and meta description), the office "100 Example Street, Brooklyn, NY 11217" (contact, footer; replaced), "Based in Brooklyn since 2009" (opening), service area Brooklyn, western Queens, Manhattan and Jersey City (FAQ "Where do you work?").
  - Phone (718) 000-0000 and email hello@ashlarbuild.example (index overlay, contact, footer; replaced) and office hours "Monday to Friday, 7:30–17:00. Saturdays by appointment." (contact).
  - Durations and prices per service: Kitchens 8–12 weeks, from $68,000; Bathrooms 4–6 weeks, from $34,000; Lofts 10–14 weeks, from $95,000; Rear extensions 16–24 weeks, from $180,000; Restoration priced per room (services). "Most jobs between six and twenty weeks" (opening).
  - Survey terms: half a day on site, drawings "to the quarter inch", a quote "valid for sixty days", the survey costs $450 and comes off the job (survey, contact form labels); the dimensions "Width 15′ 10″" / "Height 9′ 8″" and the caption "Parlour floor, Clinton Hill" (survey).
  - Finished work: "Twelve rooms from the last eighteen months" and twelve captions with Brooklyn neighbourhoods (work). The photos are stock photos, not the company's projects: replace them with your own work before publishing.
  - Schedule: Week 0, Week 1, Weeks 2–5, Weeks 4–7, Weeks 7–12 and "photos every Friday" (process); surveys within two weeks of a call, building six to ten weeks after signing (FAQ).
  - Guarantees: fixed price, a handover date with "$250 for every working day" if missed, and a ten-year guarantee on structure and waterproofing that moves with the house (promise).
  - Payment: "A ten percent deposit, then a payment as each stage passes inspection" (FAQ); smallest job a single bathroom, no repairs or handyman work (FAQ); permits handled by an expediter (FAQ); heated floors as standard in bathrooms (services).
  - People: Joe Brennan (site lead, 16 years), Ines Varga (surveyor and estimator, 9 years), Kwame Asante (electrician, 12 years), Rafael Ortiz (plumber, 8 years), Mehmet Kaya (plasterer, 22 years) (crew). The portraits are stock photos of other people: use photos of your own team.
  - Reviews: Priya and Sam Okafor (rear extension, Ditmas Park, 2025), Hannah Lowe (kitchen, Park Slope, 2024; mentions "Joe"), Daniel Reyes (restoration, Crown Heights, 2024; mentions an 1890 stair), Margaret Chen (two bathrooms, Cobble Hill, 2025), and "Four clients from the last two years" (reviews). Use only real reviews you have permission to publish.
  - Response time: "we will call within one working day" (contact text and the #contact-ok message).
  - "© 2026 Ashlar Build LLC" (footer).
- `<title>`, the meta description and the og tags; photos (Unsplash, see CREDITS.md) when the user has their own.

## Notes
- Chapter numbers and labels are written in each section's intro ("02 ( Services )"), in the Index list and in the footer's "Back to 01 Practice ↑" link; the top bar reads them from the sections. When you add, remove or rename a section, update all three.
- The wall of blocks on the first screen and the process blocks are HTML and CSS, not images: restyle them through the colour variables.
- Red (--color-7) is used only for measuring marks, link hover lines and focus outlines; keep it off large areas and body text.
- The order-of-work wall is laid out for exactly five stages; a sixth needs its own place in the grid.
- Shuffle re-orders the crew in the browser only; the order in the file is the order on load.
- On desktop the process section shows only its heading for the first part of its scroll, until the first block lands (intended: the empty site before the first course).
- Without JavaScript the Index button and the chapter arrows do nothing; the section links stay reachable in the footer.

## Common edits
- Rebrand: search the old name (`Ashlar Build`) in any letter case and replace every match; change the favicon letter and colours in `<link rel="icon">`.
- Photos: replace `src` and delete `srcset` and `sizes` (they list Unsplash sizes), keep `width`/`height` to the new photo's ratio, update `alt` and CREDITS.md.
- Remove a section: delete its markup, its `section:<id>` and `scene-style:<id>` styles, its `scene:<id>` and `section-script:<id>` scripts, and links to `#<id>`.
- Native scroll instead of smooth scroll: delete the Lenis block in `page-init` and the Lenis `<script>` tag.

## Check and publish
- Open the page at 375 and 1440 px, with reduced motion on, with the console open.
- Search `data-8b-placeholder` and the old name: nothing should be left but class names.
