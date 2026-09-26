# Build Prompts — Sivamed Hospital Website

Copy-paste one of these into an AI coding agent (Cline / Cursor / Copilot Chat / ChatGPT) working **inside this project folder**. They are self-contained — the agent needs no extra context from you.

- **PROMPT 1 — Master build prompt (Option A: React/Vite app)** ← use this for your presentation build
- **PROMPT 2 — Finish the static HTML site (Option B: fastest to live)**
- **PROMPT 3 — Presentation content prompt (slides + demo script)**
- **PROMPT 4 — Small surgical prompts** (one-task fixes)

> Before running any prompt, install **Node.js 20 LTS** (it is not installed on this PC) so `npm install`, `npm run dev` and `npm run build` work. Read `PROJECT-ANALYSIS.md` for the full audit.

---

## PROMPT 1 — Master Build Prompt (React/Vite)

```text
ROLE
You are a senior React developer + SEO engineer finishing a production website for a real
business. Work directly in the existing project at
c:\Users\ELCOT\Desktop\Hospital-website\Hospital-website

GOAL
Turn this half-finished project into ONE complete, correct, presentable website for
"Sivamed Multispeciality Hospital", Pollachi, Tamil Nadu. Right now the repo contains TWO
conflicting websites - a static HTML hospital site (index.html + css/style.css + js/main.js
+ pages/*.html) and a React 18 + Vite 5 SPA in src/ that is branded as a US dental clinic
("Premium Periodontist"). The React app is orphaned: index.html has no <div id="root"> and
no <script type="module" src="/src/main.jsx">, so React never mounts and `npm run build`
would produce a broken site.

NON-NEGOTIABLE RULES
1. React is the single stack going forward. Move the static site to legacy/ (keep it as
   reference for content) instead of deleting it - but nothing outside legacy/ may use
   css/style.css or js/main.js.
2. Keep the existing stack and conventions. Do NOT add new libraries unless absolutely
   required. Already installed: react 18, react-dom, react-router-dom 6, react-helmet-async,
   framer-motion, react-icons (import icons from react-icons/hi and react-icons/fa),
   tailwindcss 3, vite 5.
3. Match the existing code style exactly: functional components, default exports, Tailwind
   utilities plus the component classes already in src/index.css (btn-primary, btn-secondary,
   input-field, section-title, section-subtitle, glass-card, gradient-primary, gradient-text,
   card-hover, testimonial-card, service-card, doctor-card, stat-number, timeline-item,
   accordion-*, lightbox-*). Reuse them; never create a second design system.
4. Every page must set <title>, <meta name="description">, a canonical link and Open Graph +
   Twitter tags with react-helmet-async, following the pattern already used in src/pages/*.
5. Never invent hospital facts. Use the BRAND FACTS block below and one shared
   src/data/hospital.js file as the single source of truth. Where a fact is unknown use an
   obvious placeholder like REPLACE_WITH_... and list it in your final summary.
6. Keep framer-motion animations subtle (short durations, whileInView with
   initial={{opacity:0, y:30}}) and always respect prefers-reduced-motion.
7. Accessibility: real alt text on every image, aria-label on icon-only buttons, a <label> for
   every input, interactive cards as <Link>/<button> (keyboard focusable), mobile nav that
   closes correctly.
8. After each group of edits run `npm run build` and fix every error/warning. The task is not
   finished until `npm run dev` and `npm run build` both succeed.

BRAND FACTS (create src/data/hospital.js and import from it everywhere)
- name: Sivamed Multispeciality Hospital
- tagline: Advanced Healthcare With Compassion
- address: No.146/2, Near Kousalya Hospital, Bharathi Street, Mahalingapuram,
  Pollachi - 642002, Tamil Nadu, India
- phone: REPLACE_WITH_REAL_PHONE  (existing values are fake: "+91 4259-123-456",
  "+1 (555) 123-4567")
- whatsapp: REPLACE_WITH_REAL_WHATSAPP  (fake values in code: "9194259123456", "15551234567")
- email: info@sivamedhospital.com
- hours: Emergency 24/7; OPD Monday-Saturday 8:00 AM - 9:00 PM; Sunday 9:00 AM - 5:00 PM
- experience: 19+ years of healthcare service
- departments (14): General Medicine, General Surgery, Women's Health, Fertility Care,
  Obstetrics, Gynecology, Pediatrics, Diagnostic Services, Laboratory Services,
  Preventive Healthcare, Emergency Care, Health Checkups, Outpatient Services,
  Inpatient Services
- location notes: near Kousalya Hospital, Mahalingapuram, Pollachi
- domain: https://www.sivamedhospital.com
- socials: Facebook, Instagram, LinkedIn, Twitter, YouTube (URLs to be supplied)

TASKS - do them in this order and report after each phase

PHASE 1 - Make the React app run (critical)
1.1 Rewrite index.html as the React entry: keep lang="en", charset, viewport, theme-color,
    the hospital description/keywords, OG + Twitter tags, favicon link, Google Fonts
    preconnect + Inter/Playfair Display stylesheet and the Hospital JSON-LD, then add
    <div id="root"></div> and <script type="module" src="/src/main.jsx"></script> at the end
    of <body>. Remove the css/style.css link, the js/main.js script, the emergency banner div
    and all static markup.
1.2 Move the static site (the old index.html copy, pages/, css/, js/) into legacy/ and note it
    in README.md.
1.3 Create public/favicon.svg (simple hospital cross or "S" monogram in the brand gradient),
    public/images/og-image.jpg (1200x630 placeholder), and public/_redirects containing
    "/* /index.html 200" for SPA hosting.
1.4 Verify `npm run dev` renders the React Home page and `npm run build` succeeds.

PHASE 2 - Rebrand the React app from dental clinic to Sivamed Hospital
2.1 src/components/Navbar.jsx: logo text "Sivamed" / "Multispeciality Hospital", brand gradient,
    phone number and Book Appointment CTA from hospital.js. Show ALL primary links (remove the
    slice(0,6) so Technology/Gallery/Testimonials/Blog/FAQ are visible) - the nav must reach:
    Home, About, Departments, Doctors, Facility/Technology, Gallery, Testimonials, Blog, FAQ,
    Contact. Add an Emergency quick-call button. Keep the mobile drawer behaviour.
2.2 src/components/Footer.jsx: hospital name/description, real Pollachi address, phone, email,
    OPD + emergency hours, working social links, quick links to every page, department links to
    real department pages, and Privacy Policy / Terms / Sitemap links (delete the
    "link everything to /faq" hack).
2.3 src/components/WhatsAppButton.jsx: use hospital.js whatsapp number, prefilled message
    "Hello Sivamed Hospital, I would like to book an appointment. Name: / Phone: / Department: /
    Preferred date:", aria-label, remove the fake "1" badge.
2.4 Rewrite src/pages/Services.jsx as "Departments" (14 hospital departments with icon, short
    description and a link to /departments/:slug).
2.5 DELETE src/pages/DentalImplants.jsx and src/pages/GumDisease.jsx, their routes and every
    nav/footer link to them.
2.6 Rewrite page copy/statistics for the hospital: 19+ years, 14 departments, patients served,
    24/7 emergency. Remove the "3.8/5 JustDial rating" headline (or show the review count only).
2.7 Replace every testimonial and blog author with realistic placeholders clearly marked for the
    hospital to approve (e.g. "Patient Name (to be approved)"). Remove "Sarah Johnson",
    "Michael Chen", "Dr. James Mitchell" and "New York" everywhere.

PHASE 3 - Add the missing pages and routes
Create these pages in src/pages/ and register them in src/App.jsx (keep lazy loading):
  3.1  Doctors.jsx        -> /doctors                doctor grid, department filter, booking CTA
  3.2  DoctorProfile.jsx  -> /doctors/:slug          bio, qualifications, experience, timings, book
  3.3  Department.jsx     -> /departments/:slug      overview, symptoms, diagnostics, doctors, FAQs
  3.4  Emergency.jsx      -> /emergency              ambulance number, when to come, ER services
  3.5  Packages.jsx       -> /packages                health checkup packages, inclusions, pricing
  3.6  Insurance.jsx      -> /insurance               TPA/cashless list, what to bring
  3.7  Inpatient.jsx      -> /inpatient               admission, visiting hours, discharge, billing
  3.8  Privacy.jsx        -> /privacy-policy
  3.9  Terms.jsx          -> /terms-of-service
  3.10 Sitemap.jsx        -> /sitemap                 human-readable link map
  3.11 ThankYou.jsx       -> /appointment/success     confirmation page (reads ?name= & ?dept=)
  3.12 NotFound.jsx       -> path="*"                 styled 404 with links back
Add matching data files under src/data/ (hospital.js, departments.js, doctors.js, packages.js,
blogPosts.js) so pages render from data, not hard-coded JSX.

PHASE 4 - Make the appointment form real
4.1 Extract the booking form into src/components/AppointmentForm.jsx used by Home (hero), Contact
    and every department/doctor page. Fields: name, phone, email (optional), department select
    (from departments.js), preferred doctor (optional), preferred date, preferred time, message,
    consent checkbox. Full client-side validation with inline errors and aria-invalid.
4.2 On submit POST the JSON to import.meta.env.VITE_APPOINTMENT_ENDPOINT (Formspree / Google
    Apps Script / hospital CRM). If the env var is missing, fall back to opening a prefilled
    wa.me link with hospital.js whatsapp and show a WhatsApp-fallback notice. Show a loading
    state, a success state with aria-live="polite", then navigate to /appointment/success.
    Include a honeypot field for spam.
4.3 Add .env.example with VITE_APPOINTMENT_ENDPOINT and VITE_GA4_ID, document it in README.md.
    Never hard-code secrets.
4.4 Replace src/pages/Admin.jsx mock data with a clearly-labelled demo mode: keep the tabs, read
    from src/data/, persist edits to localStorage, and add a simple VITE_ADMIN_PASSCODE gate plus
    a banner stating it is demo-only (no real auth).

PHASE 5 - Real content, images and trust
5.1 Add an image-first gallery: create public/images/gallery/ with placeholder files and an
    images.js manifest; render real <img> tags with loading="lazy", width/height,
    decoding="async" and descriptive alt text; keep the lightbox plus keyboard support
    (Esc / ArrowLeft / ArrowRight) and focus management.
5.2 Add a hospital photo to the Home hero and the About page with a graceful fallback if the
    file is missing.
5.3 Replace the fake map box in Contact.jsx with a real Google Maps <iframe> embed for
    "Sivamed Multispeciality Hospital, Mahalingapuram, Pollachi", add a "Get Directions" link
    and a nearby-landmarks list (near Kousalya Hospital).
5.4 Add trust badges (19+ years, 24/7 emergency, accreditation placeholders) and a
    "What patients say" section linking to /testimonials.

PHASE 6 - SEO, performance, accessibility, PWA
6.1 Create src/components/Seo.jsx wrapping Helmet to emit title, description, canonical, og:*,
    twitter:* and optional JSON-LD. Use it on every page: Hospital/MedicalClinic for Home,
    Physician for doctor profiles, MedicalWebPage for departments, FAQPage for FAQ, BlogPosting
    for blog posts, BreadcrumbList for inner pages.
6.2 Fix public/robots.txt: allow all, disallow /admin, sitemap
    https://www.sivamedhospital.com/sitemap.xml
6.3 Generate public/sitemap.xml covering every public route (including department, doctor and
    blog slugs) with realistic lastmod values.
6.4 Prerender for crawlers: add a prerender step (react-snap or equivalent) or generate static
    HTML snapshots for the top 8 routes during the build, and document the approach in README.md.
6.5 Performance: lazy-load below-the-fold images, keep the framer-motion chunk out of the
    critical path, add loading skeletons, and report gzipped CSS/JS sizes.
6.6 Accessibility pass: "Skip to main content" link wired to <main id="main-content">, labels on
    all inputs, aria-expanded on accordions/mobile menu, focus-visible rings, contrast >= 4.5:1,
    reduced-motion support, keyboard-navigable lightbox.
6.7 PWA: add public/manifest.webmanifest (name, short_name, theme_color, icons, display) and
    public/sw.js with a cache-first shell strategy; register it in src/main.jsx inside a window
    load listener with try/catch.

PHASE 7 - Housekeeping and docs
7.1 Delete temp_drive.html, temp_link.html and justdial_temp.html.
7.2 Add .gitignore (node_modules, dist, .env, .DS_Store) and a README.md documenting: purpose,
    stack, folder structure, npm install/dev/build, env vars, where to change hospital details
    (src/data/hospital.js), how to add a department/doctor/blog post, and deployment
    (Netlify/Vercel with SPA redirects).
7.3 Update package.json name/description/keywords away from "periodontist-website", remove the
    unused @heroicons/react dependency, and replace the failing "test" script placeholder.
7.4 Remove unused imports and dead code in every file you touch.

ACCEPTANCE CRITERIA (verify and report each one)
- `npm run build` succeeds with no errors; dist/ contains index.html, manifest, sitemap,
  robots.txt, favicon and assets.
- The words "Periodontist", "New York", "+1 (555)", "Sarah Johnson" and "Dr. James Mitchell"
  appear nowhere in src/, index.html or public/.
- Every route in the sitemap renders and is reachable by clicking (no dead links, no
  "Article Not Found" for a linked post).
- The appointment form delivers to the configured endpoint, or degrades to WhatsApp, and lands
  on /appointment/success.
- Unknown URLs show the styled 404 inside the site chrome.
- No 404s in the Network tab on Home, Departments, Department detail, Doctors, Doctor profile,
  Contact, Blog, Blog post, FAQ, Gallery, Emergency.
- Lighthouse (mobile): Performance >= 90, Accessibility >= 95, Best Practices >= 95, SEO = 100.
  Report the actual numbers.
- Responsive at 375px, 768px and 1440px with no horizontal scroll and a usable mobile menu.

OUTPUT FORMAT FOR YOUR FINAL REPORT
1. Summary of what changed, per phase.
2. Every file created / modified / deleted.
3. Build output sizes and the verification checklist with pass/fail.
4. Every remaining placeholder that needs real hospital data (REPLACE_WITH_* items).
5. Anything you deliberately did not do, and why.
```

---

## PROMPT 2 — Finish the Static HTML Site (Option B)

```text
ROLE
You are finishing a static multi-page HTML/CSS/JS hospital website (no framework, no build
step). Work in c:\Users\ELCOT\Desktop\Hospital-website\Hospital-website, which also contains
an unused React app in src/ - ignore src/, package.json, vite.config.js, tailwind.config.cjs
and dist/ for this task (they will be removed separately).

CONTEXT
- index.html (root) + pages/*.html (about, services, doctors, gallery, testimonials, faq,
  contact, blog) + css/style.css (3011 lines) + js/main.js (719 lines).
- Brand: Sivamed Multispeciality Hospital, No.146/2, Near Kousalya Hospital, Bharathi Street,
  Mahalingapuram, Pollachi - 642002, Tamil Nadu. 19+ years, 14 departments, 24/7 emergency,
  info@sivamedhospital.com. Placeholders to replace: phone "+91 4259-123-456" and WhatsApp
  "9194259123456" (use a CONFIG object with clear REPLACE_WITH_ markers if the real values are
  not supplied).
- Keep the existing visual language: CSS custom properties in :root, .container, .btn,
  .btn-primary, .btn-secondary, .card, .section-header, .reveal animations, emoji/inline-SVG
  icons. Do NOT introduce Tailwind, Bootstrap or a build step.

TASKS
1. Cleanup: delete temp_drive.html, temp_link.html and justdial_temp.html. Fix the stale
   headers that still say "PEDIATRIC HOSPITAL WEBSITE / Child-Friendly Healthcare Design" in
   css/style.css and "SUNSHINE PEDIATRIC HOSPITAL" (plus the pediatric console.log) in
   js/main.js - this is a multispeciality hospital, not a pediatric clinic.
2. Create the missing assets so nothing 404s: assets/icons/favicon.svg,
   assets/images/og-image.jpg (1200x630) and placeholder photos for the hero/gallery.
3. Replace all placeholder doctors in pages/doctors.html with a data-driven grid from a new
   js/data.js (name, qualification, department, experience, timings, photo, booking link) and
   delete the "Doctor details will be updated from official hospital records." text.
4. Add new pages that match the existing page template exactly (same emergency banner, nav,
   footer, floating WhatsApp + call buttons, back-to-top): privacy-policy.html, terms.html,
   sitemap.html, 404.html, thank-you.html, packages.html (health checkup packages),
   insurance.html (TPA/cashless list), emergency.html (ambulance + ER info).
5. Fix every broken or incorrect internal link: footer "Privacy Policy" and "Terms of Service"
   must point to the new pages (currently both -> faq.html), footer "Sitemap" -> sitemap.html,
   footer service links -> the correct anchors in services.html, and add blog.html to the
   navigation.
6. Make the appointment forms work: give every field in pages/contact.html a name and id, then
   in js/main.js replace the fake success-message-only handleFormSubmit with a real POST to
   FORM_ENDPOINT (Formspree / Google Apps Script URL) defined in a single CONFIG object at the
   top of the file. If FORM_ENDPOINT is empty, fall back to opening a prefilled wa.me link with
   the hospital WhatsApp number. Add inline validation, a button loading state, an
   aria-live="polite" success message and a redirect to thank-you.html.
7. Replace the fake map placeholder with a real Google Maps iframe embed, keeping the
   "Get Directions" link.
8. Add js/data.js with the hospital constants (name, phone, whatsapp, email, address, hours,
   social links) and use consistent values in every page header/footer. Guard every
   addEventListener target (menuToggle, backToTop, whatsappFloat) so a page missing an element
   can never throw and break all JS.
9. SEO: add canonical, Open Graph + Twitter tags and matching JSON-LD to every page (Hospital on
   the home page, FAQPage on faq.html, BreadcrumbList on inner pages); create sitemap.xml
   listing all pages; fix robots.txt to point to
   https://www.sivamedhospital.com/sitemap.xml
10. Accessibility: actually call the already-written createSkipLink() helper, add <label>s to
    form fields, aria-expanded on the mobile menu toggle and FAQ accordions, focus-visible
    styles, keyboard support for the lightbox (Esc to close, arrow keys to navigate) and alt
    text on every image.
11. Performance: add loading="lazy", width/height and decoding="async" to images, defer
    js/main.js, and remove unused CSS blocks.

DEFINITION OF DONE
- Serve index.html with VS Code Live Server (port 5503 is already configured): no console
  errors, no 404s in the Network tab, all nav links work, forms validate and submit (or fall
  back to WhatsApp).
- Every page shares an identical nav/footer/floating buttons; no placeholder text remains
  ("Doctor Name", "123 Medical Center Drive", "+1 (555)", "Sunshine Pediatric").
- Report: files created/modified/deleted, remaining placeholders needing real hospital data,
  and anything intentionally skipped.
```

---

## PROMPT 3 — Presentation Prompt (slides + demo script + viva answers)

```text
ROLE
You are preparing a college/portfolio project presentation for a hospital website I built
("Sivamed Multispeciality Hospital", Pollachi). Read PROJECT-ANALYSIS.md and BUILD-PROMPT.md
in this folder first, then inspect the code in src/ (React 18 + Vite 5 + Tailwind 3 + Framer
Motion + React Router 6 + React Helmet Async) and the static site (index.html + css/style.css
+ js/main.js, moved to legacy/ once the React build is wired up).

DELIVERABLE
Produce a complete, ready-to-copy presentation pack in one markdown file named
PRESENTATION.md with exactly these sections:

1. Title slide text and a 120-word abstract.
2. Problem statement (3 bullets: patients search online; the hospital has 19 years of offline
   trust but no online booking, no department discovery, no doctor credibility online).
3. Objectives (5 bullets) and Scope (in scope / out of scope).
4. Technology review: a short comparison table of "Static HTML site" vs "React SPA" vs
   "Next.js", and why React + Vite was chosen.
5. System architecture: an ASCII diagram (User/Browser -> Router -> Lazy pages -> Components ->
   Data files; Helmet for SEO; form endpoint -> email/WhatsApp; admin demo mode) plus a table of
   the folder structure with a one-line purpose for every folder/file.
6. Module description + a table of every route (path, component, purpose, key features) pulled
   from the real src/App.jsx, and note the gaps listed in PROJECT-ANALYSIS.md.
7. Technology stack table: name, version, why it is used (read the real versions from
   package.json).
8. Backend/database design: state clearly that the current build is front-end only, then propose
   a Firebase/Supabase schema (tables: appointments, enquiries, doctors, departments, blogs,
   testimonials, gallery, admin_users) with columns, types and relationships.
9. Screenshots checklist: exactly which screens to capture, in which order, at 1440px and 375px
   (Home hero, departments grid, department detail, doctor profile, appointment form with
   validation errors, success/thank-you page, blog list, blog post, FAQ, gallery lightbox,
   mobile menu open, admin dashboard, 404).
10. A 6-8 minute live demo script: what to click, what to say, and 3 "wow" moments.
11. Testing table: ID, description, steps, expected result, actual result, status - at least 15
    cases covering navigation, forms, validation, responsiveness, accessibility and the 404 route.
12. Results/performance: what to measure (Lighthouse mobile + desktop, page weight, first load
    time, per-route bundle sizes from `npm run build`) and a before/after table to fill in.
13. Limitations and Future scope (Tamil toggle, online payment, real backend/admin auth, patient
    portal, lab report download, ambulance tracking, PWA install).
14. Twelve likely viva questions with concise model answers, including: "Why React over plain
    HTML?", "How does SEO work in an SPA and how did you fix it?", "How is the appointment form
    handled?", "Is the admin secure?", "How is the site responsive?", "What did you test?",
    "Where is the hospital data stored?", "What would you do differently?"
15. A one-page abstract/synopsis for the front matter of the project report.

RULES
- Use only facts that exist in the code. Mark anything still placeholder (phone numbers, email,
  doctor names, the 3.8/5 rating) as "to be confirmed with the hospital".
- Do not invent performance numbers; leave blanks like "__ ms" / "__ / 100" to fill in after
  running the measurement commands.
- Keep it copy-paste friendly for slides: short bullets, no long paragraphs, tables where useful.
```

---

## PROMPT 4 — Small surgical prompts (one task each)

**4a. Fix the critical "React never mounts" bug**
```text
In c:\Users\ELCOT\Desktop\Hospital-website\Hospital-website, index.html is a static hospital
page that loads css/style.css and js/main.js, so the React app in src/ never mounts and
`npm run build` would emit a broken site. Rewrite index.html as a pure Vite React entry: keep
the existing head metadata (description, keywords, OG/Twitter, theme-color, favicon, Google
Fonts preconnect + Inter/Playfair Display stylesheet, Hospital JSON-LD), then add
<div id="root"></div> and <script type="module" src="/src/main.jsx"></script> before
</body>, and remove all the static markup, the emergency banner, the css/style.css link and
the js/main.js script. Move the previous static files (pages/, css/, js/) into legacy/ so
nothing is lost. Then run `npm run build` and confirm dist/index.html references the built
React bundle, and that the dev server renders the React Home page.
```

**4b. Rebrand the whole React app in one pass**
```text
In c:\Users\ELCOT\Desktop\Hospital-website\Hospital-website, the React app in src/ is branded
as a US dental clinic ("Premium Periodontist", 123 Medical Center Drive New York,
+1 (555) 123-4567, info@periodontistclinic.com, wa.me/15551234567, "Sarah Johnson",
"Dr. James Mitchell"). Rebrand it fully to Sivamed Multispeciality Hospital, Pollachi: create
src/data/hospital.js as the single source of truth (name, tagline, address "No.146/2, Near
Kousalya Hospital, Bharathi Street, Mahalingapuram, Pollachi - 642002, Tamil Nadu", phone and
WhatsApp as REPLACE_WITH_REAL_* placeholders, email info@sivamedhospital.com, hours Emergency
24/7 + OPD Mon-Sat 8AM-9PM + Sunday 9AM-5PM, 19+ years, domain https://www.sivamedhospital.com)
and import it in Navbar, Footer, WhatsAppButton and every page. Update all <title> tags, Helmet
descriptions and schema to the hospital, delete src/pages/DentalImplants.jsx and
src/pages/GumDisease.jsx with their routes and links, replace the dental service content with
the hospital's 14 departments, and replace the fake testimonials/blog authors with clearly
marked placeholders for the hospital to approve. Report every file changed and every remaining
placeholder.
```

**4c. Make the appointment form actually work**
```text
In c:\Users\ELCOT\Desktop\Hospital-website\Hospital-website, the booking form
(src/pages/Contact.jsx and the Home hero) only calls setSubmitted(true) and sends nothing.
Extract it into src/components/AppointmentForm.jsx and make it real: POST JSON to
import.meta.env.VITE_APPOINTMENT_ENDPOINT, show a loading state and inline validation errors,
include a honeypot field, add aria-live="polite" on success, and navigate to
/appointment/success. If VITE_APPOINTMENT_ENDPOINT is not set, fall back to opening a prefilled
wa.me link using the hospital WhatsApp number from src/data/hospital.js and tell the user that
WhatsApp was opened. Add .env.example and document the variable in README.md.
```

**4d. Generate the SEO layer**
```text
In c:\Users\ELCOT\Desktop\Hospital-website\Hospital-website, add the full SEO layer for
https://www.sivamedhospital.com: (1) src/components/Seo.jsx wrapping react-helmet-async that
emits title, description, canonical, og:title/description/image/url, twitter:card/title/
description/image and optional JSON-LD; (2) use it on every page with the correct schema type
(Hospital/MedicalClinic on Home, Physician on doctor profiles, MedicalWebPage on department
pages, FAQPage on FAQ, BlogPosting on blog posts, BreadcrumbList on inner pages); (3) create
public/sitemap.xml for every public route including department, doctor and blog slugs;
(4) rewrite public/robots.txt (allow all, disallow /admin, sitemap URL above); (5) remove the
leftover dental schema from index.html. Then run `npm run build` and print the final head tags
of the built index.html so I can verify.
```

**4e. Delete the junk and set the repo up properly**
```text
In c:\Users\ELCOT\Desktop\Hospital-website\Hospital-website, delete the leftover scraped junk
files temp_drive.html, temp_link.html and justdial_temp.html. Add a .gitignore covering
node_modules/, dist/, .env, .env.local and .DS_Store. Add a README.md documenting the project
purpose, stack, folder structure, the commands `npm install` / `npm run dev` / `npm run build`,
the required environment variables, where to change hospital details (src/data/hospital.js),
how to add a department/doctor/blog post, and how to deploy to Netlify or Vercel with SPA
redirects. Update package.json (name, description, keywords) away from "periodontist-website"
and remove the unused @heroicons/react dependency. Then run `git init` and make an initial
commit.
```

**4f. Quick pre-presentation sanity check (run this last, before your demo)**
```text
Audit c:\Users\ELCOT\Desktop\Hospital-website\Hospital-website for a presentation and report
a pass/fail table for: (1) every occurrence of the strings "Periodontist", "New York",
"+1 (555)", "Sarah Johnson", "Michael Chen", "Dr. James Mitchell", "Doctor Name",
"Sunshine Pediatric", "3.8/5" - list file and line for each; (2) every reference to an image or
asset file that does not exist on disk (broken links); (3) every internal link/route that does
not resolve to an existing page or React route; (4) every form handler that does not send data
anywhere; (5) every page missing a <title> or meta description; (6) every interactive element
that is a clickable div instead of a button/link. Do not change any files in this task - just
report the findings with exact file paths and line numbers, ordered by severity.
```

