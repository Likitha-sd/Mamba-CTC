# 🧬 Temporal Mamba for Cell Tracking Challenge

> Learning long-range temporal representations for microscopy cell tracking using **Temporal Mamba State Space Models**.

---

## 📌 Overview

Cell tracking aims to preserve the identity of individual cells across time while handling:

- Cell movement
- Appearance variation
- Occlusion
- Cell division (mitosis)

This project investigates **Temporal Mamba**, a State Space Model (SSM), for learning long-range temporal dependencies between cell observations. The framework combines deep appearance features with temporal sequence modeling to produce robust cell trajectories and lineage predictions on microscopy image sequences.

---

## 🚀 Key Features

- CNN-based Cell Appearance Encoder
- Temporal Mamba Sequence Modeling
- Appearance + Motion + Shape Feature Fusion
- Hungarian Matching for Cell Association
- Division Event Prediction
- Parent–Daughter Lineage Reconstruction
- Frozen Cross-Sequence Evaluation
- Cell Tracking Challenge (CTC) Result Export

---

# 🏗 Pipeline

```text
Cell Masks
     │
     ▼
Cell Detection & Crop Extraction
     │
     ▼
CNN Appearance Encoder
     │
     ▼
Temporal Mamba
     │
     ▼
Appearance + Motion + Shape Feature Fusion
     │
     ▼
Hungarian Matching
     │
     ▼
Predicted Cell Tracks
     │
     ▼
Division Detection
     │
     ▼
Parent–Daughter Lineage Reconstruction
```

---

# 📂 Dataset

Experiments were conducted using the **Cell Tracking Challenge (CTC)** dataset.

**Dataset**

DIC-C2DH-HeLa

| Sequence | Purpose |
|-----------|----------|
| Sequence 01 | Model Training |
| Sequence 02 | Frozen Evaluation |

The model was evaluated on **Sequence 02** without retraining or fine-tuning to assess generalization across unseen sequences.

---

# 📊 Experimental Results

| Metric | Result |
|---------|--------|
| Frames Processed | **84** |
| Cell Detections | **1,030** |
| Predicted Tracks | **34** |
| Ground Truth Tracks | **32** |
| Mean Track Purity | **93.68%** |
| Weighted Identity Purity | **86.99%** |
| Perfect Purity Tracks | **24 / 34** |
| Tracks ≥90% Purity | **27 / 34** |
| Division F1 | **0.00%** |
| Lineage Edge F1 | **0.00%** |

The frozen evaluation achieved **93.68% Mean Track Purity** and **86.99% Weighted Identity Purity**, demonstrating consistent identity preservation across unseen microscopy sequences. Division detection remains an open challenge, as the tracker frequently propagated the parent identity into one daughter cell instead of explicitly modeling mitosis.

---

# 📈 Visualizations

The project generates the following outputs:

## Spatial Cell Trajectories

<img width="1189" height="1190" alt="division cells trajectories" src="https://github.com/user-attachments/assets/a17bbcc7-e7da-4a7b-afe7-78ca964f63e2" />


---

## Division Cell Trajectories


---

## Time–Position Trajectories

<img width="1690" height="989" alt="motion of cells_mamba" src="https://github.com/user-attachments/assets/b63e3d98-af88-4f57-ad3a-a29fcf8ce96f" />

---

## Cell Motion Visualization



---

## Track Identity Purity

<img width="1287" height="681" alt="sequence 2 _lines" src="https://github.com/user-attachments/assets/0d668b43-6056-4c14-b90d-5cbbd7bf8988" />


---

## Predicted Lineage Graph

<img width="1990" height="1390" alt="lineage_graph_mamba" src="https://github.com/user-attachments/assets/d28919c5-3bb8-4af0-8463-7945d43a03e9" />


---

# 📂 Repository Structure

```text
Temporal-Mamba-Cell-Tracking/
│
├── notebooks/
│   └── temporal_mamba_cell_tracking.ipynb
│
├── checkpoints/
│   ├── best_temporal_cell_mamba.pt
│   └── best_division_event_head.pt
│
├── results/
│   ├── metrics/
│   └── visualizations/
│
├── README.md
├── requirements.txt
└── LICENSE
```

---

# ⚙️ Technology Stack

| Category | Technologies |
|-----------|--------------|
| Language | Python |
| Deep Learning | PyTorch, Mamba SSM |
| Computer Vision | OpenCV, tifffile |
| Scientific Computing | NumPy, SciPy |
| Visualization | Matplotlib |
| Graph Analysis | NetworkX |

---

# ✅ Current Status

- [x] CNN Appearance Encoder
- [x] Temporal Mamba
- [x] Hungarian Matching
- [x] Frozen Cross-Sequence Evaluation
- [x] Division Analysis
- [x] Lineage Reconstruction
- [x] CTC Result Export
- [ ] Official CTC TRA Evaluation
- [ ] IDF1 Evaluation
- [ ] Additional CTC Dataset Benchmarking

---

# 🔬 Future Work

- Evaluate using the official Cell Tracking Challenge TRA metric
- Improve mitosis and parent–daughter relationship modeling
- Add IDF1 and identity-switch evaluation
- Compare Temporal Mamba with CNN-only and motion-only baselines
- Extend evaluation to additional 2D and 3D Cell Tracking Challenge datasets
- Prepare the work for research publication

---

# 👩‍💻 Author

**Likitha Sri Maddipatla**

B.Tech Computer Science and Engineering

Summer Research Fellow  
Indian Institute of Space Science and Technology (IIST)

GitHub: https://github.com/Likitha-sd

---

# ⭐ Support

If you found this repository useful, consider giving it a ⭐.


If you found this repository useful, consider giving it a ⭐.
If you found this repository useful, consider giving it a ⭐.
