

# 🚗 Advanced Driver Assistance System (ADAS)

A real-time computer vision project that integrates multiple deep learning models to assist drivers with live object detection, lane keeping, traffic sign recognition, and weather condition classification.

## 📌 Features

- **YOLOv8** for Object Detection (vehicles, pedestrians, obstacles)
- **U-Net** for Lane Detection
- **CNN (ResNet/MobileNet)** for Traffic Sign Recognition (GTSRB dataset)
- **CNN** for Weather Classification (Fog, Rain, Clear, etc.)
- **OpenCV Integration** to overlay real-time predictions on video input
- Modular architecture and easy-to-extend code

---

## 🧱 System Architecture

```plaintext
Camera Input -> Frame Preprocessing
      -> YOLOv8 (Object Detection)
      -> U-Net (Lane Detection)
      -> CNN (Traffic Sign)
      -> CNN (Weather)
      -> OpenCV Overlay & UI
      -> Final Display

# 📁 Project Structure

├── yolov8_object_detection/
├── unet_lane_detection/
├── cnn_traffic_sign/
├── cnn_weather_classification/
├── integration_pipeline/
│   └── main_pipeline.py
├── data/
├── requirements.txt
└── README.md

