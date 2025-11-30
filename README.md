# Nexora 🧠🎯

## Overview

Nexora is an advanced, GPU-accelerated real-time computer vision and control system designed for high-performance tracking and automation tasks. It leverages deep learning, Kalman filtering, and secure runtime encryption to deliver robust object detection, tracking, and automated control. Primarily for gaming and research environments.

---

## 🚀 Features

- **Real-Time Object Detection & Tracking:**  
  Utilizes a custom YOLO-based neural network for fast and accurate detection of targets (e.g., "ally", "enemy", "head") in live video streams.

- **PID-Controlled Mouse Automation:**  
  Implements a PID controller to smoothly and precisely move the mouse cursor toward detected targets, with customizable sensitivity and aiming multipliers.

- **Kalman Filter-Based Tracking:**  
  Integrates the SORT algorithm for persistent tracking of objects, even across missed detections, ensuring stable and reliable automation.

- **Secure Encrypted Runtime:**  
  All critical modules and model data are encrypted and loaded at runtime, protecting intellectual property and user privacy.

- **Customizable Settings:**  
  Easily adjust parameters such as sensitivity, FOV, target selection, and more via the configuration file.

- **Interactive Terminal Menu:**  
  Provides a simple menu for retrieving your machine ID and starting the main tracking/automation loop.

- **Visual Feedback:**  
  Draws bounding boxes, confidence scores, and labels directly on the screen for real-time feedback.

---

## 🔒 Security & Licensing

- **Encrypted Model & Modules:**  
  All neural network weights and utility modules are stored encrypted and only decrypted at runtime using device-specific keys.

- **Device Binding:**  
  The program generates a unique device ID based on your IP, hardware ID, and username, ensuring only authorized devices can run Nexora.

---

## ⚡ Requirements

- **Windows 10/11**
- **CUDA-compatible GPU**
- **Python 3.8+**
- **TensorFlow (GPU)**
- **Other dependencies:**  
  - cryptography  
  - pynput  
  - termcolor  
  - dxcam  
  - mss  
  - pillow  
  - numpy  
  - tensorflow_probability  
  - keyboard  
  - requests  
  - jwt  
  - keyring  

---

## 📝 Usage

1. **Go to Releases Page**  
Go to [releases](https://github.com/ShadowCatlol/Nexora-Aim-Assist/releases) and download the latest release then unzip the folder

2. **Configure settings:**  
   Edit `config.json` to adjust sensitivity, FOV, and other parameters.

3. **Obtain a license**  
   Go to the [discord server](https://discord.gg/28vY89jV7b) to obtain a license

4. **Run Nexora:**  
   ```
   start run.bat
   ```

5. **Menu Options:**  
   - **Get Machine-ID:**  
     Retrieve your encrypted device ID for licensing.
   - **Start Aimbot:**  
     Launch the real-time tracking and automation loop.

---

### 📄 Nexora `config.json` In-Depth Guide

The `config.json` file is the central configuration for Nexora. It allows you to fine-tune the behavior, performance, and security of the program. Below is a detailed explanation of each setting:

### 🖥️ GPU & Performance

- **`gpu_mem_size`**  
  *Type:* `number` (GB)  
  *Purpose:* How much GPU memory Nexora should allocate.  
  *Tip:* Set this to less than your total GPU memory to avoid crashes.

---

### 🎯 Aim & Control

- **`sensitivity`**  
  *Type:* `number`  
  *Purpose:* Controls how fast the mouse moves toward targets. Higher values = faster movement.

- **`aiming_multiplier`**  
  *Type:* `number`  
  *Purpose:* Multiplies the aiming speed for fine-tuning responsiveness.

- **`shooting_multiplier`**  
  *Type:* `number`  
  *Purpose:* Multiplies mouse movement speed when shooting.

- **`activate_on_button`**  
  *Type:* `string` (`"left"` or `"right"`)  
  *Purpose:* Which mouse button activates aim assist.

---

### 👁️ Field of View & Display

- **`fov`**  
  *Type:* `number` (degrees)  
  *Purpose:* Sets the detection field of view for targets.

- **`aspect_ratio`**  
  *Type:* `number`  
  *Purpose:* Sets the screen aspect ratio.  
  *Examples:*  
    - 16:9 → `1.7777777778`  
    - 4:3 → `1.3333333333`  
    - 21:9 → `2.3333333333`

---

### ⚡ Speed & Precision

- **`speed`**  
  *Type:* `number`  
  *Purpose:* Additional multiplier for mouse movement speed.

- **`error_correction`**  
  *Type:* `number`  
  *Purpose:* Corrects small persistent errors (integral term in PID control).

- **`braking_strength`**  
  *Type:* `number`  
  *Purpose:* Controls how quickly the mouse slows down near the target (derivative term in PID).

---

### 🕹️ Advanced Control

- **`quarter_turn`**  
  *Type:* `number`  
  *Purpose:* Advanced setting for mouse movement scaling.  
  *Tip:* Leave default unless you know what you're doing.

---

### 📦 Detection & Tracking

- **`min_presence_score`**  
  *Type:* `number`  
  *Purpose:* Minimum confidence score for a detection to be considered valid.

- **`max_iou`**  
  *Type:* `number`  
  *Purpose:* Maximum allowed overlap (Intersection over Union) between boxes for tracking.

---

### 🔫 ADS (Aim Down Sights) Settings

- **`ads_tolerance`**  
  *Type:* `number`  
  *Purpose:* Number of frames to tolerate before disabling shooting if the target is lost.

- **`ads_time`**  
  *Type:* `number` (seconds)  
  *Purpose:* Minimum time to stay in ADS mode.

---

### 🖥️ Monitor Settings

- **`monitor_index`**  
  *Type:* `number`  
  *Purpose:* Which monitor to use for detection (1 = primary).

- **`monitor_count`**  
  *Type:* `number`  
  *Purpose:* Total number of monitors connected.

---

### 🎯 Targeting & Automation

- **`target_head`**  
  *Type:* `boolean`  
  *Purpose:* Prioritize aiming at the head.

- **`single_shot`**  
  *Type:* `boolean`  
  *Purpose:* Enable single-shot firing mode.

- **`first_person`**  
  *Type:* `boolean`  
  *Purpose:* Optimize for first-person games.

- **`on_screen`**  
  *Type:* `boolean`  
  *Purpose:* Draw overlays and feedback on the screen.

---

### 🖱️ Mouse & Visuals

- **`center_offset`**  
  *Type:* `array` `[x, y]`  
  *Purpose:* Offset for the aiming center (pixels).

- **`circle_size`**  
  *Type:* `number`  
  *Purpose:* Size of the detection region as a fraction of the screen.

- **`pulldown_rate`**  
  *Type:* `number`  
  *Purpose:* Rate at which the mouse pulls down (useful for recoil control).

- **`line_thickness`**  
  *Type:* `number`  
  *Purpose:* Thickness of bounding box lines in the overlay.

---

### 📝 Example

```json
{
    "gpu_mem_size": 8,
    "sensitivity": 1.25,
    "aiming_multiplier": 1,
    "shooting_multiplier": 1.5,
    "activate_on_button": "right",
    "fov": 90,
    "aspect_ratio": 1.7777777778,
    "speed": 1,
    "error_correction": 0.02,
    "braking_strength": 0.9,
    "quarter_turn": 1600,
    "min_presence_score": 0.8,
    "max_iou": 0.5,
    "ads_tolerance": 15,
    "ads_time": 0.02,
    "monitor_index": 1,
    "monitor_count": 2,
    "target_head": true,
    "single_shot": false,
    "first_person": true,
    "on_screen": true,
    "center_offset": [0, 40],
    "circle_size": 0.15,
    "pulldown_rate": 5,
    "line_thickness": 4
}
```

---

### 💡 Tips

- Adjust `sensitivity`, `aiming_multiplier`, and `speed` for your preferred aiming feel.
- Set `target_head` to `true` for headshots, or `false` for body shots.
- Use `on_screen` to enable/disable visual overlays.

---

## 🛡️ Disclaimer

Nexora is intended for research and educational purposes only.  
**Do not use in violation of any software's terms of service.**

---

## 🤝 Support


For help, licensing, or updates, join the official [Discord](https://discord.gg/28vY89jV7b)



