# Design Tokens Implementation

## Overview

This document describes the premium design token system implemented in NotaryOS. All tokens are defined as CSS custom properties (variables) in the `:root` selector for global accessibility.

## Implementation Status

✅ **Phase 2 Complete**: Design tokens layer implemented without layout changes

**Location**: `index.html` lines 95-187 (CSS `:root` block)

## Token Categories

### 1. Color Tokens

#### Background & Surface
- `--app-bg`: #F8F9FA - Main application background
- `--surface-bg`: #FFFFFF - Primary surface for cards and panels
- `--surface-2`: #F1F3F5 - Secondary surface for subtle contrast
- `--surface-muted`: #eef2ff - Compatibility layer (legacy)

#### Text
- `--text-primary`: #212529 - Primary text, high contrast
- `--text-secondary`: #495057 - Secondary text, labels
- `--text-muted`: #64748b - Compatibility layer (legacy)
- `--muted`: #ADB5BD - Tertiary text, placeholders

#### Brand & Semantic
- `--brand`: #4C6EF5 - Primary brand color
- `--brand-hover`: #4263eb - Brand hover state
- `--brand-soft`: #e0e7ff - Brand tint for backgrounds
- `--success`: #37B24D - Success states
- `--success-soft`: #d3f9d8 - Success backgrounds
- `--warning`: #F59F00 - Warning states
- `--warning-soft`: #fff3bf - Warning backgrounds
- `--danger`: #F03E3E - Error/destructive states
- `--danger-soft`: #ffe0e0 - Error backgrounds

#### Borders & Inputs
- `--border-color`: #E9ECEF - Standard borders
- `--input-border`: #E9ECEF - Form input borders

### 2. Spacing Scale (8px base)

| Token | Value | Pixels | Usage |
|-------|-------|--------|-------|
| `--space-1` | 0.25rem | 4px | Tight spacing, icon gaps |
| `--space-2` | 0.5rem | 8px | Base unit, small padding |
| `--space-3` | 0.75rem | 12px | Compact spacing |
| `--space-4` | 1rem | 16px | Standard spacing |
| `--space-5` | 1.25rem | 20px | Medium spacing |
| `--space-6` | 1.5rem | 24px | Card padding, section gaps |
| `--space-8` | 2rem | 32px | Large section spacing |
| `--space-10` | 2.5rem | 40px | Extra large spacing |
| `--space-12` | 3rem | 48px | Section dividers |
| `--space-16` | 4rem | 64px | Major section breaks |

### 3. Border Radius

| Token | Value | Usage |
|-------|-------|-------|
| `--radius-sm` | 4px | Badges, small elements |
| `--radius-md` | 8px | Buttons, inputs |
| `--radius-lg` | 12px | Cards, modals |
| `--radius-xl` | 16px | Large containers |
| `--radius-2xl` | 20px | Extra large containers |

### 4. Shadows

| Token | Value | Usage |
|-------|-------|-------|
| `--shadow-sm` | `0 1px 2px 0 rgba(0,0,0,0.05)` | Buttons, inputs |
| `--shadow-md` | `0 4px 6px -1px rgba(0,0,0,0.1), 0 2px 4px -1px rgba(0,0,0,0.06)` | Cards |
| `--shadow-lg` | `0 10px 15px -3px rgba(0,0,0,0.1), 0 4px 6px -2px rgba(0,0,0,0.05)` | Modals, drawers |
| `--shadow-xl` | `0 20px 25px -5px rgba(0,0,0,0.1), 0 10px 10px -5px rgba(0,0,0,0.04)` | Elevated modals |

### 5. Typography

#### Font Families
- `--font-sans`: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif
- `--font-serif`: 'Merriweather', Georgia, serif
- `--font-heading`: 'Poppins', sans-serif

#### Font Sizes
| Token | Value | Pixels | Usage |
|-------|-------|--------|-------|
| `--text-xs` | 0.75rem | 12px | Tiny labels, tertiary info |
| `--text-sm` | 0.875rem | 14px | Small text, captions |
| `--text-base` | 1rem | 16px | Body text (default) |
| `--text-lg` | 1.125rem | 18px | Lead paragraphs |
| `--text-xl` | 1.25rem | 20px | H4, sub-headings |
| `--text-2xl` | 1.5rem | 24px | H3, card titles |
| `--text-3xl` | 1.875rem | 30px | H2, section titles |
| `--text-4xl` | 2.25rem | 36px | H1, page titles |

#### Font Weights
- `--font-normal`: 400
- `--font-medium`: 500
- `--font-semibold`: 600
- `--font-bold`: 700
- `--font-extrabold`: 800

#### Line Heights
- `--leading-tight`: 1.25 - Headings
- `--leading-snug`: 1.375 - Sub-headings
- `--leading-normal`: 1.5 - Body text
- `--leading-relaxed`: 1.625 - Paragraphs
- `--leading-loose`: 2 - Spacious text

### 6. Transitions

- `--transition-fast`: 150ms ease - Quick interactions
- `--transition-base`: 200ms ease - Standard transitions
- `--transition-slow`: 250ms ease - Smooth, noticeable changes

## Typography Hierarchy

Updated base styles (lines 189-244):

```css
body {
    font-family: var(--font-sans);
    font-size: var(--text-base);
    line-height: var(--leading-normal);
    font-weight: var(--font-normal);
}

h1 { font-size: var(--text-4xl); font-weight: var(--font-bold); }
h2 { font-size: var(--text-3xl); font-weight: var(--font-bold); }
h3 { font-size: var(--text-2xl); font-weight: var(--font-semibold); }
h4 { font-size: var(--text-xl); font-weight: var(--font-semibold); }
```

## Backward Compatibility

All existing CSS variable names are preserved with compatibility comments:

- `--accent-color` → maps to `--brand`
- `--accent-hover` → maps to `--brand-hover`
- `--accent-soft` → maps to `--brand-soft`
- `--text-muted` → preserved alongside `--muted`
- `--surface-muted` → preserved alongside `--surface-2`

Existing utility classes remain functional:
- `.theme-app-bg`
- `.theme-surface`
- `.theme-surface-muted`
- `.theme-text`
- `.theme-text-muted`
- `.theme-border`
- `.theme-accent-btn`
- `.theme-pill`

## Usage Guidelines

### In Component Styles

```css
/* Use tokens instead of hardcoded values */
.my-card {
    background: var(--surface-bg);
    border: 1px solid var(--border-color);
    border-radius: var(--radius-lg);
    padding: var(--space-6);
    box-shadow: var(--shadow-md);
    transition: box-shadow var(--transition-base);
}

.my-card:hover {
    box-shadow: var(--shadow-lg);
}
```

### In Tailwind Classes

Tailwind classes can still be used, but prefer token-based custom classes for consistency:

```jsx
{/* Instead of: className="bg-white p-6 rounded-xl shadow-md" */}
{/* Use: className="premium-card" (defined with tokens) */}
```

## Testing

✅ **Verified**: All existing screens render correctly with new tokens
✅ **Verified**: No layout shifts or visual regressions
✅ **Verified**: Backward compatibility maintained

## Next Steps

- [ ] Create shared component library using these tokens
- [ ] Migrate existing components incrementally
- [ ] Document component patterns

## References

- Original design tokens: `UI_POLISH_PLAN.md` Section II
- Token usage examples: Design System Showcase (separate project)
