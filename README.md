# Crazy Knight Curve

**A seed-based generative system for smooth knight's-tour curves.**

A catalogue of computational textile compositions for fashion, textile and surface design — algorithmically drawn, seed-documented, and ready for production.

---

## Overview

Crazy Knight Curve is a generative design system rather than a single artwork. Each composition is built from a random walk in the shape of a knight's move — one step forward, two sideways, or vice versa — traced across a square grid and then smoothed through a Catmull-Rom spline to produce a single, continuous line.

The system is designed for:

- **Fashion houses** adapting path-based ornament for apparel and accessories
- **Textile studios** developing repeat patterns and yardage
- **Surface designers** working across print, wallpaper, and interior applications

Every composition can be licensed, adapted, or commissioned to a brief.

---

## Concept

A path, when it is *traced* rather than drawn, becomes a line of thought — erratic, precise, quietly yours.

The wandering path — irregular, rule-bound, endlessly variable — has always carried meaning. From caravan routes to textile draft lines, the traced curve is one of the oldest forms of drawn computation we have. Crazy Knight Curve translates that structure into code. Each composition begins with a starting cell and unfolds through a chain of knight's moves until the path exhausts itself or the step limit is reached. The result is then smoothed — not as a chain of straight segments, but as a single flowing line.

The grid size, the two step lengths, the total number of moves, and the starting position are all derived from a single numeric seed.

Like the other still volumes in this series (Girih, Arachne, Celestial Grove, ChaotiColor, Citrus Mosaic), **Crazy Knight Curve is a static composition.** The plate, the framed plate, the surfaces, and the archive are all static frames. A traced line is something you read; its character is stillness, not motion.

---

## Features

- **Seed-based generation** — every composition is defined by a numeric seed and can be regenerated exactly
- **Deterministic output** — the same seed always produces the same composition
- **Knight's-move walk** — randomized (s1, s2) step lengths, bounded to a square grid
- **Catmull-Rom smoothing** — the raw walk is smoothed into a single continuous curve
- **Adaptive grid** — 5 to 305 divisions per axis, derived from the seed
- **Adaptive surfaces** — one seed applied across print, scarf, textile, and wall formats
- **Archive** — eight curated seeds available for immediate loading
- **Download** — export the composition as a high-resolution PNG
- **Keyboard shortcuts** — `R` for new seed, `S` to save

---

## Project Structure

```
.
├── index.html          # Main catalogue page
├── images/
│   ├── fav.svg         # Favicon
│   ├── tote.png        # Mockup: tote bag
│   ├── tee.png         # Mockup: t-shirt
│   └── cushion.png     # Mockup: cushion
└── README.md
```

---

## How It Works

### The Seed

A numeric seed (a large integer) initializes a deterministic pseudo-random generator. From this seed, the system derives:

- Grid size (5–305 cells per axis)
- Step length s1 (the longer leg of the knight's move)
- Step length s2 (the shorter leg, always ≤ s1)
- Total number of moves (10 to a few thousand)
- Starting cell (x, y)

Because the generator is deterministic, the same seed always produces the same composition — on any device, at any time.

### The Knight's Move

The knight's move is the classic chess leap: **one step in one direction, two steps in the other** — or vice versa. From any cell, there are up to eight possible knight moves:

```
      ○     ○
        ╲ ╱
    ○ ── ● ── ○
        ╱ ╲
      ○     ○
```

At each step of the walk, the system:

1. Computes all eight candidate positions from the current cell.
2. Filters to those inside the grid bounds.
3. Picks one at random.
4. If no valid moves remain, the walk ends early.

The path is stored as a list of grid cells — the raw walk.

### The Step Lengths

Unlike a standard knight's move (which is always (2, 1) or (1, 2)), Crazy Knight Curve generalizes the leap. The seed determines:

- **s1** — the longer leg (typically between 1 and the grid size divided by a small factor)
- **s2** — the shorter leg (always ≤ s1)

This means the walk can be a standard knight's move (2, 1), a stretched leap (3, 1), a near-diagonal step (2, 2), or almost anything in between. Each seed's character depends on this ratio.

### The Smoothing

The raw walk is a chain of grid cells. Drawn directly, it would look like a series of straight lines with sharp corners. To soften it, the system applies a **Catmull-Rom spline** — a curve that passes through every control point and interpolates smoothly between them.

Each segment between two consecutive path points is subdivided into 25 sub-segments, producing a final curve with thousands of points. The result is a single continuous line that reads as a flowing path, not a wireframe.

### The Grid

The grid division count is derived from the seed, between 5 and 305 cells per axis. The path is drawn on the **inner 90%** of the canvas (a 9/10 scale factor), so the composition always has a small margin — like a plate on a page.

- A **coarse grid** (5 to 20 divisions) produces bold, sweeping steps.
- A **fine grid** (200 to 305 divisions) produces delicate, near-woven detail.

### The Surfaces

The same seed is rendered across four surface formats. These are static frames — they represent the print-ready composition.

| Surface  | Aspect | Material          |
|----------|--------|-------------------|
| Print    | 1 : 1  | Cotton rag        |
| Scarf    | 3 : 1  | Twill silk        |
| Textile  | 4 : 3  | Fabric yardage    |
| Wall     | 2 : 3  | Wallpaper         |

Each surface uses the same underlying seed and structural logic — only the repeat, orientation, and scale change.

### Stillness

Like Girih, Arachne, Celestial Grove, ChaotiColor, and Citrus Mosaic, Crazy Knight Curve does not animate. The plate is a single frozen frame — the composition is complete the moment it is generated.

This is a deliberate design choice. A traced path is not a swarm. It is not a rotation. It is a single line, drawn once and left. Its stillness is what makes it print-ready in the strictest sense: what you see is what you get.

---

## Usage

### In the browser

1. Open `index.html` in any modern browser.
2. Click **New Seed** to generate a new composition.
3. Click **Download** to save the composition as a PNG.
4. Scroll to the **Archive** section and click any plate to load it into Plate 001.

### Keyboard shortcuts

| Key | Action          |
|-----|-----------------|
| `R` | New seed        |
| `S` | Save as PNG     |

### Reproducing a composition

Each composition is identified by an 8-digit seed label displayed in the metadata panel. To reproduce a specific composition, note the seed and regenerate it programmatically:

```js
const rng = new RandomGenerator(seed);
const features = buildFeatures(rng);
renderComposition(canvas, features, rng);
```

Because the generator is deterministic, this will produce the identical composition on any device.

---

## Technical Notes

- **No build step.** The system is a single HTML file with inline CSS and JavaScript.
- **No dependencies.** All drawing is done with the native Canvas 2D API.
- **Deterministic.** The `RandomGenerator` class uses a xorshift-based PRNG seeded by an integer, so identical seeds produce identical outputs.
- **Static rendering.** Every canvas renders a single frame. There is no animation loop.
- **Feature isolation.** Cover, framed plate, surfaces, and archive thumbnails each derive their own feature set from their own local RNG, without disturbing the main plate's state.
- **Bounded walk.** The knight's-move walk terminates cleanly when no valid moves remain, so no infinite loop is possible even at large grid sizes.
- **Explicit RNG passing.** `getRandomKnightMove` and the Catmull-Rom smoothing both take an explicit RNG, so every canvas generates its own path independently.
- **Responsive.** The layout adapts from large desktop down to very small mobile devices (tested at 360px viewport width).
- **Accessible.** Supports `prefers-reduced-motion`. Pinch-zoom is enabled.

### Browser support

Tested in current versions of:

- Chrome / Edge
- Firefox
- Safari (desktop and iOS)

---

## Licensing

All Crazy Knight Curve compositions are **seed-documented** and available for licensing across textile, surface, and print applications.

- **Standard licenses** cover single-product production runs.
- **Commercial use, custom editions, or exclusive rights** are available on request.

Each license is issued against a specific seed ID. Regeneration of the same seed produces the identical composition — ensuring reproducibility between artist, studio, and manufacturer.

For licensing enquiries: [reyhanehdaneshdoost@gmail.com](mailto:reyhanehdaneshdoost@gmail.com)

---

## Commission

Crazy Knight Curve is a generative design system, not a fixed artwork. It can be adapted for specific briefs:

| Service     | Description                                                       |
|-------------|-------------------------------------------------------------------|
| Licensing   | Existing seeds from the archive, licensed for production use      |
| Commission  | New compositions designed to your palette, repeat, and product    |
| Systems     | A private generative tool built for your studio's ongoing use     |

To begin a conversation: [reyhanehdaneshdoost@gmail.com](mailto:reyhanehdaneshdoost@gmail.com)

---

## Series

Crazy Knight Curve is part of a computational textile series. Each volume approaches ornament from a different structural angle:

| Volume                | Structure                    | Motion                     |
|-----------------------|------------------------------|----------------------------|
| Girih 1               | Islamic geometric            | Static                     |
| Arachne               | Rotating rings               | Static                     |
| Baroque Me Baby       | Baroque frames               | Static                     |
| Bezier 1              | Concentric curves            | Static                     |
| Bezier 2              | Single rotating curve        | Animated (plate)           |
| Brownian Graphe       | Graph networks               | Animated + interactive     |
| Celestial Grove       | Recursive branch trees       | Static                     |
| ChaotiColor           | Cellular automata            | Static                     |
| Citrus Mosaic         | Arc-and-triangle tiles       | Static                     |
| **Crazy Knight Curve**| **Knight's-tour path**       | **Static**                 |

The series is designed as a coherent whole — same page structure, same seed logic, same licensing and commission terms — so that each volume can be presented individually or as part of a larger body of work.

---

## Credits

- **Design & Generative System** — Reyhaneh Daneshdoost
- **Typefaces** — Cormorant Garamond · DM Mono
- **Platform** — Reyrove Studio
- **Edition** — Crazy Knight Curve, Autumn 2026

### On AI tools

Where technical obstacles were encountered, AI tools were used for debugging and code optimization. Every structural, aesthetic, and conceptual decision remained the artist's own.

---

## Links

- Website — [reyrove.github.io](https://reyrove.github.io/)
- Instagram — [@rey._.rove](https://www.instagram.com/rey._.rove/)
- LinkedIn — [Reyhaneh Daneshdoost](https://www.linkedin.com/in/reyhaneh-daneshdoost-730481160/)
- X — [@reyrove](https://x.com/reyrove)

---

© Crazy Knight Curve · All compositions reproducible by seed · Computational Textile Design