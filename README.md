# 🧬 Kinetics — Spring-Physics Motion for Web Interfaces

> A gallery of **153+ spring-physics micro-interactions** for web interfaces. Each effect ships with a live demo, a physics-style parameter readout, and copy-paste CSS + React + AI prompt code.

**🔗 Live Demo:** [kinetics.colorion.co](https://kinetics.colorion.co/)  
**📦 GitHub:** [ckissi/kinetics](https://github.com/ckissi/kinetics)  
**👤 Author:** Csaba Kissi — [colorion.co](https://colorion.co)

---

## 📖 What is Kinetics?

Kinetics is a curated library of interface animations built on **spring physics** instead of fixed-duration easing. Instead of saying "animate for 300ms with ease-out," you say "this element has a spring with stiffness=170, damping=26, mass=1" — and the motion feels alive, responsive, and physically accurate.

### Key Features

- 🎯 **153+ micro-interactions** across multiple categories
- 🎛️ **Tunable physics** — adjust stiffness, damping, mass in real-time
- 📋 **Copy-paste CSS** — pure CSS with `linear()` spring curves (zero JS)
- ⚛️ **Copy-paste React** — hooks-based implementation
- 🤖 **AI Prompts** — ready-made prompts for ChatGPT/Claude/Gemini to generate the animation
- 📱 **Responsive** — works on all screen sizes
- ♿ **Accessible** — respects `prefers-reduced-motion`

---

## 🧪 Spring Physics 101

### The Three Parameters

| Parameter | What It Controls | Range | Typical Value |
|-----------|------------------|-------|---------------|
| **Stiffness** | How tight/rigid the spring is | 50–400 | 170 |
| **Damping** | How quickly oscillation dies | 5–40 | 26 |
| **Mass** | How heavy the element feels | 0.5–5 | 1 |

### Visual Guide

```
Stiffness:  Low ◄─────────────────────► High
            Slow, elastic              Fast, snappy

Damping:    Low ◄─────────────────────► High
            Lots of bounce             No bounce, settles quickly

Mass:       Low ◄─────────────────────► High
            Light, responsive          Heavy, momentum
```

### Common Presets

| Feel | Stiffness | Damping | Mass | Best For |
|------|-----------|---------|------|----------|
| 🎈 **Bouncy** | 120 | 8 | 1 | Playful buttons, notifications |
| 🌊 **Smooth** | 170 | 26 | 1 | General UI, cards, modals |
| ⚡ **Snappy** | 300 | 20 | 0.8 | Quick feedback, toggles |
| 🪨 **Heavy** | 100 | 15 | 2 | Large elements, page transitions |
| 🍮 **Jelly** | 200 | 6 | 1 | Fun interactions, Easter eggs |
| 🌿 **Gentle** | 80 | 18 | 1 | Subtle hover effects, tooltips |

---

## 📂 Categories

### 🖱️ Interaction & Input
- Button hover/press effects (scale, glow, magnetic)
- Input field focus animations
- Toggle/switch spring transitions
- Drag and snap behaviors
- Magnetic cursor effects
- Ripple effects

### ✅ Feedback & State
- Success/error state animations
- Loading spinners with spring physics
- Toast/notification slide-in
- Skeleton loading shimmer
- Progress bar spring fill
- Checkmark draw animation

### 🎬 Surface & Motion
- Page/card transitions
- Stagger reveal animations
- Parallax scroll effects
- Modal/overlay spring open/close
- Drawer slide with spring bounce
- Grid shuffle/morph

---

## 💻 Implementation

### Pure CSS (Recommended for Simple Effects)

```css
/* Spring animation using CSS linear() — zero JS runtime cost */
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

**Why `linear()`?** The `linear()` CSS function accepts a list of easing points. With ~100 carefully calculated stops, it approximates a real spring differential equation — no JavaScript, no libraries, pure GPU-accelerated CSS.

### React Implementation

```jsx
import { useState } from 'react';

function SpringButton({ children, onClick }) {
  const [pressed, setPressed] = useState(false);

  return (
    <button
      onMouseDown={() => setPressed(true)}
      onMouseUp={() => setPressed(false)}
      onMouseLeave={() => setPressed(false)}
      onClick={onClick}
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

### Framer Motion

```jsx
import { motion } from 'framer-motion';

function SpringCard({ children }) {
  return (
    <motion.div
      whileHover={{ scale: 1.05, y: -4 }}
      whileTap={{ scale: 0.95 }}
      transition={{
        type: 'spring',
        stiffness: 170,
        damping: 12,
        mass: 1,
      }}
    >
      {children}
    </motion.div>
  );
}
```

### React Spring

```jsx
import { useSpring, animated } from '@react-spring/web';

function SpringElement({ children }) {
  const [hovered, setHovered] = useState(false);
  
  const spring = useSpring({
    transform: hovered ? 'scale(1.05)' : 'scale(1)',
    config: { stiffness: 170, damping: 12, mass: 1 },
  });

  return (
    <animated.div
      style={spring}
      onMouseEnter={() => setHovered(true)}
      onMouseLeave={() => setHovered(false)}
    >
      {children}
    </animated.div>
  );
}
```

---

## 🤖 AI Prompt Usage

Each Kinetics effect includes a **ready-made AI prompt** — a structured description you can paste into any AI coding assistant to generate the animation.

### How It Works

1. **Browse** → [kinetics.colorion.co](https://kinetics.colorion.co/)
2. **Find** → Pick the effect you want
3. **Copy** → Click the "AI Prompt" tab (next to CSS/React tabs)
4. **Paste** → Into ChatGPT, Claude, Gemini, Cursor, etc.
5. **Get** → Full production-ready implementation

### Example AI Prompt

```
Create a spring-physics button hover effect:
- On hover: scale(1.05) with stiffness=170, damping=12, mass=1
- On click: scale(0.95) with stiffness=300, damping=20
- Add a subtle glow that fades in on hover
- Use CSS transition with linear() for spring curve
- No JavaScript dependencies
- Respect prefers-reduced-motion
```

### Why AI Prompts Matter

- **Consistency** — Same spring parameters across your entire app
- **Speed** — No need to calculate spring curves manually
- **Learning** — See how physics parameters translate to motion
- **Portability** — Works with any AI tool, any framework

---

## 🎯 When to Use

### ✅ Use Kinetics When:
- Adding micro-interactions to buttons, cards, inputs
- You want physics-based (not linear/cubic-bezier) animation feel
- Building design systems with consistent motion language
- Need responsive, natural-feeling UI motion
- Want ready-made animation prompts for AI-assisted development

### ❌ Don't Use When:
- Simple fade-in/out is sufficient (overkill)
- Performance-critical animations on hundreds of elements
- SVG path animations (use GSAP/Motion instead)
- Complex timeline sequences (use GSAP)

---

## ⚡ Performance Tips

1. **Prefer CSS `linear()` over JS** — Zero runtime cost, GPU-accelerated
2. **Use `transform` and `opacity` only** — Triggers compositor, no layout thrash
3. **Will-change sparingly** — Only on elements that will animate
4. **Batch spring updates** — In React, use `requestAnimationFrame`
5. **Reduce motion** — Always respect user preferences

### Accessibility

```css
@media (prefers-reduced-motion: reduce) {
  .spring-element {
    transition: transform 0.01ms !important;
  }
}
```

---

## 🔗 Integration Guide

| Library | How to Use Kinetics |
|---------|---------------------|
| **Pure CSS** | Copy `linear()` curve directly into your stylesheet |
| **Framer Motion** | Use AI prompt → implement with `motion.div` + spring config |
| **React Spring** | Use AI prompt → implement with `useSpring` + stiffness/damping/mass |
| **GSAP** | Use concepts as reference → implement with GSAP spring helper |
| **Vue** | Copy CSS curves → use with Vue transition classes |
| **Svelte** | Copy CSS curves → use with Svelte transition directives |

---

## 📚 Resources

- **Official Site:** [kinetics.colorion.co](https://kinetics.colorion.co/)
- **GitHub Repo:** [github.com/ckissi/kinetics](https://github.com/ckissi/kinetics)
- **Author:** Csaba Kissi — [colorion.co](https://colorion.co)
- **CSS linear() MDN:** [developer.mozilla.org](https://developer.mozilla.org/en-US/docs/Web/CSS/easing-function/linear)
- **Spring Physics Explained:** [web.dev](https://web.dev/articles/animations-guide)

---

## 📄 License

Open Source — see [GitHub repo](https://github.com/ckissi/kinetics) for details.

---

*Built with ❤️ by [PeDitX](https://github.com/PeDitXOS) — Reference guide for [Kinetics](https://kinetics.colorion.co/)*
