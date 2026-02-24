# ♻️ PET Bottle Classifier — Waste Management System

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.12+-orange)
![MobileNetV2](https://img.shields.io/badge/Model-MobileNetV2-green)
![Status](https://img.shields.io/badge/Status-In%20Development-yellow)

---

## 📌 Problem Statement

Plastic pollution is one of the most critical environmental challenges of our time. In colleges, public spaces, and urban areas, thousands of PET (Polyethylene Terephthalate) plastic bottles are discarded every day without proper segregation. These bottles, if collected and recycled correctly, can be converted into **3D printing filament** — a valuable and sustainable material used to manufacture useful products like phone stands, pen holders, and keychains.

The core challenge is **identifying and segregating PET bottles from other types of plastic waste automatically**, without human intervention. Existing waste bins do not differentiate between plastic types, leading to contamination of recyclable material and missed opportunities for upcycling.

---

## 💡 Proposed Solution

This project presents an **AI-powered PET bottle detection and sorting system** that uses **Computer Vision (CV)** and **Deep Learning** to automatically identify whether a plastic bottle is made of PET or not — and physically sort it into the correct bin section.

### How It Works

A custom-designed **dual-chamber bin** is used:
- The bin is cylindrical and divided into **two halves** by a center divider
- A **lightweight shifting plate** sits on top of the bin
- A **camera mounted on an arch** above the plate captures an image of the bottle when placed
- The trained ML model analyses the image and classifies it as **PET or Non-PET**
- Based on the result, the plate **shifts left (PET)** or **shifts right (Non-PET)**, dropping the bottle into the correct chamber

---

## 🔄 System Workflow

```
Bottle placed on plate
        ↓
Camera captures image (arch-mounted)
        ↓
ML Model analyses → PET or Non-PET?
        ↓
GPIO signal sent to servo motor
        ↓
Plate shifts → Bottle drops into correct bin
```

---

## 🧠 ML Model

| Property | Details |
|----------|---------|
| Architecture | MobileNetV2 (Transfer Learning) |
| Task | Binary Classification (PET / Non-PET) |
| Input Size | 224 x 224 x 3 |
| Training Strategy | Phase 1: Head only → Phase 2: Fine-tuning |
| Dataset Size | 25,000 images |
| Class Handling | Class weights for imbalance correction |

---

## 📂 Project Structure

```
PET_Classifier/
├── dataset/
│   ├── train/
│   │   ├── PET/
│   │   └── Non_PET/
│   ├── val/
│   │   ├── PET/
│   │   └── Non_PET/
│   └── test/
│       ├── PET/
│       └── Non_PET/
├── models/
│   └── best_model.h5
├── src/
│   ├── reorganize_dataset.py
│   ├── train.py
│   ├── evaluate.py
│   └── predict_realtime.py
└── README.md
```

---

## 🛠️ Tech Stack

- **Python 3.10+**
- **TensorFlow / Keras** — Model training
- **OpenCV** — Real-time camera feed
- **MobileNetV2** — Pretrained base model
- **NumPy / Matplotlib** — Data handling & visualization
- **Scikit-learn** — Evaluation metrics

---

## 📦 Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/PET-Bottle-Classifier.git
cd PET-Bottle-Classifier

# Create virtual environment
python -m venv pet_env
pet_env\Scripts\activate

# Install dependencies
pip install tensorflow opencv-python numpy matplotlib scikit-learn pillow tqdm
```

---

## 🚀 Usage

**Step 1 — Reorganize Dataset**
```bash
python src/reorganize_dataset.py
```

**Step 2 — Train the Model**
```bash
python src/train.py
```

**Step 3 — Real-time Detection**
```bash
python src/predict_realtime.py
```

---

## 🌍 Real World Impact

- Reduces plastic contamination in recycling streams
- Enables upcycling of PET waste into 3D printing filament
- Promotes sustainable product manufacturing
- Reduces dependency on virgin plastic for filament production
- Can be deployed in colleges, hostels, offices, and public spaces

---

## 👩‍💻 Developed By

**Manujana Nagaraj**
AI & ML Engineer | Waste Management Innovation
> Part of the **Waste Management Systems** project —
> *Turning Waste Plastic Bottles into Sustainable Products*
