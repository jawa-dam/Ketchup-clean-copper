# Ketchup & Copper Discovery

An independent website documenting the accidental observation that ketchup may clean tarnished copper, along with experiment challenges and a community participation framework.

## Project Purpose

This site presents a first-person account of an accidental discovery: ketchup left on a copper sink for approximately 20 minutes appeared to clean the tarnished surface. The site invites visitors to try careful, documented experiments and share their results.

**This is not a scientific study.** The site clearly states that results are based on a single observation and may vary.

## Local Preview

Open `index.html` directly in a browser, or use any static file server:

```bash
# Python
python3 -m http.server 8080

# Node.js (npx)
npx serve .

# Then open http://localhost:8080
```

## File Structure

```
index.html    — Main discovery page (hero, story, videos, challenges, guide, community)
styles.css    — Self-contained design system and page styles (no external theme dependency)
README.md     — This file
images/       — (Create this directory for project images)
```

## How to Add the Social-Sharing Image

The owner has created a social-sharing image with the headline "CAN KETCHUP CLEAN COPPER?" (1200x630, bold viral thumbnail style).

1. **Upload the image** to this repository under `images/social-share.png` (or any public CDN).
2. **Open `index.html`** and find the `SOCIAL-SHARING IMAGE` comment block in `<head>`.
3. **Uncomment** the two meta tags and replace `SOCIAL_IMAGE_PENDING` with the full public URL:
   ```html
   <meta property="og:image" content="https://your-domain.com/images/social-share.png" />
   <meta name="twitter:image" content="https://your-domain.com/images/social-share.png" />
   ```
4. To also display the before-and-after photo in the story section, find the `BEFORE-AND-AFTER IMAGE` comment in the story section, uncomment the `<figure>` block, and update the `src`.

## How to Activate a Video

The site has five configurable video slots. Each starts with a "Coming Soon" placeholder.

**To publish a video:**

1. Open `index.html` and find the `VIDEO_CONFIG` object near the bottom (inside the `<script>` tag).
2. Locate the entry for the video you want to activate.
3. Change `published: false` to `published: true`.
4. Set `url` to the real, public embed URL:
   - **YouTube:** `"https://www.youtube.com/embed/VIDEO_ID"`
   - **YouTube (privacy-enhanced):** `"https://www.youtube-nocookie.com/embed/VIDEO_ID"`
   - **Direct video file:** `"https://your-host.com/path/to/video.mp4"`
5. Save and deploy.

**Example — activating the original video:**
```javascript
original: { id: "video-original", published: true, url: "https://www.youtube.com/embed/abc123XYZ", type: "youtube", title: "Original Copper Sink Observation" },
```

The page automatically:
- Replaces the "Coming Soon" placeholder with the video player.
- Updates the hero CTA from "READ THE DISCOVERY STORY" to "WATCH THE ORIGINAL EXPERIMENT" (when the original video is published).

**If a video is marked published but the URL is invalid**, the placeholder shows a red "Configuration Error" badge instead of a broken player.

### Video Slots

| Key | Title | Description |
|-----|-------|-------------|
| `original` | The Copper Sink Experiment | The firsthand discovery video |
| `penny` | Penny Demonstration | Ketchup on a tarnished penny |
| `jewelry` | Copper Jewelry Test | Testing on confirmed copper jewelry |
| `beforeafter` | Before & After | Side-by-side comparison |
| `sink` | Copper Sink Follow-Up | Controlled follow-up on the same sink |

## How to Update Social Profile Links

1. Open `index.html` and find the `kc-social-links` section.
2. Replace the `href="#"` placeholders with your real YouTube and TikTok URLs.
3. Remove the `placeholder` class and `tabindex="-1"` from each link so they become clickable:
   ```html
   <a class="kc-social-link" href="https://youtube.com/@your-channel" target="_blank" rel="noopener">
     &#9654; YouTube
   </a>
   ```

## How to Configure the Production Domain

The canonical URL and Open Graph URL currently use `DOMAIN_PENDING` as a placeholder.

1. Choose and set up your production domain (e.g., `ketchupcopper.com`, a GitHub Pages URL, or any hosting provider).
2. Open `index.html` and replace every occurrence of `https://DOMAIN_PENDING` with your actual domain:
   - `<link rel="canonical" href="...">`
   - `<meta property="og:url" content="...">`
3. Update `<meta name="theme-color">` if your hosting platform recommends a different value.

**Do not use `www.yalltoo.com`** — this is an independent project with its own domain.

## Running Checks

This is a static HTML site with no build step, no dependencies, and no test framework. To validate:

- **HTML:** Use the [W3C Markup Validator](https://validator.w3.org/) or `npx html-validate index.html`.
- **Accessibility:** Run Lighthouse in Chrome DevTools (Accessibility audit).
- **Mobile layout:** Open in Chrome DevTools device mode at 375px width and confirm no horizontal overflow.
- **Links:** Verify all `#section` links scroll to their targets.
- **Video config:** Set a video to `published: true` with a known YouTube embed URL and confirm the player renders.

## Current Limitations and Owner Actions

| Item | Status | Owner Action |
|------|--------|--------------|
| Social-sharing image | Placeholder | Upload image and update meta tags |
| Before-and-after photo (in-page) | Commented out | Upload image and uncomment the `<figure>` block |
| Videos (all 5) | Coming Soon placeholders | Set `published: true` and add URLs when ready |
| YouTube link | Placeholder | Add real channel URL |
| TikTok link | Placeholder | Add real account URL |
| Production domain | `DOMAIN_PENDING` | Choose domain and update canonical/OG URLs |
| Experiment submissions | "Coming soon" notice | Build or integrate a submission system when ready |
| Contact email | `Contact@yalltoo.com` | Update if a project-specific email is preferred |

## Design System

The site uses its own independent design tokens (defined in `styles.css`):

- **Primary brand:** Ketchup red (`#d93025`) + Copper metallic gradient
- **Accent:** Teal (`#0891b2`) — a subtle nod to YallToo's cyan, without branding dependency
- **Background:** Clean neutral (`#fafbfc`) — not the YallToo blue-tinted background
- **Typography:** Plus Jakarta Sans (loaded from Google Fonts)
- **No external theme dependency.** The site does not load `yalltoo-theme.css` or any YallToo stylesheet.
