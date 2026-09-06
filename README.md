# S.M.A.R.T. — Spinal Monitoring & Alert Real-Time Tracker

**S.M.A.R.T.** is a standalone, edge-AI powered embedded system designed to provide non-intrusive posture correction and drowsiness detection in physical study and work environments. Built on a Raspberry Pi architecture, it uses computer vision to monitor cervical spine load and eye closure in real time without requiring an open laptop or wearable straps.

---

## Key Features

* **Non-Intrusive Edge Monitoring:** Runs locally on Raspberry Pi with a USB HD webcam—no cloud dependencies or active laptop screens required.
* **Real-Time Neck Flexion Analysis:** Uses MediaPipe Pose estimation to detect neck flexion angles exceeding $30^\circ$ (mitigating forward head posture strain).
* **Fatigue & Drowsiness Tracking:** Implements the Eye Aspect Ratio (EAR) algorithm via MediaPipe Face Mesh to identify micro-sleep events ($\text{EAR} < 0.2$).
* **Multimodal Feedback Interventions:** Instantly alerts the user with dynamic WS2812B RGB LED color shifts and auditory cues via Bluetooth speaker.
* **Lightweight Embedded Logging:** Stores posture metrics and session analytics locally in an SQLite3 database for trend tracking.

---

## Tech Stack & Hardware

* **Hardware:** Raspberry Pi 4 / Zero 2 W, USB HD Webcam, WS2812B RGB LED Module, Bluetooth Speaker.
* **Core Languages:** Python 3, Bash.
* **Computer Vision & ML:** OpenCV, MediaPipe (Pose & Face Mesh).
* **Hardware Interfacing & Audio:** `rpi_ws281x`, `gpiozero`, `pygame.mixer`.
* **Database:** SQLite3.
* **Version Control:** Git & GitHub.

---

## Architecture Overview

1. **Module 1 (Data Capture):** Captures $640\times480$ video frames and formats RGB matrix arrays for inference.
2. **Module 2 (AI Engine):** Computes frame-by-frame neck angle and EAR metrics; triggers an alarm event when thresholds are breached for $>3$ seconds.
3. **Module 3 (Alert & Storage):** Executes visual/auditory interventions and logs session timestamps locally.
