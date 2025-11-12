# Self-Driving Car 

A minimal, dependency-free demo of a self-driving car that learns to drive using a simple neural network and evolutionary mutation. Runs entirely in the browser.

## Features
- Road, car physics, and collision detection
- Ray sensors for environment perception
- Tiny feed-forward neural network with visualization
- Evolution via mutation and local storage persistence (Save/Trash buttons)
- Traffic cars to avoid

## Quick start
- Double-click `index.html` to open in your browser, or run a local server:
  - Python: `python -m http.server 8000` then open http://localhost:8000/
  - Node (npx): `npx serve` then open the shown URL

## How it works
- Each AI car uses sensors -> inputs to a neural network -> outputs map to actions (forward/left/right/reverse).
- On load, N cars are spawned; if a "best brain" exists in `localStorage`, it is cloned to all cars and mutated for exploration.
- Click 💾 Save to persist the best-performing brain; 🗑️ Trash to clear it.

## Controls
- Default is AI. There is no keyboard control unless you switch a car to `KEYS` in code.
- Buttons (middle of the screen):
  - 💾 Save: store current best network in your browser
  - 🗑️ Trash: remove saved network

## Tuning
Edit `main.js`:
- `const N = 300;` — population size (raise/lower based on performance)
- `NeuralNetwork.mutate(..., 0.3);` — mutation strength (0–1; higher explores more)
- Starting lane is randomized for diversity

## Project structure
- `index.html` — canvases + script includes
- `style.css` — layout/style
- `main.js` — app entry, simulation loop, population management
- `car.js` — car physics, drawing, and AI control wiring
- `sensor.js` — ray casting sensor
- `network.js` — neural network + mutation
- `visualizer.js` — neural net visualization
- `road.js` — road geometry and drawing
- `utils.js` — helpers (lerp, intersections, colors)
- `car.png` — sprite used for the car mask

## Notes
- This repository was cleaned up to fix file name mismatches, ensure UTF‑8 text files, and bump exploration defaults.
- Works as a static site; you can enable GitHub Pages (Settings → Pages → Source: `main` branch, `/` root) to host a live demo.

## Disclaimer
This is an educational demo, not a driving stack. No external libraries are used.
