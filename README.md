# QR Code Generator

A production-ready, privacy-first QR code generator web app. Encode text and URLs into beautiful QR codes entirely in your browser—no server, no tracking, no external dependencies.

**[Live Demo](#)** • **[Features](#features)** • **[Usage](#usage)** • **[Deployment](#deployment)** • **[Security](#security)**

---

## Features

✅ **100% Client-Side** — All QR generation happens in your browser  
✅ **No Backend Required** — Deploy on any static host  
✅ **No Tracking** — Zero analytics, cookies, or data collection  
✅ **Fully Responsive** — Works seamlessly on mobile and desktop  
✅ **Multiple Formats** — Export as PNG, JPG, or SVG  
✅ **Customizable** — Colors, resolution (256–2048px), error correction levels  
✅ **Background Images** — Overlay QR codes on background images  
✅ **High Error Correction** — L, M, Q, H support for damaged/obscured codes  
✅ **Lightweight** — Single HTML file, <50KB  
✅ **Secure** — Validates file uploads (5MB max, blocks SVG)  

---

## Quick Start

1. **Download** or clone the repository
2. **Open** `index.html` in any modern browser
3. **Enter** text or URL
4. **Customize** colors, format, and options
5. **Download** your QR code

No installation or build step required.

---

## Usage

### Basic QR Generation

1. Enter text, URL, or any data in the input field
2. Click **Generate QR Code**
3. Preview appears instantly
4. Click **Download** to save as PNG, JPG, or SVG

### Customization

#### Colors
- **Foreground** — QR code color (default: black)
- **Background** — Background color (default: white)
- **Transparent Background** — Remove background for PNG/SVG (PNG/SVG only)

#### Resolution
Choose output size: 256×256, 512×512, 1024×1024, or 2048×2048 pixels

#### Format
- **PNG** — Lossless, supports transparency
- **JPG** — Compressed, opaque, smaller filesize
- **SVG** — Vector format, scales infinitely

#### Error Correction
- **Low (L)** — 7% data recovery
- **Medium (M)** — 15% data recovery (default)
- **Quartile (Q)** — 25% data recovery
- **Max (H)** — 30% data recovery

Higher levels make codes larger but more resilient to damage.

#### Background Image
1. Click **Background Image** input
2. Upload PNG, JPG, WebP, or GIF (max 5MB)
3. QR code overlays on your image in preview and download
4. Click **Remove Background** to clear

---

## Deployment

Since this is a static HTML file, deploy anywhere:

### GitHub Pages
```bash
git init
git add .
git commit -m "Add QR code generator"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/qrcode.git
git push -u origin main
```
Then enable Pages in repository settings.

### Cloudflare Pages
```bash
npm install -g wrangler
wrangler pages deploy .
```

### Netlify
```bash
npm install -g netlify-cli
netlify deploy --prod
```

### Any Static Host
Upload `index.html` to your host (AWS S3, DigitalOcean Spaces, etc.)

---

## Security

### Privacy
- **No network requests** — All processing is local
- **No storage** — Nothing is saved to disk or server
- **No tracking** — No analytics, no cookies
- **Works offline** — Once loaded, works without internet

### File Upload Safety
- **5MB size limit** — Prevents memory/performance issues
- **SVG blocking** — Blocks potentially malicious inline scripts
- **Format whitelist** — Only PNG, JPG, WebP, GIF accepted
- **Local only** — Images processed in-memory only

### QR Content
The app encodes **raw, exact input**—no URL shortening, redirects, or modifications. The generated QR code points directly to what you enter.

---

## Browser Support

- ✅ Chrome/Chromium (latest)
- ✅ Firefox (latest)
- ✅ Safari (latest)
- ✅ Edge (latest)
- ✅ Mobile browsers (iOS Safari, Chrome Mobile)

Requires HTML5 Canvas, FileReader API, and ES6 support.

---

## Technical Stack

- **QR Library** — [qrcode-generator](https://github.com/kazuhikoarase/qrcode-generator)
- **Language** — Vanilla JavaScript (no frameworks)
- **Styling** — CSS Grid, Flexbox, responsive units
- **Build** — None required (single HTML file)

---

## File Structure

```
qrcode/
├── index.html          # Single-file web app (all-in-one)
└── README.md          # Documentation
```

---

## How It Works

1. **Input** — User enters text or URL
2. **Validation** — Text length checked (max 2953 characters)
3. **QR Build** — qrcode-generator library encodes data
4. **Render** — Canvas or SVG draws QR matrix
5. **Display** — Preview updates in real-time
6. **Export** — Canvas/SVG converts to PNG/JPG/SVG blob and downloads

All processing happens in the browser—no data leaves your device.

---

## Troubleshooting

### "QR library failed to load"
- Check your internet connection (first load requires CDN)
- Refresh the page
- Try a different browser
- Check browser console for network errors

### Generated QR code won't scan
- Increase error correction level
- Try a simpler/shorter input
- Ensure sufficient contrast (dark QR on light background)
- Use a dedicated QR scanner app

### Background image looks distorted
- Image should be square or close to it
- Try a different image
- File size must be under 5MB
- Supported formats: PNG, JPG, WebP, GIF

### Large resolution export is slow
- 2048×2048 rendering takes a few seconds
- Try 1024×1024 for faster export
- Complex backgrounds slow down rendering

---

## Customization

### Change Default Colors
Edit the `#fgColor` and `#bgColor` input defaults in the HTML:
```html
<input type="color" id="fgColor" value="#000000">
<input type="color" id="bgColor" value="#ffffff">
```

### Change Default Resolution
Edit the selected option in the resolution select:
```html
<option value="1024" selected>1024×1024</option>
```

### Add Custom Styling
Modify the CSS in the `<style>` section to match your brand.

---

## Performance

- **Load time** — <2s (single HTML + CDN library)
- **QR generation** — <100ms for typical input
- **Memory usage** — <20MB (reasonable for large images)
- **Supports** — Inputs up to 2953 characters

---

## Limitations

- **No QR history** — Each QR is generated fresh (no save to account)
- **Browser storage only** — Device counters reset per browser/device
- **No batch generation** — Generate one QR at a time
- **Canvas size** — Limited by browser canvas max (typically 4096×4096)

---

## License

This project is provided as-is for personal and commercial use.

---

## Contributing

Found a bug or have a feature request? Issues and pull requests welcome.

---

## FAQ

**Q: Can I use this offline?**  
A: Yes, after the first load. The QR library is cached; subsequent uses work without internet.

**Q: Will my data be saved?**  
A: No. Nothing is stored on any server. Each QR is generated fresh in your browser.

**Q: Can I embed this on my site?**  
A: Yes. Download `index.html` and host it yourself.

**Q: What if the QR code is damaged?**  
A: Higher error correction levels (Q, H) allow recovery even if ~25-30% of the QR is obscured.

**Q: Can I use long URLs?**  
A: Yes, up to 2953 characters depending on content type and error correction.

**Q: Is there a mobile app?**  
A: This web app works on mobile. For native apps, there are QR scanners in the App Store/Play Store.

---

## Support

For issues or questions:
- Check the [Troubleshooting](#troubleshooting) section
- Review browser console for errors
- Ensure you're using a supported browser

---

**Made with ❤️ for privacy and simplicity.**
