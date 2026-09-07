# AirType — AI Virtual Keyboard

A browser-based virtual keyboard you "type" on by pinching your thumb and index
finger together over an on-screen key. Hand tracking runs entirely client-side
via [MediaPipe Hands](https://developers.google.com/mediapipe/solutions/vision/hand_landmarker) —
no server, no data leaves your browser.

This is a web port of an original Python/OpenCV + cvzone project, rebuilt in
HTML/JS/Canvas so it can run as a static site on GitHub Pages.

## Run locally

Just open `index.html` in a modern browser (Chrome/Edge recommended) and
click **Enable camera**. No build step or install required.

## Deploy on GitHub Pages

1. Push this repo to GitHub.
2. Go to **Settings → Pages**.
3. Under "Build and deployment", set Source to **Deploy from a branch**,
   branch `main`, folder `/ (root)`.
4. Save. Your site will be live at:
   `https://<your-username>.github.io/<repo-name>/`

## How it works

- `HandLandmarker` (MediaPipe Tasks Vision) tracks 21 hand landmarks per frame.
- Landmark 8 (index fingertip) is used to hover over keys.
- The distance between landmark 4 (thumb tip) and landmark 8 (index tip) is
  used as a pinch/"click" gesture — pinch below a threshold while hovering a
  key to type it.
- A short cooldown after each press prevents accidental repeat keystrokes.

## Notes

- Camera access requires HTTPS (GitHub Pages serves over HTTPS by default) or
  `localhost`.
- Works best with good lighting and one hand clearly in frame.
