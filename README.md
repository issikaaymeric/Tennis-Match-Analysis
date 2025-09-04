# 🎾 Tennis Ball Detector (YOLOv8)

This project implements an **object detection model** using [Ultralytics YOLOv8](https://github.com/ultralytics/ultralytics) to detect tennis balls in images and videos. The model is trained on a dataset from [Roboflow](https://universe.roboflow.com/viren-dhanwani/tennis-ball-detection/dataset/6) and can be used for sports analysis, automation, or as a component in a larger tennis analytics system.

---
## 📥 Download Models & Data

Since models/datasets are too large for GitHub, download them here:

👉 [Google Drive – Folder](https://drive.google.com/drive/folders/1DWnQYHOVqAFQ02NoZALCIQbvCd0nDWgl?usp=sharing)

After downloading:

* Extract into `backend/models/` or the appropriate folder.
* Update paths in `main.py` if needed.
---

## 📂 Project Structure

```
tennis-ball-detection-6/
│
├── train/
│   └── images/      # training images
│   └── labels/      # YOLO-format labels
│
├── valid/
│   └── images/      # validation images
│   └── labels/
│
├── test/
│   └── images/      # test images
│   └── labels/
│
├── data.yaml        
```

---

## ⚙️ Setup

### 1. Clone Repository

```bash
git clone https://github.com/your-username/tennis-ball-detector.git
cd tennis-ball-detector
```

### 2. Install Dependencies

Make sure you have **Python 3.10+** installed, then install requirements:

```bash
pip install ultralytics
```

---

## 🚀 Training the Model

Run the following command to start training:

```bash
yolo task=detect mode=train model=yolov8n.pt data=tennis-ball-detection-6/data.yaml epochs=100 imgsz=640 batch=16 name=tennis_ball_detector
```

* `yolov8n.pt` → lightweight YOLOv8 Nano model
* `epochs=100` → number of training iterations
* `imgsz=640` → input image size
* `batch=16` → batch size per iteration

Training outputs (weights, logs, results) will be saved under:

```
runs/detect/tennis_ball_detector/
```

---

## 🧪 Validation & Testing

To evaluate the trained model:

```bash
yolo task=detect mode=val model=runs/detect/tennis_ball_detector/weights/best.pt data=tennis-ball-detection-6/data.yaml
```

To run inference on test images:

```bash
yolo task=detect mode=predict model=runs/detect/tennis_ball_detector/weights/best.pt source=tennis-ball-detection-6/test/images
```

---

## 📊 Results

After training, you’ll obtain:

* **Precision, Recall, and mAP scores**
* Visualized predictions on validation and test images




