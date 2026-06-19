# quantum-neural-ar

Real-time 3D neural network controlled entirely by hand gestures : no backend, no install, runs in the browser.

![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![Three.js](https://img.shields.io/badge/Three.js-000000?style=flat&logo=threedotjs&logoColor=white)
![MediaPipe](https://img.shields.io/badge/MediaPipe-0097A7?style=flat&logo=google&logoColor=white)
![Web Audio API](https://img.shields.io/badge/Web_Audio_API-FF6B35?style=flat)
![License: MIT](https://img.shields.io/badge/License-MIT-purple.svg)

---

## What it is

A browser-based creative-coding project that renders a dynamic 3D neural network and lets you control it entirely through hand gestures via your webcam. Move the structure, fire energy pulses, zoom, trigger particle fireworks all hands-free.

No frameworks. No install. Open the HTML file and go.

---

## Demo

> Enable camera access when prompted. Gesture controls activate immediately after.

---

## Gesture Controls

| Gesture                  | Hand                | What it does                                           |
| ------------------------ | ------------------- | ------------------------------------------------------ |
| ✋ Hover                 | Any                 | Casts a moving light source; tilts the network         |
| 🤌 Pinch (Index + Thumb) | Any                 | Fires an energy pulse wave through the network         |
| 🫰 Snap (Middle + Thumb) | Any                 | Triggers a crackle burst + electric particle explosion |
| 🖐 Open Palm             | Left only           | Zooms in (continuous)                                  |
| ✊ Fist                  | Left only           | Zooms out (continuous)                                 |
| 🤟 Rock-On (both hands)  | Both simultaneously | Toggles fireworks mode; hides the neural network       |

---

## Features

- 3 neural formations: Crystalline Sphere, Helix Lattice, Fractal Web
- 3 color themes: Purple Nebula, Sunset Fire, Ocean Aurora
- Real-time WebGL rendering with Unreal Bloom post-processing
- Spatial audio: ambient waterfall, water-drop tones, white-noise crackle via Tone.js
- Energy pulse waves that propagate through the node-connection graph
- Physics-based fireworks system with gravity arc and additive blending
- Density slider to control node/connection count
- Mouse and touch fallback for non-webcam environments

---

## Stack

| Layer           | Technology                                                                                  |
| --------------- | ------------------------------------------------------------------------------------------- |
| 3D Rendering    | [Three.js](https://threejs.org/) r162                                                       |
| Hand Tracking   | [MediaPipe Hands](https://developers.google.com/mediapipe/solutions/vision/hand_landmarker) |
| Post-processing | UnrealBloomPass, EffectComposer                                                             |
| Audio           | [Tone.js](https://tonejs.github.io/) 14.8                                                   |
| Camera          | MediaPipe Camera Utils                                                                      |
| Font            | Outfit (Google Fonts)                                                                       |
| Runtime         | Vanilla JS (ES Modules via importmap)                                                       |

Zero build tools. Zero dependencies to install. Everything loads from CDN.

---

## Getting Started

```bash
git clone https://github.com/Aaricacoding/quantum-neural-ar.git
cd quantum-neural-ar
```

Then just open `index.html` in any Chromium-based browser (Chrome, Edge, Brave). Firefox works but MediaPipe performs better on Chromium.

> Camera and microphone permissions are required for gesture detection and audio.

---

## Project Structure

```
quantum-neural-ar/
├── index.html       # Entire app — single file
└── README.md
```

---

## How the gesture detection works

MediaPipe Hands tracks 21 landmarks per hand at up to 30fps. Gestures are derived from landmark ratios:

- **Pinch:** Euclidean distance between tip of index (landmark 8) and tip of thumb (landmark 4) < 5% of frame width
- **Snap:** Same distance check on middle finger tip (landmark 12) and thumb tip
- **Open/Fist:** Average fingertip-to-wrist distance normalized by palm size
- **Rock-On 🤟:** Index up, pinky up, middle + ring down, thumb extended outward — checked on both detected hands simultaneously

---

## License

MIT © 2026 [Aarica Raj](https://github.com/Aaricacoding)
