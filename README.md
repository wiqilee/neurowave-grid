# NeuroWave Grid — AI Portrait • Story • Music • Auto‑Evolve (Vanilla JS)

An interactive 3D cube‑grid visualizer that responds to prompts, photos/webcam (MediaPipe FaceMesh), and live audio (file, mic, or shared YouTube tab). Everything runs in the browser with **no frameworks**—just HTML, CSS, and vanilla JS.

> Made with ♥ by [Wiqi Lee](https://x.com/wiqi_lee) — follow for updates.

---

## Live Demo
👉 https://wiqilee.github.io/neurowave-grid/

> Tip: In your repo, enable **Settings → Pages → Deploy from branch → `main` / root** so this URL stays live.

---

## What’s New in This Build

- **Improved musical feel** — Bass‑weighted spectrum with a light noise gate plus attack/release smoothing, feeding a normalized `audio.level` \[0–1\] for **smoother, beat‑true motion**. Implemented directly inside the analyser loops for music/mic/tab audio—no extra function required.
- **Subtle baseline motion** — A gentle sine field keeps the grid alive even in quiet passages.
- **Optional Story‑mode controls** — The code uses safe optional chaining (`?.`) so including/excluding Story UI elements will not break anything.
- **UI Scale (zoom)** — Quickly shrink or grow the entire app via CSS `zoom` (with a `transform: scale()` fallback).
- **Tab Audio capture tips** — Clear guidance for “Share tab audio” and macOS Screen Recording permission, right in the UI.

---

## Features

- **Prompt → Style**: Lightweight CLIP‑style mapping turns keywords into palette, speed, depth, and mode choices.
- **Modes**: Prompt AI, Flow Field, Ripple, Noise, Cellular (CA), Photo Mosaic, Webcam Face, Story Blend.
- **Photo & Webcam**: Samples colors and luminance to sculpt the grid; optional FaceMesh heatmap (brows, mouth, facial area).
- **Audio Reactive**: Works with local audio files, **microphone**, or **YouTube tab audio**.
- **Auto‑Evolve**: Rotates curated prompt styles every 30s (toggleable).
- **No frameworks**: Pure HTML/CSS/JS; **MediaPipe FaceMesh is loaded from CDN**.

---

## Quick Start (Local)

1. Clone or download this repo.
2. Serve the folder with any static server. For example:
   ```bash
   # Option A: VS Code Live Server (extension)
   # Option B: Python http.server
   python3 -m http.server 5500
   ```
3. Open `http://localhost:5500` in **Chrome or Edge** (recommended).

> Webcam/Mic/Tab‑Audio require **HTTPS** or **localhost** because of browser security policies.

---

## Controls & UI

- **Prompt → Style** — e.g., `neon cyberpunk stormy waves`, then **Generate**.
- **Modes** — Prompt AI / Flow Field / Ripple / Noise / Cellular / Photo Mosaic / Webcam Face / Story Blend.
- **Photo / Webcam**
  - Paste an image URL or upload a file.
  - Toggle **Use Image Colors** to paint cube tops.
  - Adjust **Height Strength** to set how luminance sculpts the grid.
  - **Webcam**: enable to blend a FaceMesh‑based heatmap (brows, mouth, facial area).
- **Music / Mic**
  - **File**: choose a local audio file (a player appears).
  - **Microphone**: tick **Use microphone** and allow permission.
  - **YouTube (Tab Audio)**: click **Use Tab Audio**, pick your YT tab, and tick **“Share tab audio.”**
    - On macOS, allow **Screen Recording** for your browser if prompted.
- **Controls**
  - Columns, cube size, height (depth), speed, and **UI Scale**.
  - Presets: Ocean Dream / Neon Night / Forest Dawn / Supercell.
  - **Auto‑Evolve**: change style every 30s.

---

## Audio Reactivity (Technical Notes)

The analyser computes a **bass‑weighted energy** from the FFT. A **noise gate** suppresses hiss; an **attack/release envelope** smooths spikes. The final scalar `audio.level \in [0,1]` is added to each cell’s amplitude inside `animate()`, so motion feels **locked to the kick and groove** instead of twitchy per‑bin changes.

---

## Story Blend

Provide ≥2 image URLs (one per line). The app crossfades **heights** and **colors** between frames over time. If the Story UI is absent, the code simply skips Story mode safely.

---

## Performance Tips

- Reduce **Columns** or **Cube Size** for higher FPS on laptops.
- Keep the window moderate in size, or use **UI Scale** when recording.
- Turn off webcam/mic when not needed.

---

## Privacy

All processing happens **in your browser**. No servers, no analytics. (Only CDN scripts for MediaPipe and any images you choose to load.)

---

## Credits

- Core concept & code: **Wiqi Lee** — [X: @wiqi_lee](https://x.com/wiqi_lee)  
- MediaPipe FaceMesh by Google Research (via JS CDN).

---

## License

MIT — **Wiqi Lee** — see [`LICENSE`](./LICENSE).
