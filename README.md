# NeuroWave Grid (No libs) — AI Portrait • Story • Music • Auto‑Evolve

An interactive 3D cube‑grid visualizer that reacts to prompts, photos/webcam (MediaPipe FaceMesh), and live audio (file, mic, or shared YouTube tab). Everything runs in the browser with **no frameworks**—just HTML, CSS, and vanilla JS.

> Made with ♥ by [Wiqi Lee](https://x.com/wiqi_lee) — follow for updates.

---

## Demo

https://github.com/YOUR_USERNAME/YOUR_REPO/assets/DEMO_ID

> Tip: After you push this repo, upload a short screen capture to your repo’s *Releases* or directly as a repository asset, then replace the link above. You can also keep a local asset instead:
>
> ```md
> ![Demo](demo.gif)
> ```
> or
> ```md
> <video src="demo.mp4" controls muted playsinline></video>
> ```

---

## What’s New (this build)

- **Unified musical meter** — Bass‑weighted spectrum with attack/release envelope and a light noise gate for **smoother, beat‑true motion**. Drives the grid via `audio.level` (0–1).  
  _Changed area: `makeAudioMeter()` is called from music/mic/tab audio setups; no other logic altered._
- **Optional Story‑mode controls** — The code safely checks (`?.`) if story UI is present, so you can include or exclude those fields without breaking anything.
- **UI Scale (zoom)** — Use the slider to quickly shrink/grow the entire app for recording or layout testing. Works via CSS `zoom` (with `@supports` fallback to `transform: scale()`).
- **Tab Audio capture tips** — Clear instructions for “Share tab audio” + macOS Screen Recording permission for Chrome/Edge.

---

## Features

- **Prompt → Style**: Lightweight CLIP‑style mapping turns keywords into palette, speed, depth, and mode choices.
- **Modes**: Prompt AI, Flow Field, Ripple, Noise, Cellular (CA), Photo Mosaic, Webcam Face, and Story Blend.
- **Photo & Webcam**: Sample colors and luminance to sculpt the grid in 3D; optional FaceMesh heatmap (eyes/brows/mouth).
- **Audio Reactive**: Works with audio files, microphone, or **YouTube tab audio**.
- **Auto‑Evolve**: Randomly rotates through curated prompt styles every 30s (toggleable).
- **Zero frameworks**: Pure HTML/CSS/JS; MediaPipe is loaded from CDN for the face mesh.

---

## Run locally

1. Download or clone the repo.
2. Serve the folder (any static server works). Examples:
   - **VS Code Live Server** or
   - `python3 -m http.server 5500` then open `http://localhost:5500`
3. Open the page in **Chrome or Edge** (recommended).

> Some features (Webcam, Mic, Tab Audio) require **https** or **localhost** due to browser permissions.

---

## Controls & UI

- **Prompt → Style**  
  Type something like `neon cyberpunk stormy waves` and press **Generate**.
- **Modes**  
  Click a mode button: Prompt AI / Flow Field / Ripple / Noise / Cellular / Photo Mosaic / Webcam Face / Story Blend.
- **Photo / Webcam**  
  - Paste an image URL or upload a file.  
  - Toggle **Use Image Colors** to paint the grid tops.  
  - Adjust **Height Strength** to control how much luminance sculpts the grid.  
  - Start/stop **Webcam** to enable FaceMesh influence (brows, mouth, facial area heatmap).
- **Music / Mic**  
  - **Audio file**: choose a local file (the player appears).  
  - **Microphone**: tick **Use microphone** and allow capture.  
  - **YouTube (tab audio)**: click **Use Tab Audio**, select your YT tab and **tick “Share tab audio”**.  
    - On macOS, grant Screen Recording permission to your browser if prompted.
- **Controls**  
  - Grid columns, cube size, height (depth), speed, **UI Scale** (shrink/grow the entire app).  
  - Presets: Ocean Dream / Neon Night / Forest Dawn / Supercell.  
  - Auto‑Evolve toggle to change style every 30s.
- **Credit Overlay**  
  Add “Music: Title — Artist” and an optional link; toggle **Show** to display an on‑canvas credit pill.

---

## Audio reactivity (technical)

The new meter reads the analyser’s spectrum and computes a **bass‑weighted energy** with separate weightings for bass/mid/treble. It applies:
- **Noise gate** (to ignore room hiss),
- **Attack/Release envelope** (fast rise, smooth decay),
- Outputs a normalized `audio.level` in `[0,1]` that is added to each cell’s wave amplitude during `animate()`.

This makes the motion feel **tied to the kick and groove** rather than jittery per‑frame FFT spikes.

---

## Story Blend

Provide ≥2 image URLs (one per line) to crossfade **heights** and **colors** over time. The code is defensive—if the story fields aren’t in the DOM, nothing breaks.

---

## Performance tips

- Fewer columns and smaller cube size improve FPS, especially on laptops.
- Keep the browser window moderate in size or use **UI Scale** to shrink the app during recording.
- Turn off webcam/mic when not used.

---

## Privacy

All processing happens **in your browser**. No servers; no analytics. (Only CDNs for MediaPipe scripts and any images you choose to load.)

---

## Credits

- Core concept & code: **Wiqi Lee** — [X: @wiqi_lee](https://x.com/wiqi_lee)  
- MediaPipe FaceMesh by Google Research team (via JS CDN).

---

## License

MIT — see `LICENSE`.

