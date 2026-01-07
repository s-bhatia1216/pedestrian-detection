# pedestrian-detection
Benchmarking HOG, CNN, ViT, and SAM2 Approaches on the PnPLO Pedestrian Dataset

This repository contains four standalone benchmarking scripts used to evaluate and compare pedestrian detection models on the **PnPLO dataset** (Person vs. Person-Like Objects). The benchmarks focus on robustness to false positives from statues, mannequins, and other human-like non-pedestrians.

The models evaluated are:
- **HOG + SVM**
- **Faster R-CNN**
- **DETR**
- **SAM2 (Segmentation-First Pipeline)**

Each script computes consistent evaluation metrics including precision, recall, F1 score, confusion matrices, false-positive breakdowns, and model-specific diagnostics.

---

## Execution Environment

**Note:** These scripts were designed to run in **Google Colab** and may require minor path or dependency adjustments for local execution.

Recommended setup:
- Google Colab (GPU runtime)
- Python ≥ 3.9
- PyTorch
- torchvision
- OpenCV
- NumPy, Matplotlib, Seaborn

Dataset paths assume a Colab + Google Drive mounting structure.

---

## Robust Pedestrian Detection Under Visual Ambiguity

This repository benchmarks **robustness in pedestrian detection** across four representative computer vision paradigms: **HOG + SVM**, **Faster R-CNN**, **DETR**, and **YOLO + SAM2**, evaluated on the **PnPLO (Person and Person-Like Objects)** dataset.

Unlike standard object detection benchmarks that emphasize accuracy alone, this project focuses on **false positives caused by person-like nonhuman objects** (e.g., statues, mannequins), which impose significant downstream computational and reliability costs in robotics and surveillance systems.

---

## Why This Matters

Pedestrian detection systems are often deployed in **always-on, resource-constrained environments**. In these settings:

- False positives can trigger expensive downstream modules (tracking, pose estimation, planning).
- Overconfident predictions on ambiguous objects degrade system reliability.
- Robustness to *person-like visual ambiguity* is as important as recall on real pedestrians.

This repository provides a **controlled, architecture-level comparison** showing how different detection paradigms trade off accuracy, confidence, and robustness.

---

## Models Evaluated

- **HOG + Linear SVM**
  - Classical gradient-based baseline
  - Highly interpretable, but vulnerable to silhouette-based false positives

- **Faster R-CNN (ResNet-50 FPN)**
  - Two-stage CNN detector with region proposals
  - Strong semantic filtering, but still confusable on realistic statues

- **DETR**
  - Transformer-based, set-prediction detector
  - Exhibits cautious behavior via background abstention under ambiguity

- **YOLO + SAM2**
  - Detection-first pipeline with high-quality segmentation
  - Excellent localization; semantic robustness depends on detector

---

## Dataset: PnPLO (Karthika & Chandran, 2020)

- Binary classes: **person** vs. **person-like**
- Includes real pedestrians and visually similar nonhuman objects
- Annotated in **PASCAL VOC** format
- Balanced train / val / test splits

The dataset is specifically designed to stress-test **robustness to visual ambiguity**, not just detection accuracy.

---

## Evaluation Metrics

All models are evaluated using a unified pipeline with metrics chosen to reflect real-world deployment costs:

- Precision, Recall, F1 Score
- **False Positive Rate (person-like → person)**
- Average Precision (AP) and mean Average Precision (mAP)
- Precision–Recall curves
- Confusion matrices (including background for detectors)

---

## Key Findings

- **HOG + SVM** exhibits a high false positive rate driven by silhouette similarity.
- **Faster R-CNN** achieves strong precision–recall balance but still misclassifies high-fidelity statues.
- **DETR** achieves the **lowest false positive rate** by abstaining under ambiguity, at the cost of recall.
- **YOLO + SAM2** achieves the **highest mAP**, producing excellent masks, but semantic errors propagate from detection.

**Takeaway:** Robustness is governed by *architectural priors*, not just model size or accuracy alone.

---

## Report.pdf

📄 **Full Paper**  
*Robustness in Pedestrian Detection: Benchmarking HOG, Faster R-CNN, SAM2, & DETR on the PnPLO Dataset*  
Sonal Bhatia, Yash Thakkar @ Princeton University

---

## Authors

- **Sonal Bhatia** — MAE + CS + Robotics, Princeton University  
- **Yash Thakkar** — Computer Science, Princeton University  

