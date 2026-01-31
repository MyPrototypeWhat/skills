# Tailwind Preset for Paperize

Optional Tailwind configuration to enforce e-ink constraints at the framework level.

> **Note:** This preset is optional. The Paperize skill transforms code directly without requiring this config. Use this preset if you want Tailwind to prevent generating harmful utilities project-wide.

---

## Tailwind CSS v4

Add to your main CSS file (e.g., `app.css`):

```css
@import "tailwindcss";

/* ═══════════════════════════════════════════════════════════
   Paperize: Disable harmful utilities for e-ink displays
   ═══════════════════════════════════════════════════════════ */

@theme {
  /* Rule A: Remove all shadows and drop-shadows */
  --shadow-*: initial;
  --drop-shadow-*: initial;

  /* Rule A: Remove all gradient color stops */
  /* (Tailwind v4 uses --gradient-* for gradient utilities) */

  /* Rule B: Remove all animations */
  --animate-*: initial;
}

/* Rule B: Disable transitions globally via CSS reset */
*, *::before, *::after {
  transition-property: none !important;
}
```

---

## Tailwind CSS v3

Add to `tailwind.config.js`:

```javascript
module.exports = {
  corePlugins: {
    // Rule A: No shadows or gradients
    boxShadow: false,
    boxShadowColor: false,
    gradientColorStops: false,

    // Rule B: No animations or transitions
    animation: false,
    transitionProperty: false,
    transitionDuration: false,
    transitionTimingFunction: false,
    transitionDelay: false,
  },
}
```

---

## What This Preset Does

| Disabled Utility | Rule | Reason |
|------------------|------|--------|
| `shadow-*` | A | Shadows render as dirty blobs on e-ink |
| `from-*`, `via-*`, `to-*` | A | Gradients become unpredictable muddy tones |
| `animate-*` | B | Animations cause painful flickering |
| `transition-*` | B | Transitions are imperceptible on slow refresh |
| `duration-*` | B | No point without transitions |

---

## What This Preset Does NOT Do

The following are handled by the Paperize skill during transformation, not by this preset:

| Concern | Handled By |
|---------|------------|
| Color → Grayscale conversion | Skill (Rule A) |
| Font weight increases | Skill (Rule C) |
| Letter-spacing adjustments | Skill (Rule C) |
| Drag → Tap refactoring | Skill (Rule D) |
| Border emphasis | Skill (Rule E) |

---

## Recommended Grayscale Palette

Use Tailwind's native `gray-*` scale. No custom colors needed.

| Use Case | Recommended Class |
|----------|-------------------|
| Background | `bg-white` or `bg-gray-50` |
| Alternate background | `bg-gray-100` |
| Subtle border | `border-gray-300` |
| Secondary text | `text-gray-500` |
| Body text | `text-gray-700` |
| Headings / emphasis | `text-gray-900` or `text-black` |

---

## Example: Card Without Custom Classes

No need for `.paper-card`. Compose with utilities:

```jsx
{/* Primary card */}
<div className="bg-white border-2 border-black p-6 mb-4">
  <h2 className="text-black font-bold">Title</h2>
  <p className="text-gray-700">Content</p>
</div>

{/* Secondary card */}
<div className="bg-white border border-gray-500 p-6 mb-4">
  <h2 className="text-gray-900 font-semibold">Title</h2>
  <p className="text-gray-600">Content</p>
</div>

{/* Subtle card */}
<div className="bg-gray-50 border border-gray-300 p-6 mb-4">
  <p className="text-gray-700">Background info</p>
</div>
```
