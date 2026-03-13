# System Architecture - Biometric Face Recognition Engine

## 1. Pipeline Overview
The recognition pipeline is divided into four distinct phases:

### Phase 1: Pre-processing
Images are loaded and converted from BGR (OpenCV default) or RGB (Standard) into a format suitable for dlib processing.

### Phase 2: Face Detection
The system uses the `dlib` HOG detector to locate faces.
- **Complexity**: O(N*M) where N, M are image dimensions.
- **Accuracy**: Extremely high for frontal and near-frontal faces.

### Phase 3: Feature Extraction (Encoding)
A pre-trained Residual Network (ResNet) maps coordinates to a 128-dimensional space.
- **Model**: `dlib_face_recognition_resnet_model_v1`
- **Output**: 128 floating-point numbers.

### Phase 4: Identity Mapping
We calculate the distance between the input encoding and all encodings in the `data/known` directory. A match is confirmed if the distance is below the threshold of `0.6`.

## 2. Directory Mapping
- **Input**: `data/testing/`
- **Registry**: `data/known/`
- **Logic**: `src/face_engine.py`
