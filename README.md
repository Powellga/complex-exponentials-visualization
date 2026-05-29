# Complex Exponentials Visualization

An interactive, single-page visualization exploring why three very different-looking complex expressions all have an absolute value (modulus) of exactly **1**:

```
|e^(iπ)| = |π^(ie)| = |i^(πe)| = 1
```

It plots all three numbers on the unit circle in the complex plane, walks through the math step by step, and lets you animate and inspect the result. Built with the HTML5 Canvas and vanilla JavaScript — no external dependencies.

**▶ View it live:** https://powellga.github.io/complex-exponentials-visualization/

## The idea

The three constants come from different branches of mathematics — `e` from calculus, `π` from geometry, `i` from algebra — yet each of these expressions evaluates to a point on the unit circle, so each has modulus 1:

- **`e^(iπ) = -1`** — Euler's identity; modulus `|-1| = 1`.
- **`π^(ie) = e^(i·e·ln π)`** — a purely imaginary exponent, so the result is `e^(iθ)` with `θ = e·ln π ≈ 3.107` rad; modulus 1. Value ≈ `0.368 − 0.930i`.
- **`i^(πe) = e^(iπ²e/2)`** — writing `i = e^(iπ/2)`, the exponent `π²e/2 ≈ 13.4` is real, so again `e^(iθ)`; modulus 1. Value ≈ `0.949 + 0.315i`.

The page presents this as a static reference (full derivations in text) **and** as a live canvas plot computed from `Math.E`, `Math.PI`, and `Math.log` so the plotted points match the math exactly.

## Features

- **Unit-circle plot** of all three complex numbers, with labeled axes, grid, quarter-circle tick marks, and vectors drawn from the origin.
- **Start Animation** — points sweep around the unit circle, illustrating that every `e^(iθ)` stays at radius 1 regardless of angle.
- **Show Traces** — leaves a fading trail along the circular path during animation.
- **Show Math Steps** — overlays the angle (θ in degrees) of each point on the plot.
- **Reset View** — returns to the static, true-position layout.
- **Hover tooltips** — mouse over any point (touch-supported on mobile) to see its description and confirm `|z| = 1.000`.
- **Full written derivations** for each of the three identities, plus explanation cards on Euler's formula, the complex modulus, and the unit-circle property.
- **Responsive** — the canvas and layout adapt to the viewport, down to mobile widths.

## Controls

| Button | Action |
|--------|--------|
| Start / Stop Animation | Rotate the points around the unit circle |
| Show Traces | Toggle the fading circular trail |
| Show Math Steps | Toggle on-plot angle (θ) labels |
| Reset View | Stop animation and return to static positions |

Hover (or tap) a plotted point for its label, description, and modulus.

## How it works

Everything is in `index.html` — content, styling, derivations, and logic in one file.

- The three numbers are computed once at load: `e^(iπ)` is hard-coded as `-1`, while `π^(ie)` and `i^(πe)` are derived from their real exponent angles (`e·ln π` and `π²e/2`) via `cos`/`sin`. Their displayed decimal values are generated from those computations.
- `drawComplexPlane()` renders the axes, grid, unit circle, and scale markers; `drawPoint()` draws each number's vector, dot, glow, and label.
- A `requestAnimationFrame` loop drives the optional animation, advancing a shared angle and (when enabled) accumulating trace points.
- Mouse/touch handlers do simple distance-based hit testing to highlight a point and show its tooltip.

> Note: during animation the three points are spaced evenly around the circle for visual effect; their *true* positions are shown in the static (Reset View) layout.

## Running locally

No build and no dependencies. Either open `index.html` directly in any modern browser, or serve the folder statically (e.g. `python -m http.server`) and open the page.

## Tech

- HTML5 Canvas 2D
- Vanilla JavaScript (no frameworks, no external assets)

## Author

Gregg Powell · g.a.powell@protonmail.com
