# Healthcare Page Overrides - MomsCare Telekonseling Nifas

> **PROJECT:** MomsCare
> **Generated:** 2026-05-09
> **Page Type:** Healthcare / Maternal Care
> **Theme:** Soft White-Pink Healthcare

> ⚠️ **IMPORTANT:** Rules in this file **override** the Master file (`design-system/MASTER.md`).
> Enhanced for postpartum healthcare with nurturing animation system.

---

## Color Palette (Soft White-Pink Healthcare Theme)

| Role | Color | Hex | Usage |
|------|-------|-----|-------|
| Primary | Soft Coral Pink | `#F8BBD9` | Main CTAs, highlights |
| Primary Dark | Rose Pink | `#EC4899` | Hover states, emphasis |
| Primary Light | Blush Pink | `#FCE7F3` | Backgrounds, cards |
| Secondary | Soft Lavender | `#E9D5FF` | Secondary elements |
| Accent | Warm Peach | `#FED7AA` | Warnings, highlights |
| Background | Cream White | `#FFFBF7` | Page background |
| Surface | Pure White | `#FFFFFF` | Cards, modals |
| Surface Alt | Soft Rose | `#FFF5F8` | Section backgrounds |
| Text Primary | Dark Rose | `#831843` | Headings, body text |
| Text Secondary | Warm Taupe | `#7A6B5E` | Muted text, labels |
| Border | Soft Pink | `#F9D0E3` | Borders, dividers |
| Success | Soft Mint | `#A7F3D0` | Success states |
| Warning | Soft Amber | `#FDE68A` | Warning states |
| Danger | Soft Red | `#FCA5A5` | Error states |

---

## Animation System (Enhanced for Healthcare)

### Entry Animations
| Animation | Duration | Easing | Use Case |
|-----------|----------|--------|----------|
| Fade In | 400ms | ease-out | Page loads, modal opens |
| Slide Up | 500ms | ease-out | Content reveals |
| Slide Left | 400ms | ease-out | Page transitions |
| Scale In | 300ms | ease-out | Cards, buttons |
| Stagger | 100ms delay | - | List items, cards |

### Micro-interactions
| Interaction | Duration | Easing | Effect |
|-------------|----------|--------|--------|
| Hover Lift | 200ms | ease-out | translateY(-4px) + shadow |
| Button Press | 150ms | ease-in | scale(0.98) |
| Focus Ring | 150ms | ease-out | pink glow effect |
| Loading Pulse | 1.5s | ease-in-out | opacity animation |

### Custom Keyframes
```css
@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

@keyframes slideUp {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes slideLeft {
  from { opacity: 0; transform: translateX(30px); }
  to { opacity: 1; transform: translateX(0); }
}

@keyframes scaleIn {
  from { opacity: 0; transform: scale(0.95); }
  to { opacity: 1; transform: scale(1); }
}

@keyframes softPulse {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.6; }
}

@keyframes gentleFloat {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-6px); }
}

@keyframes shimmer {
  0% { background-position: -200% 0; }
  100% { background-position: 200% 0; }
}

@keyframes gentleBounce {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-8px); }
}
```

### Animation Utility Classes
```html
<!-- Entry animations -->
<div class="animate-fade-in">...</div>
<div class="animate-slide-up">...</div>
<div class="animate-slide-left">...</div>
<div class="animate-scale-in">...</div>

<!-- Staggered delays -->
<div class="animate-slide-up delay-100">...</div>
<div class="animate-slide-up delay-200">...</div>
<div class="animate-slide-up delay-300">...</div>

<!-- Hover effects -->
<button class="transition-all duration-200 hover:-translate-y-1 hover:shadow-lg">
  Hover Lift
</button>

<!-- Loading states -->
<div class="animate-shimmer bg-gradient-to-r from-pink-100 via-white to-pink-100">
  Skeleton Loading
</div>
```

---

## Typography
- **Headings:** Nunito (rounded, friendly, weight 600-800)
- **Body:** Poppins (clean, readable, weight 300-500)
- **Line height:** 1.6-1.75 for readability

---

## Component Styling

### Cards with Soft Pink Shadows
```html
<div class="bg-white rounded-2xl shadow-sm border border-pink-100 
            transition-all duration-300 hover:shadow-md hover:-translate-y-1">
  <!-- Card content -->
</div>
```

### Primary Button (Pink Theme)
```html
<button class="bg-pink-400 text-white px-6 py-3 rounded-xl font-medium
               transition-all duration-200 hover:bg-pink-500 hover:shadow-lg hover:-translate-y-0.5
               active:scale-[0.98] focus:ring-4 focus:ring-pink-200">
  Konsultasi Sekarang
</button>
```

### Secondary Button (Pink Theme)
```html
<button class="bg-pink-50 text-pink-600 border border-pink-200 px-6 py-3 rounded-xl
               transition-all duration-200 hover:bg-pink-100 hover:border-pink-300">
  secondary action
</button>
```

### Glass Morphism Card
```html
<div class="bg-white/80 backdrop-blur-md rounded-2xl shadow-sm 
            border border-pink-100/50">
  <!-- Glass content -->
</div>
```

### Input Fields
```html
<input class="w-full px-4 py-3 rounded-xl border border-pink-200 
             bg-white/50 text-slate-800 placeholder-slate-400
             transition-all duration-200 focus:border-pink-400 focus:ring-4 focus:ring-pink-100
             hover:border-pink-300">
```

---

## Reduced Motion Support

```css
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}
```

---

## Anti-patterns for Healthcare

| Avoid | Instead |
|-------|---------|
| Fast/jarring animations | Gentle, slow transitions (200-400ms) |
| High contrast flashing | Subtle color shifts |
| Complex hover effects | Simple elevation changes |
| Stark white backgrounds | Cream/off-white with warmth |
| Blue/purple gradients | Soft pink/lavender tones |
| Square edges | Generous border-radius (12-24px) |

---

## Accessibility Checklist

- [x] Minimum 4.5:1 contrast ratio for text
- [x] Focus states visible with pink glow ring
- [x] `prefers-reduced-motion` respected
- [x] Touch targets minimum 44x44px
- [x] Semantic HTML with proper ARIA labels
- [x] No continuous animations except loading

---

## Layout Overrides
- **Max Width:** 1200px
- **Layout:** Full-width sections, centered content

---

## Effects
- Soft box-shadow (multiple: -5px -5px 15px, 5px 5px 15px)
- Smooth press (150ms)
- Inner subtle shadow
- Pink glow on focus states
- Gentle floating for decorative elements

---

## Implementation Notes

Apply these styles to all pages:
1. Landing page (`/`)
2. Dashboard (`/dashboard`)
3. Chat/Telekonseling (`/chat`)
4. Edukasi (`/education`)
5. Skrining (`/screening`)
6. Profile (`/profile`)

The soft pink theme creates a nurturing, calming healthcare environment appropriate for postpartum mothers.
