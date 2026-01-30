# compass24-snippets

Code snippets for Compass24

E.g. for A/B-Testing or personalization.

## Quick Start: Hot-Reload Development

To enable instant browser refresh when editing HTML files, use the `live-server` development server:

### 1. Install Dependencies
```bash
npm install
```

### 2. Start Development Server
Choose a development command based on what you're working on:

```bash
# For newsletter templates (default)
npm run dev

# For banner components
npm run dev:banner

# For experiments
npm run dev:experimnets
```

The browser will automatically open and refresh whenever you save changes to HTML, CSS, or JS files.

### Features
- **Auto-refresh**: Changes appear instantly in the browser
- **Live CSS reloading**: No need to manually refresh
- **HTTPS support**: Useful for testing in different contexts
- **Port configurable**: Default is 8080

### How It Works
`live-server` watches all files in the directory and triggers a browser refresh when changes are detected. This is perfect for rapid development and testing of HTML email templates.

---

## Contents

- [./banner-tests](/banner-tests) : HTML, JS, and CSS injection payloads for banners. Experiments with Shopware context.
- [./banner/2006-01--preis-offensive](/banner/2026-01--preis-offensive) : multi-language modal-banner, vanilla JS, accessible, json-configurable
- [./templates-newsletter](/templates-newsletter) : project to create new templates for email newsletters
- t.b.c.

The code is currently being injected on the Shopware 6.7 stage through the [C24 - Simple AB Testing plugin](https://compass.k24z44.meinserver.io/admin#/sw/extension/config/C24SimpleABTesting).

## Development Tips

### Testing Email Templates
When developing newsletter templates:
1. Start with `npm run dev` to open the templates directory
2. Navigate to the specific template file in your browser
3. Edit the HTML file in your editor
4. Save and watch the browser refresh automatically

### Browser DevTools
- Use the **Elements Inspector** to verify HTML structure
- Use **Network tab** to check image loading
- Test **responsive design** with device emulation (mobile, tablet)

### Email Client Testing
After development:
- Test templates in actual email clients (Gmail, Outlook, Apple Mail, mobile)
- Use email testing services like [Litmus](https://www.litmus.com/) or [Email on Acid](https://www.emailonacid.com/)
- Consider dark mode rendering with CSS `@media (prefers-color-scheme: dark)` rules

## Developer Notes

It is possible to access the Shopware context via our Compass24 [C24 - Simple AB Testing plugin](https://compass.k24z44.meinserver.io/admin#/sw/extension/config/C24SimpleABTesting).

Demo code snippet:

```html
<script>

/* Make the large context json object globally available */
window.shopwareContext = {{ context | json_encode() | raw }};

let salesChannelName = window.shopwareContext.salesChannel.translated.name;

console.info('Sales Channel Name derived from Shopware context:', salesChannelName);

console.info('Locale code: ', shopwareContext.languageInfo.localeCode);
</script>

```
