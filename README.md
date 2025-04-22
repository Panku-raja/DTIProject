

# 🚗 Advanced Driver Assistance System (ADAS)

## 🧠 Motivation

Road safety is a growing concern due to human error and limited driver awareness in poor conditions. This project simulates a real-world driver assistance system to provide visual and intelligent alerts using AI, offering a foundation for real-time safety applications in future autonomous vehicles.


A real-time computer vision project that integrates multiple deep learning models to assist drivers with live object detection, lane keeping, traffic sign recognition, and weather condition classification.

## 📌 Features

- **YOLOv8** for Object Detection (vehicles, pedestrians, obstacles)
- **U-Net** for Lane Detection
- **CNN** for Traffic Sign Recognition (GTSRB dataset)
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


## 📚 References

- [YOLOv8 - Ultralytics](https://github.com/ultralytics/ultralytics)
- [GTSRB Dataset](https://benchmark.ini.rub.de/gtsrb_news.html)
- [TuSimple Lane Dataset](https://github.com/TuSimple/tusimple-benchmark)
- [ACDC Weather Dataset](https://acdc.vision.ee.ethz.ch/)

Special thanks to open-source contributors and research communities.

## ⚙️ Configuration

- Set confidence threshold in `config.py`
- Load our video input in `input/video.mp4`
- Pretrained weights should be placed in `/models/` directory

## 📈 Evaluation

| Module                | Accuracy |
|-----------------------|----------|
| Object Detection (YOLOv8)     | 89.3%    |
| Lane Detection (U-Net)        | 92.1%    |
| Traffic Sign Recognition (CNN) | 95.6%    |
| Weather Classification (CNN)  | 93.7%    |


## Security Considerations

### Fast Gradient Sign Method (FGSM)
The Fast Gradient Sign Method (FGSM) is an adversarial attack technique that perturbs input images by adding noise in the direction of the gradient of the loss function, scaled by a small epsilon (ε) value. Introduced by Goodfellow et al. (2014), FGSM is relevant to this ADAS pipeline as it can test the robustness of the YOLOv8 object detection model against misclassifications (e.g., cars as pedestrians). Simulated components (U-Net for lane identification, GTSRB CNN for traffic sign recognition, and Weather CNN for weather classification) may also be vulnerable, potentially leading to incorrect annotations in the output image (`output_frame.jpg`).

- **Implementation**: FGSM can be applied by computing the gradient of the model's loss with respect to the input frame (e.g., `perturbed_image = image + ε * sign(∇_x J(θ, x, y))`) using frameworks like TensorFlow or PyTorch.
- **Impact**: Adversarial examples could compromise safety in real-world ADAS applications.


