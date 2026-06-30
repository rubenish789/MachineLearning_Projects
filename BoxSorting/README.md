# 📦 Box Sorting using YOLO

A computer vision project for detecting and classifying boxes using the YOLO object detection model. The project demonstrates the complete workflow from dataset preparation and model training to inference with a trained model.

## Features

- 📷 Object detection using YOLO
- 🧠 Pre-trained model included (`best.pt`)
- 📊 Training metrics and evaluation results
- 📦 Detection of different box categories
- ⚡ Fast inference on images

---

## Project Structure

```
BoxSorting/
│
├── data.zip                  # Dataset
├── my_model/
│   ├── yolo_detect.py        # Detection script
│   ├── my_model.pt           # Trained model
│   └── train/               # Training results
│       ├── weights/
│       │   ├── best.pt
│       │   └── last.pt
│       ├── results.csv
│       ├── results.png
│       ├── confusion_matrix.png
│       ├── PR_curve.png
│       ├── F1_curve.png
│       └── ...
│
├── photos/
│   ├── broken boxes/
│   ├── ...
│
└── my_model.zip
```

---

## Technologies

- Python
- YOLO
- PyTorch
- OpenCV
- Ultralytics

---

## Dataset

The dataset contains labeled images of boxes used for training and evaluation.

Example categories include:

- Normal boxes
- Broken boxes

*(Modify this section if additional classes are available.)*

---

## Installation

Clone the repository:

```bash
git clone https://github.com/yourusername/BoxSorting.git
cd BoxSorting
```

Install the required packages:

```bash
pip install ultralytics opencv-python torch torchvision
```

---

## Running Detection

Run the detection script:

```bash
python my_model/yolo_detect.py
```

The script loads the trained YOLO model and performs object detection on the selected images or video stream.

---

## Model

The repository includes pretrained weights:

```
my_model/train/weights/best.pt
```

These weights achieved the best validation performance during training.

---

## Training Results

The repository contains training statistics, including:

- Precision-Recall Curve
- F1 Score Curve
- Precision Curve
- Recall Curve
- Confusion Matrix
- Normalized Confusion Matrix
- Training Loss
- Validation Predictions

These files can be found inside:

```
my_model/train/
```

---

## Possible Improvements

- Real-time webcam detection
- Video stream processing
- Deployment on Raspberry Pi or Jetson Nano
- Integration with robotic sorting systems
- Automatic conveyor belt control
- Model optimization for embedded devices

---

## License

This project was developed for educational and research purposes.
