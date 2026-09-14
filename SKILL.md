---
name: kinetics
description: "Spring-physics web animations. Use for motion UI."
---

# Kinetics

**Source:** [kinetics.colorion.co](https://kinetics.colorion.co/) | **Author:** Csaba Kissi (Colorion)

153+ spring-physics micro-interactions. Each effect: live demo + CSS/React/AI prompt.

## Spring Parameters
| Param | Range | Default | Effect |
|-------|-------|---------|--------|
| Stiffness | 50-400 | 170 | Higher = snappier |
| Damping | 5-40 | 26 | Higher = less bounce |
| Mass | 0.5-5 | 1 | Higher = heavier |

## Presets
| Feel | Stiffness | Damping | Mass |
|------|-----------|---------|------|
| Bouncy | 120 | 8 | 1 |
| Smooth | 170 | 26 | 1 |
| Snappy | 300 | 20 | 0.8 |
| Jelly | 200 | 6 | 1 |

## CSS (no JS)
```css
/* Spring curve via linear() — zero JS runtime */
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

## React
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

## AI Prompt Workflow
1. Browse effects at kinetics.colorion.co
2. Find desired effect
3. Click "AI Prompt" tab
4. Copy prompt → paste into ChatGPT/Claude/Gemini
5. Get production-ready code

## When to Use
- Micro-interactions (buttons, cards, inputs)
- Physics-based motion feel
- Design system motion language
- AI-assisted animation development