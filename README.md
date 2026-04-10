# ESO Trait Tracker — Progressive Web App

A mobile-first trait research tracker for **The Elder Scrolls Online**, built as a Progressive Web App (PWA) that works offline and can be installed on your iPhone home screen.

---

## 📁 Project Structure

```
esott-pwa/
├── index.html          # Main app (HTML + CSS + JS)
├── manifest.json       # PWA manifest (app metadata, icons, theme)
├── sw.js               # Service worker (offline caching)
├── README.md           # This file
└── icons/              # App icons for various devices
    ├── icon-72x72.png
    ├── icon-96x96.png
    ├── icon-128x128.png
    ├── icon-144x144.png
    ├── icon-152x152.png   (iPad)
    ├── icon-167x167.png   (iPad Pro)
    ├── icon-180x180.png   (iPhone - apple-touch-icon)
    ├── icon-192x192.png   (Android / Standard PWA)
    ├── icon-384x384.png
    └── icon-512x512.png   (Standard PWA / Splash)
```

---

## 📱 Installing on iPhone (Add to Home Screen)

### Step-by-step:

1. **Open Safari** on your iPhone (this must be Safari — Chrome/Firefox on iOS don't support PWA installation)
2. **Navigate** to the URL where the app is hosted
3. Tap the **Share button** (the square with an upward arrow, at the bottom of the screen)
4. Scroll down in the share sheet and tap **"Add to Home Screen"**
5. Optionally edit the name (default: "ESO Traits")
6. Tap **"Add"** in the top-right corner
7. The app icon will appear on your home screen!

### After installation:
- The app launches in **standalone mode** (no Safari UI — looks like a native app)
- It works **fully offline** — all assets are cached by the service worker
- Your data is stored in **localStorage** and persists between sessions
- Use **Import/Export** buttons to back up your data as JSON files

---

## 🖥️ Hosting Options

To install as a PWA, the app must be served over **HTTPS** (or localhost for testing). Options:

### Local Testing
```bash
# Python 3
cd esott-pwa
python3 -m http.server 8080
# Then open http://localhost:8080 in your browser
```

### Free Hosting Services
- **GitHub Pages** — Push to a GitHub repo, enable Pages in settings
- **Netlify** — Drag and drop the `esott-pwa` folder at netlify.com/drop
- **Vercel** — Connect a GitHub repo or use `vercel` CLI
- **Cloudflare Pages** — Free static hosting with automatic HTTPS

### Important Notes
- PWA installation requires **HTTPS** (except localhost)
- Safari on iOS is the **only browser** that supports Add to Home Screen
- Data is stored per-origin in localStorage — different URLs = different data

---

## 🔄 Updating the App

When you update the hosted files:
1. Increment the `CACHE_NAME` version in `sw.js` (e.g., `esott-pwa-v2`)
2. The service worker will automatically detect the change
3. Old caches will be cleaned up on the next visit
4. Users may need to close and reopen the app to see updates

---

## ✨ Features

- Track trait research for unlimited characters
- 20 gear slots × 9 traits each = 180 traits per character
- Tap to mark traits as known, long-press for bank tracking
- Progress statistics per character and per gear piece
- Import/Export data as JSON for backup and transfer
- Fully offline capable
- Elder Scrolls aesthetic with gold-on-dark parchment theme
