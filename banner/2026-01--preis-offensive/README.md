# Preis-Offensive Banner (January 2026)

A promotional overlay banner for the Compass Preis-Offensive campaign with multi-language support.

## Overview

This banner is designed to be injected into pages via a personalization platform. It displays a fixed-position promotional banner with language-specific images and links.

## Files

| File | Description |
|------|-------------|
| `basic-leaderboard-modal.html` | Complete banner code (CSS, HTML, JS) |
| `assets/` | Banner image assets per language |

## Features

- **Multi-language support**: 10 languages (de, dk, es, fr, ch-fr, gb, it, nl, pl, se)
- **Path restrictions**: Show banner only on specific paths (or all paths)
- **Session persistence**: Remembers if user closed the banner
- **Debug mode**: Console logging for development/testing
- **Global API**: Accessible via browser console for testing
- **Safe injection**: Uses specific IDs to avoid conflicts with page elements

## Configuration

The banner is configured via `BANNER_CONFIG` object in the script:

```javascript
const BANNER_CONFIG = {
    position: 'bottom',           // 'top' or 'bottom'
    language: 'de',               // Language code for content
    allowedPaths: [],             // Empty = all paths, or ['/path1', '/path2']
    DEBUG: true                   // Enable console logging
};
```

### Configuration Options

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `position` | string | `'bottom'` | Banner position: `'top'` or `'bottom'` |
| `language` | string | `'de'` | Language code for images/links |
| `allowedPaths` | array | `[]` | Paths where banner shows. Empty = all paths |
| `storageKey` | string | `'bannerClosed_preisOffensive_2026-01'` | sessionStorage key |
| `DEBUG` | boolean | `true` | Enable console debug logging |

# Preis-Offensive Banner (January 2026)

A promotional overlay banner for the Compass Preis-Offensive campaign with multi-language support.

## Overview

This banner is designed to be injected into pages via a personalization platform. It displays a fixed-position promotional banner with language-specific images and links.

## Files

| File | Description |
|------|-------------|
| `basic-leaderboard-modal.html` | Complete banner code (CSS, HTML, JS) |
| `assets/` | Banner image assets per language |

## Key Features

- Multi-language support (de, dk, es, fr, ch-fr, gb, it, nl, pl, se)
- Path restrictions (show only on configured paths)
- Persistent closed state using `localStorage`
- Session display control using `sessionStorage.bannerSeen` (banner shows once per session)
- Configurable delay before display (`BANNER_CONFIG.delay`, default 5000ms)
- Responsive images with `srcset`, `sizes`, and `loading="lazy"`
- Global API for debugging: `window.PreisOffensiveBanner`

## Configuration

The banner is configured via the `BANNER_CONFIG` object in the script.

```javascript
const BANNER_CONFIG = {
    position: 'bottom',                     // 'top' or 'bottom'
    language: 'de',                         // Language code for content
    allowedPaths: [],                       // Empty = all paths
    storageKey: 'bannerClosed_preisOffensive_2026-01', // localStorage key for closed state
    DEBUG: true,                            // Enable console logging (set false in prod)
    delay: 5000                             // Delay in ms before showing banner
};
```

## Supported Languages

| Code | Language | Link URL |
|------|----------|----------|
| `de` | German | `/compass-preisoffensive` |
| `dk` | Danish | `/pris-offensiv` |
| `es` | Spanish | `/ofensiva-de-precios` |
| `fr` | French | `/offensive-sur-les-prix` |
| `ch-fr` | Swiss French | `/ch-fr/offensive-sur-les-prix` |
| `ch-de` | Swiss German | `/compass-preisoffensive` |
| `gb` | English (UK) | `/price-offensive` |
| `it` | Italian | `/offensiva-sui-prezzi` |
| `nl` | Dutch | `/prijs-offensief` |
| `pl` | Polish | `/ofensywa-cenowa` |
| `se` | Swedish | `/pris-offensiv` |

## Deployment

1. Set `BANNER_CONFIG` values to match the deployment channel (language, position, allowedPaths).
2. Set `DEBUG: false` for production.
3. Inject `basic-leaderboard-modal.html` through the personalization platform or include it in your page template.
4. If you serve a minified variant, ensure comments are removed or converted to `/* ... */`.
5. Clear cache after deployment if necessary.

## Responsive Images

The banner uses language-specific `imageSrc` URLs in `BANNER_CONFIG.data`. Images are requested at different widths by appending a `width=` query parameter to the image URL. The script sets `srcset`, `sizes`, and `loading="lazy"` for the banner image to improve network and rendering performance.

Recommendations and behavior:

- `imageSrc` should point to an origin that supports dynamic resizing via a `width` query parameter (the script expects `?width=...` or `&width=...`).
- The script builds a `srcset` with common breakpoints (480w, 768w, 1200w, 1920w). You can customize those in the script if needed.
- `sizes` is set to: `(max-width: 480px) 90vw, (max-width: 768px) 95vw, 350px` — adjust to match your layout.
- `loading="lazy"` is applied to avoid loading the banner image until it's near the viewport.
- Example generated `srcset` entry:

```
https://.../image.jpg?width=480 480w, https://.../image.jpg?width=768 768w, https://.../image.jpg?width=1200 1200w
```

If your image CDN uses a different parameter for resizing, update the helper `getSrcWithWidth()` in the script accordingly.

## Console API / Debugging

Use the global `PreisOffensiveBanner` object in the console to inspect and control the banner during development.

```javascript
// Access configuration
PreisOffensiveBanner.config

// Close and persist preference
PreisOffensiveBanner.close()

// Reset stored preferences (clears localStorage and sessionStorage)
PreisOffensiveBanner.reset()

// Change language and reinitialize
PreisOffensiveBanner.setLanguage('fr')

// Manual init
PreisOffensiveBanner.init()
```

### API Reference

| Method/Property | Description |
|-----------------|-------------|
| `.config` | Access the full `BANNER_CONFIG` object |
| `.init()` | Initialize and display the banner |
| `.close()` | Close the banner and save preference to `localStorage` |
| `.reset()` | Clear the closed state from `localStorage` and session (`sessionStorage.bannerSeen`) |
| `.setLanguage(code)` | Switch language and reinitialize (e.g., `'pl'`, `'fr'`) |
| `.isPathAllowed()` | Check if current path matches `allowedPaths` |
| `.getLanguageData()` | Get the current language's image/link configuration |

## Element IDs

| ID | Element |
|----|---------|
| `overlayBanner-preisOffensive-2026-01` | Banner container |
| `overlayBanner-link-preisOffensive-2026-01` | Anchor tag |
| `overlayBanner-image-preisOffensive-2026-01` | Image element |

## Developer Notes

- Avoid single-line `//` comments in the production script; minifiers or inline serving can break if comments are not handled. Use `/* ... */` for multi-line comments when possible.
- If your CDN or image origin does not support `width=` querying, adapt `getSrcWithWidth()` in the script to match your resizing parameter.
- Test in staging (and private browsing) — storage APIs may be restricted in some browsers.

---

Last updated: 2026-01-21

## Accessibility

- The banner includes ARIA labeling and a polite announcement region to help screen reader users discover the content when it appears.
- The close control is implemented as a semantic `<button>` with `aria-label` and visible focus styles. It supports keyboard activation and the Escape key closes the banner.
- The image includes `width` and `height` attributes to reduce layout shift (CLS) and `alt` text is set per language.
- Animations respect the user's `prefers-reduced-motion` setting and are disabled when the preference is set to `reduce`.
- Focus is returned to the previously focused element when the banner is closed to avoid losing keyboard context.

If you want stricter behavior (e.g., focus trap / modal), we can convert this to a fully modal dialog with `aria-modal` and more rigorous focus management.
