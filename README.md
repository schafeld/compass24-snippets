# compass24-snippets

Code snippets for Compass24

E.g. for A/B-Testing or personalization.

Contents:

- [./banner-tests](./banner-tests) : HTML, JS, and CSS injection payloads for banners. Experiments with Shopware context.
- [./banner/2006-01--preis-offensive](/banner/2026-01--preis-offensive) : multi-language modal-banner, vanilla JS, accessible, json-configurable
- [./templates-newsletter](./templates-newsletter) : project to create new templates for email newsletters
- t.b.c.

The code is currently being injected on the Shopware 6.7 stage through the [C24 - Simple AB Testing plugin](https://compass.k24z44.meinserver.io/admin#/sw/extension/config/C24SimpleABTesting).

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
