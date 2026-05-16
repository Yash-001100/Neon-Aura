# Neon Aura AR

An interactive, browser-based hand-tracking AR experience. Real-time finger detection drives a layered neon visual + audio scene — no install, no build step, just a single HTML file using [MediaPipe Hands](https://google.github.io/mediapipe/solutions/hands).

## Live Demo

Deployed on Railway. Public URL will be added here once the service is up.

## Features

- **Hand skeleton tracking** — up to 2 hands, 21 landmarks each, via MediaPipe Hands.
- **Neon fingertip particles** — fingertips trail sparks that obey gravity and fade out.
- **Pinch shockwaves** — pinch thumb + index to release a colored ripple and a synth zap.
- **Two-hand interactions** — rainbow gradient connectors between matching fingertips, electric arcs when fingertips approach each other, and a slowly rotating mandala formed from all 10 fingertips.
- **Reactive matrix-rain background** — speeds up when your hands move quickly.
- **Continuous audio hum** — when both hands are visible, pitch and volume modulate with the distance between index fingers.
- **5 themes** — Rainbow, Cyberpunk, Lava, Ocean, Galaxy.
- **Live HUD** — FPS, hand count, current gesture (pinch / open hand / fist), and finger spread percentage.

## Getting Started

The fastest way is just to open the live demo above on a desktop or laptop browser with a webcam, grant camera permission, and click **Enter Experience**.

To run locally:

```bash
git clone https://github.com/Yash-001100/Neon-Aura.git
cd Neon-Aura
```

Most browsers require an HTTPS or `localhost` origin for camera access, so opening the file directly with `file://` may not work. Serve it with any static server, for example:

```bash
python -m http.server 8000
# then open http://localhost:8000
```

## Controls

| Gesture | Effect |
| --- | --- |
| Move fingertips | Neon sparks trail your hands |
| Pinch (thumb + index) | Color shockwave + zap sound |
| Bring two hands close together | Lightning arcs between matching fingertips |
| Both hands visible | Rotating mandala forms in the center |
| Open hand / fist | HUD updates with current gesture and spread % |

Click any theme button at the bottom of the screen to switch the color palette.

## Tech

- **MediaPipe Hands** — landmark detection via WASM.
- **HTML5 Canvas** — all visuals (no WebGL or three.js).
- **Web Audio API** — synthesized hum + zap.
- Single-file, vanilla JavaScript. No build step or dependencies to install.

## Browser Support

Tested on Chrome and Edge. Requires WebRTC (`getUserMedia`) and the Web Audio API. Mobile browsers may work but the UI is designed for desktop.

## Deployment

Deployed on [Railway](https://railway.app/) using a minimal Node static file server (`server.js`). Railway auto-detects the Node project from `package.json` and runs `npm start`, which serves `index.html` over the assigned `$PORT`.

To redeploy from a fresh clone:

```bash
npm start          # http://localhost:3000
```

Pushing to the `main` branch on GitHub triggers a new Railway build automatically once the repo is connected.
