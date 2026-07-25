# Crazy Knight Curve — Generative Art

[![Live Demo](https://img.shields.io/badge/demo-live-green?style=for-the-badge)](https://reyrove.github.io/Crazy-Knight-Curve-Generative-Art)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

> **Generative knight's tour art with smooth curves.** Each refresh creates a unique path of a knight's journey across a grid, rendered as elegant Catmull-Rom curves.

## 🎨 Live Demo

<div align="center">
  <a href="https://reyrove.github.io/Crazy-Knight-Curve-Generative-Art" target="_blank">
    <img src="demo-screenshot.jpg" alt="Crazy Knight Curve Website Demo" width="800" style="border-radius: 12px; box-shadow: 0 8px 32px rgba(0,0,0,0.4);"/>
  </a>
  <br><br>
  <a href="https://reyrove.github.io/Crazy-Knight-Curve-Generative-Art" target="_blank">
    <img src="https://img.shields.io/badge/🌐_View_Live_Demo-0a0a0a?style=for-the-badge&logo=githubpages&logoColor=white&color=c9a84c" alt="View Live Demo" width="300"/>
  </a>
  <br>
  <em>Click the image or button to experience the generative art</em>
</div>

## 👕 Apparel Preview

<div align="center">
  <img src="Crazy-Knight-Curve.jpg" alt="Crazy Knight Curve on T-Shirt" width="600" style="border-radius: 12px; box-shadow: 0 8px 32px rgba(0,0,0,0.3);"/>
  <br>
  <em>Crazy Knight Curve artwork printed on a T-shirt</em>
</div>

## ✨ Features

- **Knight's Tour** — Random knight moves across a square grid
- **Smooth Curves** — Catmull-Rom curve rendering for elegant paths
- **Grid-Based** — 5×5 to 305×305 grid size
- **Random Path** — Unique path every refresh
- **Seed-Based** — Every composition is unique and reproducible via its seed
- **Save & Share** — Download as PNG with seed in filename
- **Apparel Mode** — Preview artwork on a T-shirt mockup
- **Responsive** — Works on desktop, tablet, and mobile
- **Pure JavaScript** — No external dependencies
- **Keyboard Shortcuts**:
  - `R` — Regenerate
  - `S` — Save image
  - `T` — Toggle apparel view

## 🎨 Artwork Details

| Parameter | Range | Description |
|-----------|-------|-------------|
| **Grid Size** | 5×5 to 305×305 | Square grid dimensions |
| **Step Size 1** | 1 to grid/9 | First knight move step |
| **Step Size 2** | 0 to step1 | Second knight move step |
| **Total Steps** | 10 to grid cells | Number of moves |
| **Start Position** | Random | Starting point on grid |
| **Curve Type** | Catmull-Rom | Smooth interpolated curves |

## 🎯 How Knight Moves Work

A knight moves in an "L" shape:
- Two steps in one direction, then one step perpendicular
- Or one step in one direction, then two steps perpendicular

This creates beautiful, intricate path patterns across the grid.

## 🌀 Catmull-Rom Curves

Unlike straight lines, Catmull-Rom curves create smooth, flowing paths that pass through each point of the knight's journey. This gives the artwork an elegant, organic feel while preserving the underlying structure of the knight's tour.

## 🚀 Quick Start

### Local Development

```bash
# Clone the repository
git clone https://github.com/reyrove/Crazy-Knight-Curve-Generative-Art.git

# Navigate to the directory
cd Crazy-Knight-Curve-Generative-Art

# Open in browser
open index.html
# or use a live server
```

### Deploy to GitHub Pages

1. Push to GitHub
2. Go to Settings → Pages
3. Select branch `main` and root folder
4. Your site will be live at `https://reyrove.github.io/Crazy-Knight-Curve-Generative-Art`

## 🧠 How It Works

The artwork is generated using a deterministic random number generator, seeded by timestamp + random noise. Every refresh:

1. **Setup**:
   - Random square grid size (5-305)
   - Random step sizes (s1, s2) for knight moves
   - Random starting position
   - Random number of steps

2. **Knight's Path**:
   - Start at random position on grid
   - Each step moves in an L-shape (knight move)
   - Step sizes (s1, s2) determine the L-shape dimensions
   - Path continues until steps run out or no valid moves remain

3. **Curve Rendering**:
   - White background
   - Path points converted to pixel coordinates
   - Catmull-Rom curve interpolation creates smooth path
   - Black stroke with clean, minimalist aesthetic

## 📁 File Structure

```
Crazy-Knight-Curve-Generative-Art/
├── index.html              # Main application (all-in-one)
├── Crazy-Knight-Curve.jpg  # T-shirt mockup image
├── fav.svg                 # Favicon
├── demo-screenshot.jpg     # Website demo screenshot
├── README.md               # This file
└── LICENSE                 # MIT License
```

## 🛠️ Tech Stack

- **Pure Vanilla HTML/CSS/JS** — No dependencies
- **Canvas API** — 2D rendering
- **Catmull-Rom Interpolation** — Smooth curve generation
- **CSS Flexbox/Grid** — Responsive layout
- **GitHub Pages** — Hosting

## 🎯 Interactive Controls

| Action | Keyboard | Button |
|--------|----------|--------|
| Regenerate | `R` | Click "regenerate" |
| Save Image | `S` | Click "regenerate" |
| Toggle Apparel | `T` | Click "apparel" |

## 🎨 The Creative Process

### Knight's Tour
The knight's tour is a classic chess problem where a knight visits every square on a board exactly once. This artwork takes inspiration from that concept, creating unique paths with random step sizes and directions.

### Step Sizes
The knight uses two step sizes (s1, s2):
- If s1=2 and s2=1, it's a standard chess knight move
- If s1=3 and s2=2, it's a larger knight-like move
- Random values create unique patterns

### Catmull-Rom Curves
Unlike straight lines, Catmull-Rom curves:
- Pass through all control points
- Create smooth, flowing paths
- Produce elegant, organic shapes
- Maintain the structure of the knight's tour

### Grid Scale
The grid size varies randomly, creating either dense, intricate patterns (large grids) or sparse, elegant designs (small grids).

## 📱 Responsive Design

The application automatically adapts to:
- Desktop screens
- Tablets
- Mobile phones
- Landscape orientation
- Various aspect ratios

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Fork the repository
- Create a feature branch
- Submit a pull request

### Ideas for Contributions:
- Different curve interpolation methods
- Color variations
- Animation features
- Interactive controls
- Performance optimizations

## 📄 License

MIT License — see [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Inspired by the knight's tour problem
- Catmull-Rom curve interpolation
- Pure JavaScript implementation
- Special thanks to the creative coding community

---

**Built with ❤️ and crazy knight curves**