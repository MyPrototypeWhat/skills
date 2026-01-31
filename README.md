# Skills

A collection of AI agent skills 

## Available Skills

| Skill | Description |
|-------|-------------|
| [paperize](./paperize/) | E-ink & low-power device CSS optimizer |

---

## Paperize

> Transform web UI into e-ink optimized interfaces

**Triggers:** "paperize", "e-ink friendly", "optimize for e-ink", "Kindle-friendly", "low-power display"

**What it does:**

| Rule | Name | Action |
|------|------|--------|
| A | Grayscale | Convert colors to `gray-*` scale, remove shadows & gradients |
| B | No-Motion | Remove animations, transitions; replace scroll with pagination |
| C | Typography | Increase font weight, letter-spacing, minimum sizes |
| D | Tap Over Drag | Replace drag interactions with tap-based alternatives |
| E | Border Emphasis | Add explicit borders for visual hierarchy |

**Includes:**
- 5 optimization rules with Tailwind mappings
- Detection strategies (CSS media queries, JavaScript, user toggle)
- Tailwind preset for v3 and v4
- `paper:` variant plugin for conditional styles

**Files:**
- `SKILL.md` — Main skill instructions (372 lines)
- `tailwind-preset.md` — Optional Tailwind configuration (127 lines)

---

## License

See [LICENSE](./LICENSE)
