# CloneTracker 🧍‍♂️🎯

A simple pose detection app using [MediaPipe](https://github.com/google/mediapipe) and OpenCV, with a square frame for precise body tracking. Built in Python.

## 📸 Features

- Real-time body pose detection using webcam
- Square-shaped centered camera frame (900×900)
- MediaPipe Pose landmark visualization
- Works with any webcam (laptop/USB)

## 🛠 Requirements

- Python 3.9–3.11
- OpenCV
- MediaPipe
- NumPy

## 🔧 Setup

```bash
git clone https://github.com/Prasen8/Clone_Tracker.git
cd CloneTracker

# Create virtual environment (optional but recommended)
python -m venv venv
venv\Scripts\activate   # Windows

# Install dependencies
pip install -r requirements.txt

# Run the app
python test.py

📁 Folder Structure
bash
Copy
Edit
CloneTracker/
├── test.py              # Main pose tracking script
├── requirements.txt     # Python dependencies
├── .gitignore
└── README.md
```
### 🔧 Built by [Prasen Nimje]


📍 Focused on AI + MediaPipe + Computer Vision 

## Code Explaination :

# 🤖 Clone Tracker - Pose Detection with MediaPipe & OpenCV

## 🧠 Project Overview

Clone Tracker is a real-time human pose tracking system using MediaPipe, OpenCV, and Matplotlib. It captures webcam video input, detects body landmarks, mirrors them to create a "clone" effect, and visualizes both 2D and 3D poses with dynamic neon trails and animations.

---

## 🚀 Features

* Real-time pose detection
* Mirror-clone visualization
* Neon glowing joint animations
* 3D pose rendering using Matplotlib
* Dynamic trail effect to show motion
* Scanning UI when no pose is detected

---

## 🔧 Libraries Used

* `OpenCV` - For real-time video and UI display
* `MediaPipe` - Pose detection with landmark tracking
* `NumPy` - Efficient array operations
* `Matplotlib` - Real-time 3D plotting
* `math`, `time` - For timing and animation effects

---

## 🧩 Code Breakdown

### 1. **Initialize Pose Detector**

```python
mp_pose = mp.solutions.pose
pose = mp_pose.Pose(...)
```

Loads MediaPipe's Pose model with live tracking configurations.

### 2. **Webcam Setup**

```python
cap = cv2.VideoCapture(0)
cap.set(cv2.CAP_PROP_FRAME_WIDTH, 1000)
cap.set(cv2.CAP_PROP_FRAME_HEIGHT, 900)
```

Starts webcam and sets the video frame size.

### 3. **3D Plot Initialization**

```python
fig = plt.figure(...)
ax = fig.add_subplot(...)
```

Creates a Matplotlib 3D plot to show pose landmarks in 3D space.

### 4. **Main Loop**

Captures each frame, processes pose, and visualizes.

#### a. **Convert Frame and Detect Landmarks**

```python
frame_rgb = cv2.cvtColor(frame, cv2.COLOR_BGR2RGB)
results = pose.process(frame_rgb)
```

Converts BGR to RGB and applies MediaPipe pose detection.

#### b. **Clone Effect (Mirrored Landmarks)**

```python
clone_landmarks_2d = [(int((1 - lm.x) * width), int(lm.y * height)) ...]
```

Landmarks are mirrored horizontally to simulate a clone effect.

#### c. **Neon Coloring and Pulse Animation**

```python
gradient_color = get_gradient_color(time)
```

Creates a pulsing neon color using HSL gradient logic.

#### d. **Drawing Connections and Joints**

```python
draw_smooth_line(...) and draw_smooth_circle(...)
```

Adds joints and bones with glowing effect using custom functions.

#### e. **Motion Trail Effect**

```python
trail_points.append(clone_joint_points.copy())
```

Stores recent joint positions to draw fading trails.

#### f. **3D Plot Rendering**

```python
ax.plot(...), ax.scatter(...)
```

Plots mirrored clone in 3D every 6 frames.

#### g. **Fallback Scanning Message**

Displays "SCANNING..." when no person is detected.

---

## 📷 Screenshot / Demo

You can add demo GIF or image here:

```
![Clone Tracker Demo](demo.gif)
```

---

## 💡 How to Use

```bash
git clone https://github.com/Prasen8/Clone_Tracker.git
cd Clone_Tracker
pip install -r requirements.txt
python test.py
```

Press `Q` to quit the webcam window.

---

## 👨‍💻 Built With ❤️ by Prasen Nimje

A passion project exploring computer vision, pose estimation, and real-time animation.

---






