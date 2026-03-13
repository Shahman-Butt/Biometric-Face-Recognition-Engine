# Biometric Face Recognition Engine
### Advanced Computer Vision & Facial Identity Verification


## 📌 Project Overview
The **Biometric Face Recognition Engine** is a high-performance Python application designed to detect, identify, and localize human faces within complex imagery. Utilizing State-of-the-Art (SOTA) deep learning models, the system generates 128-dimensional facial embeddings to achieve high accuracy in identity verification, even in group settings.

This project demonstrates the integration of **Dlib’s Histogram of Oriented Gradients (HOG)** and **Deep Metric Learning** to provide a robust solution for automated facial identification.

---

## 🎯 Key Features
*   **👤 Facial Detection:** High-accuracy localization using HOG-based detectors.
*   **🧬 Biometric Encoding:** Generation of 128D facial descriptors for unique identity mapping.
*   **🔍 Euclidean Distance Comparison:** Real-time matching against known identity databases using optimized distance metrics.
*   **🖼️ Visual Identification:** Dynamic annotation of images with identified names and bounding boxes using Pillow.
*   **📂 Structured Data Management:** Organized directory architecture for managing known registries and test datasets.

---

## 💻 Technologies Used
| Category | Technology |
| :--- | :--- |
| **Language** | Python 3.x |
| **Computer Vision** | OpenCV, face_recognition (Dlib) |
| **Image Processing** | Pillow (PIL) |
| **Algorithms** | Deep Metric Learning, HOG, CNN |
| **Development** | CMake (for Dlib compilation) |

---

## 🏗️ Project Architecture
The system follows a modular pipeline for recognition:
1.  **Ingestion:** Loading raw image data via `face_recognition`.
2.  **Detection:** Identifying face bounding boxes (`top`, `right`, `bottom`, `left`).
3.  **Encoding:** Mapping facial features to a 128D vector space.
4.  **Verification:** Computing Euclidean distance between unknown encodings and the known registry.
5.  **Visualization:** Rendering bounding boxes and identity labels on the source image.

---

## 📖 How the System Works (Technical Deep Dive)

### 1. Face Detection (HOG + Linear SVM)
The engine utilizes a **Histogram of Oriented Gradients (HOG)** detector. It simplifies the image into gradients of light and shadow, creating a representation that highlights the structural contours of the face, making it invariant to slight lighting changes.

### 2. Facial Landmark Estimation
Once a face is found, the system identifies 68 specific landmarks (eyes, nose, mouth, chin). This allows the engine to "warp" the face to a standard centered position, ensuring consistent encoding regardless of head tilt.

### 3. Deep Metric Learning (128D Embeddings)
The core of the recognition is a ResNet-based deep neural network trained to output a **128-dimensional vector**. The network is trained using a **Triplet Loss** function, which ensures that encodings for the same person are closer together in vector space than encodings for different people.

---

## 🚀 Installation & Setup

### Prerequisites
- Python 3.7+
- CMake (Required for Dlib)
- Visual Studio Build Tools (C++ Compiler for Windows)

### Steps
1. **Clone the repository:**
   ```bash
   git clone https://github.com/Shahman-Butt/PersonRecognizer.git
   cd PersonRecognizer
   ```

2. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

---

## ▶️ How to Run the Project
To execute the facial recognition engine and verify identities in the test dataset:
```bash
python src/face_engine.py
```

---

## 📁 Code Structure
```bash
PersonRecognizer/
├── assets/           # Media assets for documentation
├── data/
│   ├── known/        # Registered identities (Reference images)
│   └── testing/      # Unlabeled images for recognition
├── docs/             # Technical specifications and guides
├── src/
│   └── face_engine.py # Core recognition logic
├── requirements.txt  # Project dependencies
└── README.md         # Professional documentation
```

---

## 🛠️ Future Improvements
- [ ] **Real-time Video Processing:** Integration with `cv2.VideoCapture` for live streams.
- [ ] **Database Integration:** Moving from local image folders to a PostgreSQL/Vector DB registry.
- [ ] **GPU Acceleration:** Leveraging CUDA for faster ResNet encoding inference.

---

## 👥 Author Information
*   **Shahman Butt** - [GitHub](https://github.com/Shahman-Butt) | [LinkedIn](https://www.linkedin.com/in/shahman-butt/)


---
*Created for the CSI Professional Documentation Initiative.*
