# Gesture-Controlled Virtual Mouse

This project implements a touchless mouse interface using **Computer Vision** and **Hand Gesture Recognition**. By utilizing a standard webcam, it translates real-time hand movements into system-level mouse actions like cursor movement, clicking, and taking screenshots.

---

## 🚀 Features

* **Smooth Cursor Control**: Tracks the index finger tip to move the system pointer across the screen.
* **Intuitive Gestures**:
* **Left Click**: Triggered by bending the index finger.
* **Right Click**: Triggered by bending the middle finger.
* **Double Click**: Triggered by bending both index and middle fingers simultaneously.
* **Screenshot**: Captured by a specific "pinch" gesture (low distance between thumb and index finger).


* **Real-time Feedback**: Displays on-screen text notifications for every action detected (e.g., "Left Click", "Screenshot Taken").
* **Dynamic Scaling**: Automatically maps hand coordinates to your specific screen resolution using `pyautogui`.

---

## 🛠️ Technical Stack

* **MediaPipe**: High-fidelity hand landmark detection (21 points).
* **OpenCV**: Video frame processing and visual overlays.
* **PyAutoGUI & Pynput**: Cross-platform mouse and keyboard automation.
* **NumPy**: Mathematical calculations for gesture angles and landmark distances.

---

## 📂 Project Structure

* `mymain.py`: The core engine handling the webcam feed, MediaPipe processing, and gesture logic.
* `utils.py`: Contains helper functions for geometric calculations, specifically:
* `get_angle()`: Uses $arctan2$ to determine the bend of a finger.
* `get_distance()`: Uses $hypot$ to calculate the Euclidean distance between landmarks.



---

## ⚙️ How It Works

The system uses a mathematical approach to recognize gestures based on the relative positions of hand landmarks:

1. **Angle Calculation**: To detect a "click," the script calculates the angle of the finger joints. If the angle drops below $50^\circ$, it registers as a bent finger.
2. **Distance Mapping**: For movement and screenshots, the distance between the thumb and index finger is measured and interpolated to a scale of 0–1000 for sensitivity.
3. **Coordinate Mapping**: Finger coordinates are flipped (for a mirror effect) and scaled to match the user's screen width and height.

---

## 🚦 Getting Started

### Prerequisites

Ensure you have Python installed, then install the required dependencies:

```bash
pip install opencv-python mediapipe pyautogui pynput numpy

```

### Usage

Run the main script to start the controller:

```bash
python mymain.py

```

* **Move Mouse**: Hold your hand up and move your index finger.
* **Quit**: Press **'q'** on your keyboard to stop the application.

---

Would you like me to add a **troubleshooting section** to this README regarding camera permissions or lighting conditions?
