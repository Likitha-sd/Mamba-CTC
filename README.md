# Temporal Mamba-Based Cell Tracking for Microscopy Images

## Overview

This project presents a deep learning framework for cell tracking on microscopy image sequences from the Cell Tracking Challenge (CTC). The proposed pipeline combines CNN-based feature extraction, Hungarian-based cell association, and Temporal Mamba for temporal representation learning of reconstructed cell trajectories.

The framework reconstructs cell trajectories, learns temporal dynamics from tracked cells, and evaluates the tracking performance using standard tracking metrics.

---

## Pipeline


DIC-C2DH-HeLa dataset
        ↓
Load raw images, segmentation masks, and tracking annotations
        ↓
Extract individual cells from segmentation masks
        ↓
CNN appearance encoder
        ↓
Temporal Mamba
        ↓
Learn temporal cell representations
        ↓
Hungarian matching
        ↓
Assign predicted Track IDs
        ↓
Division-event head
        ↓
Construct predicted tracks and lineage
        ↓
Train on Sequence 01
        ↓
Freeze all learned weights
        ↓
Test on unseen Sequence 02
        ↓
Compare predictions with human annotations
        ↓
Export predictions in official CTC format

---

## Features

- CNN-based cell appearance feature extraction
- Hungarian Algorithm for optimal frame-to-frame cell association
- Temporal Mamba for temporal feature learning
- Cell trajectory reconstruction
- t-SNE visualization of learned embeddings
- Evaluation using tracking performance metrics

---

## Dataset

**Cell Tracking Challenge (CTC)**

Dataset Used:
- DIC-C2DH-HeLa

Ground Truth Includes:
- Segmentation Masks
- Tracking Annotations
- Cell Lineage Information

---

## Technologies Used

- Python
- PyTorch
- OpenCV
- NumPy
- SciPy
- Scikit-learn
- Matplotlib
- Google Colab

---

## Methodology

1. Load microscopy image sequences and segmentation masks.
2. Extract individual cells from segmentation masks.
3. Resize each cell to 64 × 64 pixels.
4. Extract 128-dimensional appearance features using a CNN.
5. Associate cells across consecutive frames using Hungarian Matching.
6. Construct complete cell trajectories.
7. Convert trajectories into temporal feature sequences.
8. Train Temporal Mamba using Mean Squared Error (MSE).
9. Generate 64-dimensional temporal embeddings.
10. Evaluate tracking performance.

---

## Results

| Metric | Value |
|---------|--------|
| Ground Truth Tracks | 38 |
| Predicted Tracks | 36 |
| Coverage | 36 / 38 |
| Precision | 100% |
| Recall | 98.57% |
| F1-Score | 99.28% |
| Approximate MOTA | 97.68% |
| Continuous Tracks | 30 |
| Fragmented Tracks | 6 |
| ID Switches | 10 |

---

## Temporal Mamba

Temporal Mamba is used to model the temporal evolution of reconstructed cell trajectories.

Input:
- Sequence of 128-dimensional CNN feature embeddings

Training:
- Previous feature embeddings → Predict next feature embedding
- Loss Function: Mean Squared Error (MSE)
- Optimizer: Adam

Output:
- 64-dimensional temporal embedding for each tracked cell

---

## Visualization

- Cell trajectory reconstruction
- t-SNE embedding visualization
- Ground truth vs predicted tracking comparison
- Tracking performance statistics

---

## Future Work

- Replace CNN with Vision Mamba for spatial feature extraction.
- Integrate Temporal Mamba directly into the tracking stage.
- Evaluate on official CTC benchmark datasets.
- Compute official CTC metrics (TRA, SEG, DET).
- Improve lineage reconstruction and cell division detection.

---

## Author

**Likitha Sri Maddipatla**

B.Tech Computer Science and Engineering

Sir C.R. Reddy College of Engineering

---

## License

This project is intended for academic and research purposes.
