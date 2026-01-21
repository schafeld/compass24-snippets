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

### Supported Languages

| Code | Language | Link URL |
|------|----------|----------|
| `de` | German | `/compass-preisoffensive` |
| `dk` | Danish | `/pris-offensiv` |
| `es` | Spanish | `/ofensiva-de-precios` |
| `fr` | French | `/offensive-sur-les-prix` |
| `ch-fr` | Swiss French | `/ch-fr/offensive-sur-les-prix` |
| `gb` | English (UK) | `/price-offensive` |
| `it` | Italian | `/offensiva-sui-prezzi` |
| `nl` | Dutch | `/prijs-offensief` |
| `pl` | Polish | `/ofensywa-cenowa` |
| `se` | Swedish | `/pris-offensiv` |

## Deployment
## Features

- **Multi-language support**: 10 languages (de, dk, es, fr, ch-fr, gb, it, nl, pl, se)
- **Path restrictions**: Show banner only on specific paths (or all paths)
- **Persistent closed state**: Remembers if user closed the banner (uses `localStorage`)
- **Session display control**: Banner is only shown once per session, even if not closed (uses `sessionStorage` with key `bannerSeen`)
- **Configurable delay**: Banner appears after a configurable delay (default: 5 seconds, see `BANNER_CONFIG.delay`)
- **Reduced size**: Banner is about half the previous size for desktop and mobile
- **Debug mode**: Console logging for development/testing
- **Global API**: Accessible via browser console for testing
- **Safe injection**: Uses specific IDs to avoid conflicts with page elements
4. Set `DEBUG: false` for production

```javascript
const BANNER_CONFIG = {
    position: 'bottom',           // 'top' or 'bottom'
    language: 'de',               // Language code for content
    allowedPaths: [],             // Empty = all paths, or ['/path1', '/path2']
    storageKey: 'bannerClosed_preisOffensive_2026-01', // localStorage key for closed state
    DEBUG: true,                  // Enable console logging
    delay: 5000                   // Delay in ms before showing banner
};
```
5. Inject via personalization platform

## Console API

The global `PreisOffensiveBanner` object is always available for testing and debugging. Console logging only appears when `DEBUG: true`.

> **Note**: The API uses a campaign-specific name (`PreisOffensiveBanner`) rather than generic names like `closeBanner` to avoid conflicts when multiple banner scripts are active on the same page.

```javascript
// Access configuration
| Desktop (>768px) | 350×87px |
| Mobile (≤768px) | 175×43px |
PreisOffensiveBanner.config

| `.close()` | Close the banner and save preference to localStorage |
| `.reset()` | Clear the closed state from localStorage |
// Manually show/hide
## Safety Features

- **IIFE wrapper**: Script runs in isolated scope, no global pollution except explicit API
- **Null checks**: All DOM operations check for element existence
- **Try/catch**: localStorage/sessionStorage operations wrapped for private browsing compatibility
- **Specific IDs**: No generic class selectors that could conflict with page styles
- **Session display control**: Banner is only shown once per session, even if not closed (uses `sessionStorage` with key `bannerSeen`)
PreisOffensiveBanner.reset()

// Switch language and reinitialize
PreisOffensiveBanner.setLanguage('fr')

// Check path restrictions
PreisOffensiveBanner.isPathAllowed()

// Get current language data
PreisOffensiveBanner.getLanguageData()
```

### API Reference

| Method/Property | Description |
|-----------------|-------------|
| `.config` | Access the full `BANNER_CONFIG` object |
| `.init()` | Initialize and display the banner |
| `.close()` | Close the banner and save preference to sessionStorage |
| `.reset()` | Clear the closed state from sessionStorage |
| `.setLanguage(code)` | Switch language and reinitialize (e.g., `'pl'`, `'fr'`) |
| `.isPathAllowed()` | Check if current path matches `allowedPaths` |
| `.getLanguageData()` | Get the current language's image/link configuration |

### Debug Logging

When `DEBUG: true`, all banner operations are logged to the console with the prefix:
```
[Banner:basic-leaderboard-modal--preis-offensive-2026-01]
```

Set `DEBUG: false` for production to silence all console output.

## Element IDs

The banner uses specific, namespaced IDs to avoid conflicts:

| ID | Element |
|----|---------|
| `overlayBanner-preisOffensive-2026-01` | Banner container |
| `overlayBanner-link-preisOffensive-2026-01` | Anchor tag |
| `overlayBanner-image-preisOffensive-2026-01` | Image element |

## Responsive Design

| Viewport | Banner Size |
|----------|-------------|
| Desktop (>768px) | 700×175px |
| Mobile (≤768px) | 350×86px |

## Safety Features

- **IIFE wrapper**: Script runs in isolated scope, no global pollution except explicit API
- **Null checks**: All DOM operations check for element existence
- **Try/catch**: sessionStorage operations wrapped for private browsing compatibility
- **Specific IDs**: No generic class selectors that could conflict with page styles

## Developer Notes

**Important:** Do NOT use single line comments `//` in JavaScript on Prod. Use multi-line comments `/* */`. Minification will otherwise render the script useless.

Probably [cache deletion ("Cache löschen")](https://www.compass24.de/admin#/sw/settings/cache/index) required to see updated script payload.
