---
title: "Develop a System for Tomato Quality Assessment 🧑🏻‍💻"
summary: "Background & Summary"
description: "Background & Summary"
date: 2025-01-12T19:38:01+09:00
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

### Overview
This project is a **joint research collaboration between Ritsumeikan University (Japan) and Universitas Dinamika Surabaya (Indonesia)**.  
We developed an **automated tomato quality assessment system** using computer vision and machine learning to improve the efficiency, consistency, and scalability of traditional grading processes.

---

### Collaboration Structure

This research was conducted through an international collaboration with clearly defined roles:

- **Ritsumeikan University (Japan)**  
  - Led the **system design and development**  
  - Implemented the **machine learning models and pipeline**  
  - Conducted experiments and performance evaluation  

- **Universitas Dinamika Surabaya (Indonesia)**  
  - Led **data collection and dataset preparation**  
  - Collected real-world tomato images from local environments  
  - Performed **manual labeling and data annotation**  

This division of responsibilities enabled us to combine **strong technical implementation** with **real-world data acquisition**, improving the practical relevance of the system.

---

### Motivation & Background
Tomato grading is typically performed manually, which introduces:

- Human bias and inconsistency  
- High labor costs  
- Limited scalability  

This project aims to solve these issues by building an automated, image-based grading system.

---

### System Architecture

#### 1. Image Acquisition
- Individual input (uploaded images)  
- Industrial input (video frames from conveyor systems)  

---

#### 2. Preprocessing
- Segmentation to isolate the tomato  
- Auto-cropping to remove background noise  
- Normalization for consistent input conditions  

---

### Feature Extraction

- **Color Features**: RGB distribution, ripeness indicators  
- **Shape Features**: Size, circularity, symmetry  
- **Texture Features**: Surface smoothness, defect detection  

---

### Machine Learning Models

#### Freshness Classification (CNN)
- VGG16-based architecture  
- Transfer learning and fine-tuning  
- Captures high-level visual features related to ripeness  

#### Physical Quality Assessment (SVM)
- Uses handcrafted features  
- Evaluates uniformity, size, and defects  

---

### Output

- **Freshness Grade**: A–D  
- **Physical Quality Score**: 1–4  

---

### Dataset & Experiments

- ~10,000+ training images (open-source datasets)  
- ~300 real-world images collected and labeled by Universitas Dinamika  
- Evaluation using:
  - F1 Score  
  - 5-fold cross-validation  

---

### Results

- Successfully built an end-to-end grading system  
- CNN effectively captured freshness-related features  
- SVM provided interpretable physical quality evaluation  
- Hybrid approach improved overall robustness  

---

### Industrial Extension

- Video-to-frame processing for batch grading  
- Designed for real-time use in conveyor-based systems  
- Demonstrated scalability for agricultural and industrial applications  

---

### Limitations

- Dataset diversity remains limited  
- Freshness classification partially relies on mapping  
- Limited number of grading classes  

---

### Future Work

- Expand dataset with more environmental variations  
- Train models from scratch for improved accuracy  
- Develop a user-friendly interface  
- Optimize for real-time deployment  

---

### Tech Stack

- Python, OpenCV, NumPy, Pandas  
- TensorFlow, PyTorch, Scikit-learn  
- Matplotlib, Seaborn  

---

### Key Contributions

- Developed a **hybrid ML system (CNN + SVM)**  
- Designed a **full end-to-end pipeline**  
- Contributed to an **international collaborative research project**  
- Bridged **technical development and real-world data collection**  

---

### Takeaways

Through this project, I gained experience in:

- International research collaboration  
- End-to-end AI system development  
- Computer vision for real-world applications  
- Data-driven problem solving  

---

### Impact

This project demonstrates how AI can be applied to agriculture to:

- Improve efficiency and consistency  
- Reduce human bias  
- Enable scalable quality assessment systems  

It reflects my interest in applying **AI and optimization techniques to real-world problems in a global context**.