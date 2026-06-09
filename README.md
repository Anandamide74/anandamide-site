# Anandamide Sports Solutions — Updated Site

This package contains the reviewed and updated version of your website.

## What's in this folder

```
output/
├── index.html              ← homepage (was 663 KB → now 122 KB)
├── mm2l.html               ← Move More to Learn page (was 137 KB → now 34 KB)
├── start-your-sport.html   ← Assessment funnel (was 340 KB → now 31 KB)
├── article-template.html   ← Blog article template (was 94 KB → now 19 KB)
└── assets/                 ← extracted images (logo, hero brand, photos)
    ├── img-41384de5a7.png
    ├── img-4805e8f27f.jpg
    ├── img-6f67582979.png
    ├── img-c408de4acf.jpg
    ├── img-dcd095369a.jpg
    └── img-e2e3c215ba.png
```

**Total HTML size reduction: 1,055,294 bytes (~85% smaller)**

---

## What was changed

### Performance
- All 6 large base64-encoded images extracted into separate files under `/assets/`
- Logo now loads once and is cached across all pages (was being re-downloaded on every page)
- Hero brand mark loads as a real image file
- Removed three `<meta http-equiv="Cache-Control / Pragma / Expires">` tags that were disabling browser caching
- Added `loading="lazy"` to all `<img>` tags

### SEO
- Added `<link rel="canonical">` pointing to https://www.anandamidesports.com
- Added Open Graph tags (`og:title`, `og:description`, `og:image`, `og:url`, `og:type`, `og:site_name`) — your site now generates proper previews when shared on WhatsApp, LinkedIn, Twitter, Facebook
- Added Twitter Card tags
- Added JSON-LD structured data:
  - Homepage → `Organization` schema with both addresses
  - MM2L → `Service` (Educational Programme) schema
  - Start Your Sport → `Service` with free offer schema
  - Article template → `Article` schema (marked `noindex` until you populate it)
- Added `<meta name="robots" content="index,follow">` (and `noindex,nofollow` on the article template)
- Added `<meta name="theme-color">` for mobile browser chrome
- `anandamide.org` listed as `sameAs` in the Organization schema (for CBHPP future)

### Accessibility (a11y)
- Logo now has `alt="Anandamide Sports Solutions"`
- All other `<img>` tags have `alt=""` (decorative) as a safe default — review and add descriptive alt where appropriate
- Added `:focus-visible` outline styles on all interactive elements for keyboard users
- Mobile menu has proper ARIA: `role="dialog"`, `aria-modal`, `aria-label`, `aria-expanded`, `aria-controls`

### Mobile Experience
- New hamburger menu (☰) appears on screens narrower than 900px
- Tapping it opens a full-screen overlay with all nav links
- Closes on link click, close-button click, or Escape key
- Body scroll locked while menu is open

### Security
- All `target="_blank"` external links now have `rel="noopener noreferrer"` (prevents tab-nabbing)

### Code Quality
- Removed duplicate `.hps-funnel` CSS rule
- (Note: I kept the CSS inline because each page now has unique sections — extracting to a shared external `styles.css` is a Phase 2 improvement; if you want me to do that later, just say so.)

---

## ⚠️ ONE THING YOU STILL NEED TO DO MANUALLY

The contact form and email-capture form on `index.html` still point to a Formspree placeholder. You need to:

1. Go to https://formspree.io and sign up (free tier allows 50 submissions/month)
2. Create a new form, copy the form endpoint (looks like `https://formspree.io/f/xyzabcde`)
3. Open `index.html`, find **two** occurrences of `YOUR_FORMSPREE_ID` and replace both with your real ID

Search-and-replace:
```
FIND:    https://formspree.io/f/YOUR_FORMSPREE_ID
REPLACE: https://formspree.io/f/yourrealid
```

(I marked these with a `data-todo="REPLACE-WITH-REAL-FORMSPREE-ID"` attribute so they're easy to find.)

Alternative free options if you prefer: **Getform**, **Web3Forms**, **Basin**.

---

## How to upload to your live site (www.anandamidesports.com)

Depending on where your site is hosted:

**GoDaddy / Bluehost / cPanel hosting:**
1. Log in to cPanel → File Manager
2. Navigate to `public_html/`
3. Upload all 4 `.html` files (overwrite existing)
4. Create an `assets/` folder, upload the 6 image files into it

**Netlify / Vercel / GitHub Pages:**
1. Replace the existing files in your repo
2. Commit and push — auto-deploys

**FTP / SFTP:**
1. Connect with FileZilla or similar
2. Upload all files preserving the folder structure

**Important:** Keep the folder structure exactly as it is — `assets/` must be at the same level as the HTML files.

---

## Recommended next steps (Phase 2)

1. **Add real testimonials with photos** to the homepage — your "coming soon" placeholder is a conversion drag
2. **Replace the article-template.html placeholder copy** with one real article (e.g., "MM2L for kinaesthetic learners in Ahmedabad"). Remove `noindex` once populated. Aim for one article/month — over 6 months this will meaningfully grow organic traffic.
3. **Set up the anandamide.org → CBHPP page** when ready, and link it from the main site
4. **Create an `og-image.jpg`** (1200×630px) and upload to `/assets/og-image.jpg` — this is the image that shows when your site is shared on WhatsApp/social. Right now, OG tags reference this path but the image doesn't exist yet.
5. **Add Google Search Console** to track impressions and indexing
6. **Set up a 301 redirect** from anandamide.org to anandamidesports.com (until anandamide.org has its own CBHPP content)

---

## Questions?

If anything breaks after upload, the most likely cause is the `assets/` folder being missed — double-check it's uploaded alongside the HTML files.
