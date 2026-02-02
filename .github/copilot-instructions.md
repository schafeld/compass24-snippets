# GitHub Copilot Workspace Instructions

## Email Newsletter Development Guidelines

**CRITICAL**: All HTML email newsletter development in this workspace MUST follow the comprehensive guidelines defined in:
`/templates-newsletter/AI-GUIDELINES-NEWSLETTER-CREATION.md`

### Automatic Validation Rules

When working with any HTML files in `/templates-newsletter/` directory:

1. **ALWAYS verify compatibility** before suggesting or implementing changes
2. **WARN immediately** if any of the following violations are detected:
   - CSS Grid or Flexbox used for main structure
   - External CSS or JavaScript references
   - Missing inline styles on critical elements
   - `<button>` elements instead of bulletproof table-based buttons
   - `<div>`-based layouts instead of tables
   - CSS filters (limited email client support)
   - Icon fonts instead of images
   - Animated SVG (poor email support)
   - Direct video embedding
   - Missing `alt` text on images
   - Missing `width`/`height` attributes on images
   - Color contrast below WCAG AA (4.5:1)
   - Font sizes below 14px for body text
   - Touch targets below 44x44px
   - Missing `role="presentation"` on layout tables
   - Base64-encoded images
   - External font loading without fallbacks
   - Missing preheader text
   - Missing unsubscribe link

3. **Best Practice Checklist** - Verify before completing any newsletter task:
   - ✅ Table-based layout with inline CSS
   - ✅ Responsive media queries for mobile
   - ✅ Dark mode support via `prefers-color-scheme`
   - ✅ All images hosted on CDN with descriptive alt text
   - ✅ Bulletproof buttons (table-based)
   - ✅ Total email size under 100KB
   - ✅ Web-safe font stack with fallbacks
   - ✅ WCAG AA color contrast compliance
   - ✅ Outlook-compatible VML for complex features
   - ✅ Mobile-first responsive design

4. **Automatic Recommendations**:
   - When SVG is used, always suggest PNG fallback
   - When background images are used, provide VML for Outlook
   - When custom fonts are referenced, ensure web-safe fallbacks
   - When colors are defined, verify WCAG contrast ratios
   - When GIFs are used, ensure first frame conveys full message

### File Scope
These rules apply to all files matching:
- `templates-newsletter/**/*.html`
- `templates-newsletter/**/*.htm`
- Any HTML email template in the workspace

### Enforcement Level
**STRICT** - Reject or warn about any code that violates email newsletter best practices. Always reference the specific guideline section when flagging issues.

### Quick Reference Links
- Full Guidelines: `/templates-newsletter/AI-GUIDELINES-NEWSLETTER-CREATION.md`
- Technical Do's/Don'ts: Lines 45-115
- Layout Best Practices: Lines 117-195
- Media Recommendations: Lines 197-345
- Usability Guidelines: Lines 347-550
