# Cʀɪᴍsᴏɴ@Pᴀʀᴅᴏɴ `</>` — Portfolio & Store

A two-page static website for a Discord, website and bot developer who makes **paid bots** and **free bots**.
No build step and no dependencies to install. It is plain HTML, CSS and JavaScript.

## Pages

| File | What it is |
| --- | --- |
| `index.html` | Home page: profile, animated 3D laptop, projects, footer |
| `store.html` | Store page: Discord bot plans, coupon code, prices in ₹ and $ |

Both files must be in the **same folder**, because the Store links on the home page open `store.html`.

## Features

- Top bar with logo and name, plus a hamburger menu (Home, Dev Station, Projects, Store, Discord)
- 7 color themes (Dark, Light, Sunset, Orchid, Wine, Gold, Crimson), chosen from the menu and remembered in the browser. The store page uses the same saved theme.
- Starfield image background, with a 3D moon and planets on top (Three.js)
- 3D laptop that opens on load, floats, and spins as you scroll
- Glowing glass pill buttons
- Project cards: Minecraft Hosting, VPS Hosting, two Discord bots, Discord Support
- Store with a working coupon code

## Store plans

| Plan | Price | Approx. USD |
| --- | --- | --- |
| 1 GB Bot | ₹49 / month | $0.56 |
| 10 GB Bot | ₹129 / month | $1.47 |

### Coupon

Code `crimson` (not case sensitive) gives **10% off** all plans.

| Plan | With coupon | Approx. USD |
| --- | --- | --- |
| 1 GB Bot | ₹44.10 | $0.50 |
| 10 GB Bot | ₹116.10 | $1.32 |

## Editing guide

All store settings are in the `<script>` at the bottom of `store.html`:

```js
const COUPONS = { crimson: 10 };   // code (lowercase) : percent off
const USD_RATE = 88;               // ₹ per $1 — change to update dollar prices
```

- **Add a coupon:** add another entry, e.g. `{ crimson: 10, welcome: 5 }`.
- **Change a plan price:** edit `data-inr="49"` on the plan's `<div class="plan">`, and the visible `₹49` and `≈ $0.56` text beside it. The coupon math uses `data-inr`.
- **Add a plan:** copy one `<div class="plan" ...>` block and edit it.
- **Change Discord links:** search for `discord.gg/gtQ5j35VVt` in both files.
- **Bot invite links:** the two "Add to Discord" buttons in `index.html` use the OAuth links with `permissions=8` (Administrator). Lower the permissions if you want servers to trust the bots more.
- **Name, bio and tagline:** in `index.html`, edit the `profile-name`, `profile-tagline` and `bio` elements.

## Deploying

**Vercel**
1. Put `index.html`, `store.html` and `README.md` in a GitHub repository.
2. Import the repository on Vercel. No build command and no output folder are needed.
3. Deploy, then connect your custom domain if you have one.

**GitHub Pages / any static host:** upload the files and open `index.html`.

## Notes

- The site loads Three.js, Font Awesome and Inter from CDNs (cdnjs and Google Fonts), so it needs an internet connection to show 3D and icons.
- The logo and starfield background are embedded in the HTML files, so there are no image files to upload.
- Dollar prices are approximate and depend on `USD_RATE`.
- The coupon check runs in the browser, so it is a display discount only. Apply the real discount when you take the order on Discord.
