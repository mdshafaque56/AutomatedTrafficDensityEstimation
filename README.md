
### Intelligent Transportation Systems - Course Project C - NIT Calicut (NITC)
# *Advanced Vehicle Trajectory & Traffic Event Analysis*  

This repository contains the code and analysis for **ITS Course Project C**, focusing on **vehicle trajectory extraction, event detection, and traffic flow characterization** using drone videos and sensor fusion.

This README is designed as an **interactive guide** to run, understand, and extend the project smoothly. Start with Quick Start, then explore the guided sections for deeper customization and insights.  

---

## 1. Project Summary  

Project C builds upon automated trajectory extraction methods to include:  
- **Advanced trajectory cleaning and smoothing**  
- **Event detection** such as stops, accelerations, lane changes  
- **Traffic parameters estimation** for individual vehicles and aggregates (headway, time gaps, density)  
- Support for **multi-modal inputs** including drone video and supplemental sensor data  

It integrates Python-based CV (OpenCV), detection (YOLOv8), filtering, and data analysis libraries to output:  

- Vehicle-wise clean trajectories with kinematic states  
- Interactive plots and visual summaries of detected traffic events  
- CSV exports summarizing event times and locations  

---

## 2. Environment Setup  

### 2.1. Dependencies  

Install core libraries:  

```

pip install ultralytics opencv-python-headless pandas numpy matplotlib scikit-learn

```

Optional (for extended visualization or advanced plots):  

```

pip install seaborn

```

Use Python version ≥ 3.9. GPU support is recommended for faster YOLOv8 inference.

---

## 3. Quick Start: Run Complete Pipeline  

With your input drone video (e.g., `input_video.mp4`) and pretrained YOLOv8 model (`yolov8n.pt`), run the main notebook or script that includes these steps:  

1. **Trajectory extraction with detection and tracking**  
2. **Trajectory smoothing & interpolation** to correct jitter and fill occlusions  
3. **Event detection** using velocity/acceleration thresholds and lane-position analysis  
4. **Traffic analysis summary**, including flow, density, and headway metrics  
5. **Interactive visualization** of trajectories and traffic events  

Typically, this is done by running the notebook `ITS_CP_C.ipynb` top-to-bottom or executing the main driver script.

---

## 4. Modules & Workflow Details  

### 4.1. Trajectory Smoothing  

- Uses **Savitzky-Golay filtering** or polynomial smoothing  
- Interpolates missing frames to maintain continuous vehicle paths  
- Produces smoother derivatives → more reliable speed/acceleration analysis  

### 4.2. Event Detection  

Events are inferred by analyzing smoothed trajectories:  
- **Stop events**: vehicle speed drops below threshold for specified duration  
- **Acceleration/Deceleration**: large changes in velocity over short intervals  
- **Lane changes**: significant lateral displacement across lane boundaries  

Output includes event type, vehicle ID, start/end frames, and timestamps.

### 4.3. Traffic Flow Metrics  

Computes microscopic & macroscopic parameters such as:  
- **Time headway** (difference in passage times between vehicles)  
- **Space headway** (distance between two vehicles)  
- **Density and flow rate** per lane or segment  
- **Average speed**, aggregated over analysis windows  

These provide a quantitative understanding of traffic behavior.

---

## 5. Visualization & Export  

Project generates several forms of output:  

- **Trajectory plots** colored by speed or event type  
- **Time-series plots** of speed, acceleration, lateral movement, etc.  
- **Overlay videos** showing bounding boxes, trajectories, and event markers  
- **CSV exports** containing cleaned trajectories and detected events  

Visualization is mainly achieved using Matplotlib and Seaborn.

---

## 6. Customization & Extension  

You can adapt the system in many ways:  

- Adjust event detection thresholds (`speed_thresh_stop`, `accel_thresh`)  
- Customize lane detection/mapping for multi-lane roads  
- Fuse external sensor data for improved accuracy  
- Modify plotting or export formats  
- Add new event types (e.g., harsh braking, weaving, congestion pockets)  

---

## 7. File Structure  

- `ITS_CP_C.ipynb` — Main notebook with end-to-end pipeline  
- Supporting scripts/modules for:  
  - detection  
  - smoothing  
  - event detection  
  - visualization  
- `data/` — raw input videos and processed CSVs  
- `output/` — trajectory files, event logs, and overlay videos  

---

## 8. Acknowledgements  

This project builds on methodologies from previous vehicle tracking and detection work.  
Tools used include Ultralytics YOLOv8, OpenCV, Pandas, NumPy, Matplotlib, and standard scientific Python libraries.

Feel free to extend or integrate this project for future ITS research and academic purposes.

```

