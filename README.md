# 🤹 Air Juggler

A real-time, gesture-controlled browser game where you keep a ball in the air using your hands — no controller required.

![Game Demo](https://img.shields.io/badge/status-playable-brightgreen) ![JavaScript](https://img.shields.io/badge/language-JavaScript-yellow) ![MediaPipe](https://img.shields.io/badge/AI-MediaPipe%20Hands-blue) ![TensorFlow.js](https://img.shields.io/badge/ML-TensorFlow.js-orange)

---

## 🎮 How It Works

Air Juggler uses your webcam and AI-powered hand tracking to detect the position of your hands in real time. Move your hands in front of the camera to bounce the ball and keep it from hitting the ground. The longer you survive, the higher your score.

---

## ✨ Features

- **Real-time hand tracking** via MediaPipe Hands + TensorFlow.js — runs entirely in the browser, no server needed
- **Live webcam feed** rendered directly onto the game canvas as the background
- **Physics simulation** — gravity, wall bouncing, and velocity-based hand deflection
- **3-second countdown** before each round to get your hands ready
- **Score tracking** by survival time (seconds)
- **Responsive overlay UI** for game start, countdown, and game over states
- **Supports up to 2 hands** simultaneously

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| HTML5 Canvas | Game rendering |
| TensorFlow.js | ML runtime in the browser |
| MediaPipe Hands | Hand landmark detection model |
| Vanilla JavaScript | Game logic & physics |
| CSS3 Animations | UI styling & transitions |
| WebRTC (`getUserMedia`) | Webcam access |

---

## 🚀 Getting Started

### Prerequisites

- A modern browser (Chrome recommended)
- A webcam
- Camera permissions enabled

### Running Locally

```bash
# Clone the repository
git clone https://github.com/your-username/air-juggler.git
cd air-juggler

# Serve with any static file server, e.g.:
npx serve .
# or
python3 -m http.server 8080
```

Then open `http://localhost:8080` in your browser.

> ⚠️ **Important:** The game must be served over HTTP/HTTPS (not opened directly as a `file://` URL) for webcam access and CDN scripts to work correctly.

---

## 📁 Project Structure

```
air-juggler/
├── index.html        # Entry point — loads scripts, defines layout
├── style.css         # Styling, animations, loading overlay
├── game.js           # Game loop, physics, collision detection, rendering
└── handTracking.js   # Webcam setup, MediaPipe Hands integration
```

---

## 🧠 How Hand Tracking Works

1. The webcam stream is captured via `getUserMedia` and fed into a hidden `<video>` element.
2. MediaPipe Hands detects up to 21 landmarks per hand at ~30 FPS.
3. The palm center is calculated by averaging keypoints at the wrist and finger bases (indices 0, 5, 9, 13, 17).
4. The x-coordinate is mirrored to match the flipped video display.
5. Hand positions are passed into the game loop as paddle locations, triggering ball collisions.

---

## 🎯 Gameplay

- **Objective:** Keep the ball from falling off the bottom of the screen
- **Controls:** Move your hands in front of the camera
- **Scoring:** 1 point per second survived
- **Performance ratings:**
  - 🎉 **Amazing!** — 30+ seconds
  - 👏 **Great Job!** — 15–30 seconds
  - 💪 **Game Over!** — Under 15 seconds
