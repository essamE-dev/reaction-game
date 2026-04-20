# Reaction Forge

A portfolio-style **reaction timer game** built as a **single static HTML file** using **vanilla JavaScript** and **Three.js**.

The project is designed to demonstrate:

- clean frontend engineering
- precise timing logic with `performance.now()`
- state-driven UI updates
- responsive layout and UX polish
- animated 3D graphics in the browser

---

## Overview

Reaction Forge is a browser game where the player starts a round, waits for a random signal, and then reacts as quickly as possible.

The game includes:

- random delay before the stimulus appears
- false start detection
- reaction-time measurement in milliseconds
- session statistics
- recent-attempt history
- a live Three.js scene used as the visual centrepiece of the game

This revised version uses a **3D sphere** as the main scene object and removes the three informational boxes that previously showed tech, timing, and stimulus details.

---

## Files

- `reaction-game-v2.html` — the complete application in one file
- `README-reaction-game.md` — this documentation file

---

## Features

### Core Gameplay

- **Start / Stop / Reset controls**
- **Random stimulus timing** between **1 and 5 seconds**
- **Accurate reaction timing** using `performance.now()`
- **False start detection** when the player clicks too early
- **Immediate result display** after a valid reaction

### Session Tracking

- **Best reaction time**
- **Average reaction time**
- **Attempt count**
- **Recent attempts panel** with simple performance labels

### 3D / Visual Layer

- Built with **Three.js**
- Central animated **3D sphere**
- Orbit rings, sparks, lighting, and animated motion
- Visual state changes for:
  - idle
  - waiting
  - ready
  - result
  - false start
  - error
- Click-responsive sphere movement inside the stage area

### UX / Accessibility

- Responsive layout for desktop and mobile
- Keyboard support
- Focusable stage area
- Live region messaging for status updates
- Strong contrast and modern UI styling

---

## Controls

### Mouse / Touch

- **Start button**: begins a new round
- **Stop button**: stops the current round
- **Reset button**: clears all stats and history
- **Click the stage** when the signal is active to record your reaction time

### Keyboard

- **Enter**: start a round when Start is available
- **Space**: react during the active signal
- **Esc**: stop the current round

---

## Gameplay Flow

1. The page loads in the **Idle** state.
2. The player presses **Start**.
3. The game enters the **Waiting** state.
4. A random delay is generated between **1000 ms and 5000 ms**.
5. The game switches to the **Ready** state.
6. The player clicks or presses **Space**.
7. The game records the reaction time and shows the result.
8. Stats and recent attempts are updated.

If the player clicks too early during the waiting phase, the game triggers a **False Start** state.

---

## State Management

The game uses a simple state model:

- `idle`
- `waiting`
- `ready`
- `result`
- `false-start`
- `error`

Each state updates:

- the status chip
- the main display text
- the instruction text
- button availability
- the visual treatment of the Three.js scene

This keeps gameplay logic and UI behavior predictable and easier to maintain.

---

## Technical Notes

### Timing

Reaction measurement uses:

```js
performance.now()
```

This gives higher-precision timing than `Date.now()` and is better suited for millisecond-sensitive interaction.

### Random Delay

The stimulus delay is generated in this range:

```js
1000 ms to 5000 ms
```

That prevents the player from anticipating a fixed pattern.

### Three.js

The 3D scene includes:

- `PerspectiveCamera`
- ambient, directional, and point lighting
- a main sphere mesh
- a wireframe core sphere
- orbit rings
- animated spark elements
- a render loop driven by `requestAnimationFrame`

The code also includes cleanup logic for:

- animation frames
- resize observers
- geometries
- materials
- renderer disposal

---

## Design System

### Main Colors

- Background: `#0F172A`
- Surface: `#1E293B`
- Text: `#F1F5F9`
- Secondary text: `#94A3B8`
- Ready: `#10B981`
- Waiting: `#F59E0B`
- Result: `#3B82F6`
- Error: `#EF4444`

### Typography

- **Inter** for UI and data
- **Outfit** for headings

---

## How to Run

### Option 1: Open directly in the browser

Double-click the HTML file:

- `reaction-game-v2.html`

or right-click it and choose **Open With** your browser.

### Option 2: Use a local server

A local server is often better during development.

#### Python

```bash
python3 -m http.server
```

Then open:

```text
http://localhost:8000
```

---

## Dependency

The project loads Three.js from a CDN:

```html
https://unpkg.com/three@0.164.1/build/three.min.js
```

That means:

- the page can still load locally
- but the 3D scene needs an internet connection unless Three.js is bundled or hosted locally

If Three.js fails to load, the game falls back to a non-3D mode and still remains playable.

---

## Suggested Improvements

Good next enhancements for a stronger portfolio version:

- add a visible FPS/performance-safe mode toggle
- add subtle sound effects with mute control
- add difficulty presets
- add a post-result micro chart of recent attempts
- move Three.js to a local module build instead of CDN
- add automated tests for core game-state transitions
- improve the click-to-sphere coordinate mapping for tighter visual accuracy

---

## Who This Project Is For

This project is suitable as a portfolio piece for showing:

- JavaScript fundamentals
- DOM manipulation
- event handling
- animation handling
- state management
- performance-aware frontend work
- basic creative coding / 3D web graphics skills

---

## Author Notes

This project was intentionally built as a **single-file static artifact** to make it easy to:

- review
- share
- run locally
- include in a portfolio

It is a strong example of combining **interactive UI engineering** with **visual presentation** in a compact frontend build.
