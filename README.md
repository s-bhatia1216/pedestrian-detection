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
