# Temporal Mamba for Cell Tracking

A deep-learning framework that combines **CNN-based cell representation**, **Temporal Mamba**, and **Hungarian matching** to track cells across microscopy image sequences.

The model was developed using the **DIC-C2DH-HeLa** dataset from the Cell Tracking Challenge. It was trained on Sequence 01 and evaluated using frozen weights on unseen Sequence 02.

---

## Overview

Cell tracking requires maintaining the identity of individual cells across time while handling movement, appearance changes, and cell division.

This project explores Temporal Mamba for learning long-range temporal relationships between cell observations.

### Pipeline

```text
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
    ↓
Lineage Reconstruction
