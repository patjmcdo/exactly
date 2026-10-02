# EXACTLY — Stop the clock. Exactly.

A daily 5-round timing game. Tap to start, tap to stop. After one second the clock goes **blind** — stop it on the target. Everyone in the world gets the same 5 targets each day. Share your emoji grid, keep your streak.

Zero dependencies. Zero build step. One HTML file + a PWA shell. Installs to any iPhone / Android home screen.

## Run locally

```sh
python3 -m http.server 4173
# open http://localhost:4173 — or your LAN IP on your phone
```

## Deploy (pick one, ~10 seconds)

- **Netlify**: drag this folder onto https://app.netlify.com/drop
- **Vercel**: `npx vercel --prod`
- **GitHub Pages**: push, then Settings → Pages → branch `main` / root
- **Cloudflare Pages**: `npx wrangler pages deploy .`

HTTPS is required for the service worker + install prompt (all of the above provide it).

## Ship to the app stores (when ready)

- Fastest: https://www.pwabuilder.com — paste the deployed URL, download store-ready iOS/Android packages.
- Native wrapper: `npm i -D @capacitor/cli @capacitor/core && npx cap init exactly com.yourname.exactly --web-dir . && npx cap add ios && npx cap add android`

## Why this can make money

The Wordle playbook: daily puzzle → one shared result grid → streak anxiety → habit. Wordle was a single web page with no backend and sold to the NYT for 7 figures. Monetization paths, in order of effort:

1. **Interstitial / rewarded ads** between practice rounds (AdSense for web, AdMob via Capacitor).
2. **EXACTLY Pro** ($2.99 one-time): unlimited practice stats, archive of past dailies, themes, no ads.
3. **Acquisition**: the daily-share mechanic is what buyers pay for.

## Files

- `index.html` — the whole game (UI, timing engine, daily seed, audio, haptics, share, stats)
- `manifest.webmanifest`, `sw.js`, `icon.svg`, `icon-512.png` — PWA install + offline
