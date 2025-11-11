# Real-Time Object Tracking for Behavior Analysis

This project implements **real-time object detection and multi-object tracking** using **YOLOv8** and **DeepSort**. It captures live video from your a camera, tracks multiple objects in real-time, and generates structured data suitable for **behavior analysis**.

---

## Features

- Real-time object detection using **YOLOv8**.
- Multi-object tracking with **DeepSort**.
- Webcam input for live tracking.
- Frame-by-frame structured output for behavior analysis.
- Modular design for integration into larger systems.

---

## Installation

1.  **Clone the repository and navigate to the directory:**

```bash
git clone https://github.com/yourusername/real-time-tracking.git
cd real-time-tracking
```

2.  **Switch to the `phase2` branch:**

```bash
git checkout phase2
```

3.  **Create and activate a virtual environment (optional but recommended):**

```bash
python -m venv venv
# Linux / Mac
source venv/bin/activate
# Windows
venv\Scripts\activate
```

4. **Install the dependencies:**

```bash
pip install ultralytics opencv-python deep_sort_realtime numpy
```

5. **Download the YOLOv8 model:**

```bash
# Example: YOLOv8n (nano model)
wget https://github.com/ultralytics/ultralytics/releases/download/v8.0/yolov8n.pt
```

## Usage

**Run Real-Time Tracking**

```bash
python main.py
```
The script will:
1. Capture live video from your PC camera.
2. Detect objects using YOLOv8.
3. Track objects with DeepSort.
4. Output structured frame data for behavior analysis.

## Data Output
``` python
frame_data = {
    "frame_id": 1,
    "objects": [
        {
            "id": 1,                  # Tracked object ID
            "bbox": [x1, y1, x2, y2], # Bounding box coordinates
            "center": [cx, cy],       # Center coordinates
            "class": 0,               # Detected class ID
            "confidence": 0.85        # Detection confidence
        },
        ...
    ]
}
```
This data can be fed directly into your behavior analysis methods.

## Example Integration

```python
def analyze_behavior(frame_data):
    for obj in frame_data["objects"]:
        # Example: detect objects near the top of the frame
        if obj["center"][1] < 50:
            print(f"Object {obj['id']} is near the top boundary")

```

## Configuration
- YOLOv8 Model: You can switch to a different YOLOv8 model (e.g., yolov8s.pt or yolov8m.pt) by changing the model path in main.py.
- Detection Threshold: Adjust the minimum confidence threshold in main.py to filter weak detections.
- DeepSort Parameters: Modify parameters like max_age or n_init to tune tracking sensitivity.

# References

*   **YOLOv8:** <https://github.com/ultralytics/ultralytics>
*   **DeepSort Realtime:** <https://github.com/levan92/deep_sort_realtime>
*   **OpenCV Documentation:** <https://opencv.org/>