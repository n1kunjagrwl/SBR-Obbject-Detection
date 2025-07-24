# SBR-Obbject-Detection
OBJECT DETECTION IMPLEMENTATION ON SELF-BALANCING BOT

# 🤖 Intelligent Self-Balancing Robot with Object Detection

This repository supports the research paper:

[**"An Intelligent Self-Balancing Robot with Integrated Object Detection Using MobileNetV2 and PID Control"**](https://ieeexplore.ieee.org/document/10925773)

Authors:  
Rohit Mittal, Nikunj Agarwal, Praveen Kumar Shukla, Narendra Khatri  
Manipal University Jaipur, MAHE, India


## 🧠 Abstract

This paper presents the design and development of a self-balancing two-wheeled robot capable of detecting hazardous objects in a household environment. The stability issue in two-wheeled robots is addressed using a Proportional Integral Derivative (PID) controller to maintain vertical equilibrium, while object detection is achieved via the MobileNetV2 framework, a convolutional neural network (CNN) architecture. A camera, interfaced with a Raspberry Pi, continuously captures video frames, identifying potentially dangerous objects. Upon detection, both the input frame and the detected object are stored for further analysis. The robot’s balance is maintained through the use of an MPU6050 sensor, which provides feedback on the robot’s angular inclination. This feedback is processed by the PID controller to adjust the direction and speed of the DC motors, ensuring the robot remains upright. The design phase included mechanical system planning, ensuring stability and efficiency in the robot’s operation. The final system integrates both object detection and self-balancing, providing a safe and interactive toy for children. This innovative combination of object detection and self-balancing mechanisms demonstrates the practical application of control theory and computer vision techniques in robotic systems. The system offers insights into the effective integration of PID control and object detection using modern neural network architectures.

This work presents a compact, mobile robotic system designed for **real-time object detection in dynamic home environments**. The core of the system is a lightweight **deep learning pipeline** deployed on a Raspberry Pi 4, capable of recognizing **potentially hazardous household objects** using **MobileNetV2** and **YOLOv5** models. To support smooth visual inference, the robot integrates a **PID-based self-balancing mechanism**, ensuring a stable visual frame even during motion.

Unlike traditional vision systems on static platforms, this robot introduces a **mobility-first computer vision architecture**, where real-time balance stabilization **enhances the reliability of object detection** on edge hardware.

## 🎯 Objectives

- Deploy **deep learning models** for detecting hazardous objects near children (e.g., knives, electronic appliances, sharp toys).
- Maintain **real-time inference** on low-power hardware (Raspberry Pi 4).
- Use **self-balancing mechanics** to enable smooth, jitter-free video capture and inference while in motion.


## 🧰 System Architecture

### Object Detection Stack

| Component          | Description                                              |
|-------------------|----------------------------------------------------------|
| **Camera Module** | Raspberry Pi Camera v2 for real-time video feed          |
| **Model 1**       | SSD MobileNetV2 (TFLite, COCO pretrained)                |
| **Model 2**       | YOLOv5s (PyTorch, quantized for Pi deployment)           |
| **Data**          | MS COCO pretrained classes + custom subset (optional)    |
| **Key Classes**   | `knife`, `scissors`, `spoon`, `fork`, `laptop`, `toaster`, `microwave`, `lego`, `mobile phone` |

**Detection Pipeline:**

1. Capture frames via Pi camera at ~2 FPS
2. Pass through MobileNetV2 or YOLOv5
3. Post-process bounding boxes and store detection snapshots
4. Maintain inference-log with timestamps and frame references


### Stability System (Support Layer)

| Component         | Role                                             |
|------------------|--------------------------------------------------|
| **MPU6050**       | IMU sensor for real-time tilt data               |
| **PID Controller**| Implements feedback loop for balance correction |
| **Motors**        | Dual BO motors controlled via L298N motor driver|
| **Chassis**       | Center-aligned weight for minimal torque drift  |

The **self-balancing mechanism** minimizes vibration-induced blur and tracking instability, which is crucial for robust inference in domestic spaces.


## 📊 Benchmark Results

| Metric                     | SSD MobileNetV2 | YOLOv5s         |
|---------------------------|-----------------|-----------------|
| COCO mAP                  | 22.0             | 37.4            |
| Inference Time (avg)      | 374.7 ms         | 1097.3 ms       |
| Effective FPS (on-device) | 2.67             | 0.91            |
| Model Size                | ~14 MB           | ~27 MB          |

Both models were benchmarked directly on Raspberry Pi 4 without external accelerators.


## 🚀 Contributions

- 📦 **End-to-end deployment** of MobileNetV2 + YOLOv5 on mobile robotic hardware
- ⚖️ **PID-based mechanical stabilization** to ensure inference reliability
- 📽️ Real-time **object detection on moving platform**
- 🧪 Extensive **empirical tuning** of PID gains and performance evaluation
- ⚙️ Built using **pure Python, OpenCV, PyTorch/TensorFlow**, and standard Raspberry Pi libraries



## 📄 Access the Research Paper

📥 [**IEEE**](https://ieeexplore.ieee.org/document/10925773)

---

## 📚 Citation

If you use or reference this work, please cite:

```bibtex
@INPROCEEDINGS{10925773,
  author={Mittal, Rohit and Agarwal, Nikunj and Shukla, Praveen Kumar and Khatri, Narendra},
  booktitle={2024 International Conference on Intelligent & Innovative Practices in Engineering & Management (IIPEM)}, 
  title={An Intelligent Self-Balancing Robot with Integrated Object Detection Using MobileNetV2 and PID Control}, 
  year={2024},
  volume={},
  number={},
  pages={1-5},
  keywords={YOLO;Computer vision;PI control;Computer architecture;Robot sensing systems;Stability analysis;Object recognition;Convolutional neural networks;PD control;Robots;Self-Balancing;OpenCV;Raspberry Pi;Object Detection;MobileNetV2;Robot;CNN;PID;MPU6050},
  doi={10.1109/IIPEM62726.2024.10925773}}

