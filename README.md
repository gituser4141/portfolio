# 🕹️ Developer Dungeon // Retro 8-Bit Portfolio Engine

A unique, retro-inspired interactive portfolio experience built using standard HTML5 Canvas and JavaScript. Instead of scrolling through a standard text layout, users pilot a character through a code dungeon where project categories are structured as interactive nodes. 

Includes a high-performance custom collision engine, global state loop locks, and crisp responsive overlay modules designed with Tailwind CSS.

---

## 🚀 Live Demo & Mechanics

- **Movement Matrix:** Navigated via keyboard (`WASD` or `Arrow Keys`).
- **Interactive Triggers:** Stepping over specialized glowing anchor nodes registers geometric grid intersections and launches localized project deep-dives.
- **Recruiter UI:** Seamlessly pauses the underlying canvas engine when modals are active, shifting context to crisp, highly readable typography featuring tech badges and direct source links.

---

## 🛠️ Architecture & Core Mechanics

The backend architecture is broken into a dual-layer state loop to guarantee high performance, smooth frame delivery, and precise window management:

### 1. Spatial Grid Logic & Collisions
The environment is mapped entirely using a fast 2D tile matrix array. Walls, clear floors, and trigger zones are flagged cleanly:
- `0` = Walkable Floor Tiles
- `1` = Hard Collision Boundary Walls
- `2, 3, 4` = Interactive Project Nodes (`C`, `SQL`, `Web Core`)

Multi-point spatial edge buffers check if the player's bounding boxes intersect with structural walls before committing coordinates to the render queue, preventing clipping glitches.

### 2. State-Locking & The Escape Ejector
To prevent frame lockups where closing a modal instantly re-triggers the collision on the next engine tic, the execution sequence handles closing windows via two critical safeguards:
* **The Input Lock (`isModalOpen`):** Suspends the `update()` physics engine entirely when a project modal is drawn.
* **The Auto-Eject Routine:** Upon interacting with a node, the algorithm dynamically calculates the closest clear floor coordinates (`0`) around that specific tile and programmatically moves the player character to that safe spot. This ensures that when the modal is closed, the player doesn't trigger an infinite loop.

---

## 💻 Tech Stack

* **Render Layer:** Vanilla HTML5 Canvas (Hardware accelerated drawing)
* **Style Framework:** Tailwind CSS (Fluid utility layers & backdrop filters)
* **Typography:** Google Fonts (*Press Start 2P* for retro UI / *Plus Jakarta Sans* for readable copy)
* **Core Language:** Pure Vanilla ECMAScript (Zero bloated heavy game engine overhead)

---

## ⚙️ Direct Deployment & Setup

This portfolio engine runs completely standalone without needing to manage heavy build pipes, Node modules, or webpack dependencies.

1. Clone or download the repository:
   ```bash
   git clone [https://github.com/your-username/developer-dungeon.git](https://github.com/your-username/developer-dungeon.git)
