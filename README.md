# Temporal Mamba for Cell Tracking

A deep-learning framework that combines **CNN-based cell representation**, **Temporal Mamba**, and **Hungarian matching** to track cells across microscopy image sequences.

The model was developed using the **DIC-C2DH-HeLa** dataset from the Cell Tracking Challenge. It was trained on Sequence 01 and evaluated using frozen weights on unseen Sequence 02.

---

## Overview

Cell tracking requires maintaining the identity of individual cells across time while handling movement, appearance changes, and cell division.

This project explores Temporal Mamba for learning long-range temporal relationships between cell observations.

### Pipeline


Cell Masks
    ↓
Cell Detection and Crop Extraction
    ↓
CNN Appearance Encoder
    ↓
Temporal Mamba
    ↓
Appearance + Motion + Shape Features
    ↓
Hungarian Matching
    ↓
Predicted Cell Tracks
    ↓
Division Detection


### Key Features

CNN-based cell appearance encoding
Temporal modeling using Mamba
Appearance-, motion-, and shape-aware association
Hungarian matching for cell tracking
Division-event prediction
Parent–daughter lineage analysis
Frozen cross-sequence evaluation
CTC-format result export
Dataset

Experiments were conducted on the DIC-C2DH-HeLa dataset.

Sequence	Usage
Sequence 01	Model training
Sequence 02	Frozen evaluation

Sequence 02 was evaluated without retraining or fine-tuning.

### Results

The frozen model processed all 84 frames and 1,030 cell detections in Sequence 02.

Metric	Result
Predicted tracks	34
Ground-truth tracks	32
Weighted identity purity	86.99%
Mean track purity	93.68%
Perfect-purity tracks	24 / 34
Tracks with ≥90% purity	27 / 34
Division F1	0.00%
Lineage-edge F1	0.00%

The model showed promising identity consistency across sequences. However, division detection remains a limitation: the tracker frequently continued the parent identity into one daughter after mitosis instead of creating explicit parent–daughter relationships.

### Visualizations

The project generates:

Spatial cell trajectories
Time–position trajectories
Track-identity purity plots
Predicted lineage graphs

"C:\Users\Likithasri\Downloads\motion of cells_mamba.png"
"C:\Users\Likithasri\Downloads\division cells trajectories.png"
"C:\Users\Likithasri\Downloads\sequence 2 _lines.png"
"C:\Users\Likithasri\Downloads\lines_histograms.png"
"C:\Users\Likithasri\Downloads\videos_mamba_ctc_final_kaggle.ipynb"

Project Structure
Temporal-Mamba-Cell-Tracking/
│
├── notebooks/
│   └── temporal_mamba_cell_tracking.ipynb
│
├── results/
│   ├── metrics/
│   └── visualizations/
│
├── checkpoints/
│   ├── best_temporal_cell_mamba.pt
│   └── best_division_event_head.pt
│
├── README.md
└── requirements.txt
Tech Stack

Python · PyTorch · Mamba SSM · OpenCV · SciPy · NumPy · tifffile · Matplotlib · NetworkX

Current Status
 CNN cell encoder
 Temporal Mamba model
 Sequence 01 training
 Hungarian cell association
 Frozen Sequence 02 evaluation
 Division and lineage analysis
 CTC-format prediction export
 Official CTC TRA evaluation
 Improved division-aware tracking
 Additional CTC dataset evaluation
Future Work
Evaluate using the official CTC TRA metric
Improve mitosis and parent–daughter modeling
Add IDF1 and identity-switch evaluation
Compare Temporal Mamba with CNN-only and motion-only baselines
Extend the framework to additional 2D and 3D cell-tracking datasets
Author

Likitha Sri Maddipatla

Summer Research Intern, Indian Institute of Space Science and Technology (IIST)
    ↓
Lineage Reconstruction
