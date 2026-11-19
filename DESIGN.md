# DESIGN.md — Albert Simel / Portfolio

**Aesthetic direction:** Tactile Editorial & Kinetic Studio (inspired by sofaknows.com).
Bold Swiss-editorial typography, high-contrast surfaces, playful magnetic micro-interactions,
smooth inertia scrolling, and interactive hover previews that make every scroll and click feel physical.

---

## 1. Palette

| Token | Value | Use |
| --- | --- | --- |
| `--obsidian` | `#0D0D0F` | Primary canvas (Deep Obsidian) |
| `--obsidian-2` | `#131316` | Raised panels, drawer surface |
| `--stone` | `#F4F3EF` | Warm Gallery Stone — inverse type & light blocks |
| `--coral` | `#FF4D3D` | Electric Coral / Vermilion accent |
| `--coral-deep` | `#D93A2B` | Pressed / hover-dark accent |
| `--hairline` | `rgba(255,255,255,0.12)` | `1px solid` dividers, index rules |
| `--hairline-strong` | `rgba(255,255,255,0.28)` | Active row rules |
| `--ink-60` | `rgba(244,243,239,0.6)` | Metadata, captions |
| `--ink-38` | `rgba(244,243,239,0.38)` | Disabled / index numerals |

Dark canvas by default. The Warm Gallery Stone is used for inverse surfaces: the hero focal card,
the cursor pill text, and the closing CTA block. Contrast is always type-on-obsidian or
type-on-stone; coral never carries body copy.

## 2. Typography

- **Display — Syne** (`next/font/google`: 600/700/800). Tight tracking (`-0.04em`), oversized
  clamps for hero (`clamp(3.4rem, 13vw, 12rem)`), section titles (`clamp(2.2rem, 6vw, 5rem)`).
- **Mono — JetBrains Mono** (400/500). All metadata: timestamps, coordinates, index numbers
  (`01 / 04`), status pills, tool tags, eyebrow labels.
- **Label rule:** uppercase mono at `0.68rem`, `letter-spacing: 0.22em`, preceded by a coral
  `+/` glyph. Section labels keep the original shell notation (`## WORK`, `$ ls ~/work/`).

## 3. Layout & surfaces

- 12-column editorial grid, max width `1560px`, generous side gutters (`clamp(20px, 5vw, 72px)`).
- Hairline rules frame every functional band; no rounded "card soup" except pills and the single
  hero focal card (radius 18px) and the project preview thumb (radius 14px).
- Work is an **index**, not a grid: full-width rows `01 — 04`, title left, role/tags centre, year right.
- Numbers, coordinates and status live in mono. Oversized titles break across masked lines.

## 4. Motion language

- **Spring:** `{ type: "spring", stiffness: 300, damping: 28, mass: 0.6 }` — the house spring.
- **Masked reveals:** each display line sits in `overflow-hidden`; inner span translates
  `y: 110% → 0` with `0.9s` custom ease `[0.16, 1, 0.3, 1]`, staggered `0.07s`.
- **Magnetic pull:** pointer offset × `0.22` (buttons) / `0.3` (links), spring returned on leave.
- **Cursor:** 8px dot follows instantly-ish (spring 900/40); 52px pill lags behind
  (spring 300/28), expands to auto-width with contextual label, rotates 0deg — never a spinner.
- **Hover preview:** spring-tracked thumbnail follows the cursor with `rotate` mapped from pointer
  velocity (`±9deg`) and a slight `scale` lift. Hidden on touch.
- **Drawer:** slide-over from the right, `x: 100% → 0` on the house spring, backdrop fade + blur.
  Closing reverses; body scroll locks.
- **Marquee:** velocity-sensitive — scroll velocity bends direction and speed, `useAnimationFrame`
  driven, never fully stops.
- **Accordion:** `layoutId="capHighlight"` shared coral hairline/block moves between rows.
- **Toast:** "COPIED TO CLIPBOARD ✓" springs up from the copy pill, auto-dismiss 2.4s.
- Respect `prefers-reduced-motion`: reveals become opacity-only, marquee slows, cursor disabled.

## 5. Interaction inventory

1. Spring cursor dot + contextual pill: `VIEW CASE`, `DRAG`, `SAY HI ↗`, `COPY`, `OPEN`, `SCROLL`.
2. Hero: line-masked kinetic title, live Nairobi clock, draggable tilt card cluster, magnetic CTA,
   velocity marquee.
3. Work index: hover preview, click-to-expand case drawer with stack pills + live links.
4. Capabilities accordion with shared-element highlight; bento stats block.
5. Contact: one-click email copy pill + toast, magnetic social links, oversized closing headline.

## 6. Content guardrails

All personal copy, project descriptions, stats, social URLs, email, phone and the
`© 2026 albert simel · nairobi, ke` footer are preserved from the deployed site
(https://simel-coral.vercel.app/). Only presentation changes.
