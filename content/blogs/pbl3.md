---
title: "Develop a Re-Identification System for Stray Cats Post-TNR Program 🧑🏻‍💻"
summary: "Background & Summary"
description: "Background & Summary"
date: 2025-07-27T10:00:01+09:00
author: "Kanato Nishiura"
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
hideSummary: false
ShowReadingTime: true
ShowPostNavLinks: true
---

**Project Website**: https://xknt21.github.io  

This project is introduced in detail on the official project website above, including system design, implementation details, and experimental results.

---

### Overview
This project is a **mobile and AI-based system for stray cat re-identification**, developed as part of a **15-week Project-Based Learning (PBL)** course.  
The system aims to support the **Trap-Neuter-Return (TNR) program** by preventing redundant medical treatments and improving coordination between volunteers, animal hospitals, and organizations in the Kansai region of Japan.

The application integrates:
- A **React Native mobile app**
- A **Flask-based backend**
- A **deep learning-based cat re-identification model**

---

### Motivation
In TNR activities, the same stray cat is often captured and treated multiple times due to the lack of a reliable identification system. This leads to:

- Unnecessary medical procedures  
- Increased burden on animal hospitals  
- Inefficient use of resources  

This project aims to solve these issues by enabling **image-based identification of individual cats**.

---

### System Architecture

The system consists of three main components:

#### 1. Frontend (Mobile & Web)
- Built with React Native (Expo)
- Allows users to:
  - Capture or upload cat images  
  - View identification results  
  - Access cat profiles and medical records  

#### 2. Backend (Flask API)
- Handles:
  - Image processing requests  
  - Model inference  
  - Database communication  
- Provides RESTful APIs for both mobile and web clients  

#### 3. AI Model (Cat Re-Identification)
- Siamese Neural Network for similarity learning  
- Generates embeddings and performs matching  

---

### Model Pipeline

1. User uploads or captures a cat image  
2. YOLO-based model detects and crops the cat face  
3. Image is resized and normalized  
4. Siamese network generates a **128-dimensional embedding**  
5. Embedding is compared with stored embeddings using **Euclidean distance**  
6. If distance < threshold (0.4), a match is returned; otherwise, no match  

---

### Model Architecture

#### Siamese Network
- **Backbone**: EfficientNetB3 (default), VGG16 or MobileNetV2 (optional)  
- **Embedding Head**:
  - Global Average Pooling  
  - Dense (128 units, ReLU)  
  - Batch Normalization / Dropout  
  - L2 normalization  

#### Loss Functions
- **Contrastive Loss** (primary)
- **Triplet Loss** (experimental)

---

### Dataset

- **Total Cats**: 250  
- **Total Images**: 1,880  
- **Average Images per Cat**: 7.5  

Sources:
- Kaggle Cat Re-ID datasets  
- HelloStreetCat dataset  
- Custom scraped datasets  

---

### Training Details

- Optimizer: Adam (lr = 0.0001)  
- Batch Size: 16  
- Epochs: 50 (production)  
- Image Size: 200×200  
- Data Augmentation:
  - Flip, rotation, noise  

---

### Performance

#### Contrastive Model
- Accuracy: 69.4%  
- Precision: 67.7%  
- Recall: 69.4%  
- F1 Score: 68.2%  

#### Key Insights
- Contrastive learning performs well with limited data  
- Triplet loss requires more data and tuning  
- Model is suitable for practical deployment  

---

### Key Features

#### Cat Re-Identification
- Image-based matching with confidence scores  
- Detects previously treated cats  
- Prevents duplicate medical interventions  

#### Medical Record Management
- Stores treatment history, vaccination status  
- Supports updates by animal hospitals  

#### Role-Based System
- Volunteers: upload images and check matches  
- Hospitals: manage medical records  
- Admins: system monitoring and analytics  

#### Admin Dashboard
- Match statistics  
- Activity tracking  
- Dataset insights  

---

### System Design Principles

- **No Auto-Registration Policy**  
  - Prevents incorrect or duplicate entries  
  - Only authorized admins can register new cats  

- **Privacy & Security**  
  - API key authentication  
  - Secure data handling (TLS, encryption)  

- **Scalability**  
  - Designed for up to 1000 users  
  - Supports real-time inference  

---

### Tech Stack

- **Frontend**: React Native, Expo  
- **Backend**: Python, Flask  
- **AI**: TensorFlow, Keras  
- **Computer Vision**: OpenCV, YOLO  
- **Data**: NumPy, Pandas  

---

### My Contributions

- Designed and implemented the **AI model pipeline**  
- Developed the **Flask backend for model inference**  
- Contributed to **system integration (mobile ↔ backend ↔ AI)**  
- Evaluated model performance and improved training process  

---

### Challenges

- Limited dataset size for deep metric learning  
- Difficulty in tuning triplet loss  
- Ensuring real-time performance on mobile environments  
- Maintaining data quality without auto-registration  

---

### Future Work

- Improve accuracy with larger datasets  
- Optimize model for edge/mobile deployment  
- Enhance UI/UX for non-technical users  
- Expand deployment beyond Kansai region  

---

### Impact

This project demonstrates how AI can support animal welfare by:

- Reducing redundant medical treatments  
- Improving efficiency in TNR operations  
- Enabling data-driven coordination between stakeholders  

It reflects my interest in applying **computer vision and machine learning to socially impactful real-world problems**.