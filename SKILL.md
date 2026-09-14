---
name: kinetics
description: "Spring-physics web animations. Use for motion UI."
---

# Kinetics — Spring-Physics Motion for Web Interfaces

**Source:** [kinetics.colorion.co](https://kinetics.colorion.co/) | **GitHub:** [ckissi/kinetics](https://github.com/ckissi/kinetics) | **Author:** Csaba Kissi (Colorion)

## What It Is

Kinetics is a gallery of **153+ spring-physics micro-interactions** for web interfaces. Each effect ships with:
- **Live demo** — interactive preview
- **Physics-style parameter readout** — stiffness, damping, mass values
- **Copy-paste CSS code** — pure CSS implementation
- **Copy-paste React code** — React hooks implementation
- **Ready-made AI prompt** — LLM-friendly prompt to generate the animation in ChatGPT/Claude/Gemini

## Core Concept: Spring Physics vs Fixed-Duration Easing

Traditional CSS animations use fixed durations (e.g., `300ms ease-out`). Kinetics uses **spring physics** — the animation feels alive and responsive because it's based on real physical simulation:

- **Stiffness** — How tight/rigid the spring is (higher = faster, snappier)
- **Damping** — How quickly oscillation dies (higher = less bounce)
- **Mass** — How heavy the element feels (higher = slower, more momentum)

## Categories (153+ effects)

### Interaction & Input
- Button hover/press effects (scale, glow, magnetic)
- Input field focus animations
- Toggle/switch spring transitions
- Drag and snap behaviors
- Magnetic cursor effects
- Ripple effects

### Feedback & State
- Success/error state animations
- Loading spinners with spring physics
- Toast/notification slide-in
- Skeleton loading shimmer
- Progress bar spring fill
- Checkmark draw animation

### Surface & Motion
- Page/card transitions
- Stagger reveal animations
- Parallax scroll effects
- Modal/overlay spring open/close
- Drawer slide with spring bounce
- Grid shuffle/morph

## Spring Physics Parameters Reference

| Parameter | Range | Typical | Effect |
|-----------|-------|---------|--------|
| Stiffness | 50-400 | 170 | Higher = snappier |
| Damping | 5-40 | 26 | Higher = less bounce |
| Mass | 0.5-5 | 1 | Higher = heavier/slower |

### Common Presets

| Feel | Stiffness | Damping | Mass |
|------|-----------|---------|------|
| Bouncy | 120 | 8 | 1 |
| Smooth | 170 | 26 | 1 |
| Snappy | 300 | 20 | 0.8 |
| Heavy | 100 | 15 | 2 |
| Jelly | 200 | 6 | 1 |
| Gentle | 80 | 18 | 1 |

## CSS Implementation Pattern

```css
/* Spring animation using CSS linear() — no JS needed */
.spring-element {
  transition: transform 0.6s linear(
    0, 0.004, 0.016, 0.035, 0.063, 0.098, 0.141, 0.191,
    0.25, 0.316, 0.391, 0.473, 0.563, 0.66, 0.766, 0.879,
    1, 1.11, 1.201, 1.269, 1.317, 1.345, 1.356, 1.352,
    1.335, 1.307, 1.271, 1.229, 1.183, 1.136, 1.089, 1.044,
    1, 0.962, 0.931, 0.908, 0.894, 0.887, 0.888, 0.897,
    0.912, 0.934, 0.96, 0.989, 1.02, 1.05, 1.076, 1.097,
    1.112, 1.12, 1.122, 1.118, 1.108, 1.094, 1.076, 1.055,
    1.033, 1.012, 0.993, 0.978, 0.967, 0.961, 0.959, 0.962,
    0.97, 0.982, 0.997, 1.014, 1.032, 1.048, 1.061, 1.069,
    1.072, 1.069, 1.062, 1.05, 1.034, 1.016, 0.996, 0.976,
    0.958, 0.943, 0.933, 0.928, 0.928, 0.932, 0.941, 0.954,
    0.97, 0.989, 1.008, 1.026, 1.041, 1.052, 1.058, 1.058,
    1.053, 1.044, 1.031, 1.015, 0.998, 0.982, 0.968, 0.958,
    0.953, 0.953, 0.959, 0.969, 0.984, 1.001, 1.019, 1.036,
    1.05, 1.06, 1.064, 1.063, 1.056, 1.044, 1.028, 1.01,
    0.991, 0.974, 0.96, 0.951, 0.947, 0.949, 0.957, 0.97,
    0.987, 1.005, 1.023, 1.038, 1.049, 1.055, 1.054, 1.048,
    1.037, 1.023, 1.005, 0.987, 0.971, 0.958, 0.95, 0.949,
    0.955, 0.966, 0.982, 1, 1.02, 1.037, 1.049, 1.055,
    1.054, 1.048, 1.037, 1.023, 1.005, 0.987, 0.971, 0.958,
    0.95, 0.949, 0.955, 0.966, 0.982, 1
  );
}
```

The `linear()` function with many stops approximates a real spring curve — zero JS runtime cost.

## React Implementation Pattern

```jsx
import { useState } from 'react';

function SpringButton({ children }) {
  const [pressed, setPressed] = useState(false);

  return (
    <button
      onMouseDown={() => setPressed(true)}
      onMouseUp={() => setPressed(false)}
      style={{
        transform: pressed ? 'scale(0.92)' : 'scale(1)',
        transition: 'transform 0.4s cubic-bezier(0.34, 1.56, 0.64, 1)',
      }}
    >
      {children}
    </button>
  );
}
```

## AI Prompt Usage

Each Kinetics effect comes with a **ready-made AI prompt**. These are:
- LLM-friendly descriptions of the animation behavior
- Include all spring parameters
- Designed for ChatGPT, Claude, Gemini, Cursor, etc.
- Copy → paste into AI tool → get production-ready code

### How to Use AI Prompts

1. Browse [kinetics.colorion.co](https://kinetics.colorion.co/)
2. Find the effect you want
3. Click "AI Prompt" tab (alongside CSS/React tabs)
4. Copy the prompt
5. Paste into your AI coding assistant
6. Get full implementation

### Example AI Prompt Structure

```
Create a spring-physics button hover effect with:
- On hover: scale(1.05) with stiffness=170, damping=12, mass=1
- On click: scale(0.95) with stiffness=300, damping=20
- Add a subtle glow that fades in on hover
- Use CSS transition with linear() for spring curve
- No JavaScript dependencies
```

## When to Use Kinetics Patterns

### Use when:
- Adding micro-interactions to buttons, cards, inputs
- Need physics-based (not linear/cubic-bezier) animation feel
- Building design systems with consistent motion language
- Want responsive, natural-feeling UI motion
- Need ready-made animation prompts for AI-assisted development

### Don't use when:
- Simple fade-in/out is sufficient (overkill)
- Performance-critical animations on many elements (use CSS transforms only)
- SVG path animations (use GSAP/Motion instead)
- Complex timeline sequences (use GSAP)

## Integration with Other Tools

- **Framer Motion** — Use Kinetics prompts to describe effects, implement with `motion.div` + spring config
- **React Spring** — Same pattern, use `useSpring` with stiffness/damping/mass
- **GSAP** — For more complex sequences, use Kinetics concepts but GSAP spring helper
- **Pure CSS** — Best for simple effects, use `linear()` spring approximation

## Performance Tips

1. **Prefer CSS `linear()` over JS** — Zero runtime cost, GPU-accelerated
2. **Use `transform` and `opacity` only** — Triggers compositor, no layout thrash
3. **Will-change sparingly** — Only on elements that will animate
4. **Batch spring updates** — In React, use `requestAnimationFrame` for smooth springs
5. **Reduce motion** — Respect `prefers-reduced-motion`

## Reduced Motion

```css
@media (prefers-reduced-motion: reduce) {
  .spring-element {
    transition: transform 0.01ms !important;
  }
}
```

## Links

- **Live Demo:** [kinetics.colorion.co](https://kinetics.colorion.co/)
- **GitHub:** [github.com/ckissi/kinetics](https://github.com/ckissi/kinetics)
- **Author:** Csaba Kissi — [colorion.co](https://colorion.co)
- **License:** Open Source