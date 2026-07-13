# Temporal Mamba for Cell Tracking and Lineage Analysis

A CNN–Temporal Mamba framework for cell identity tracking, temporal feature modeling, division-event analysis, and lineage reconstruction on the **DIC-C2DH-HeLa** dataset from the Cell Tracking Challenge.

The framework uses a convolutional neural network to encode individual cell appearance, a Temporal Mamba model to learn temporal cell representations, Hungarian matching for frame-to-frame association, and a division-event prediction head for lineage reconstruction.

The model was trained on **Sequence 01** and evaluated using frozen weights on the unseen **Sequence 02**, without retraining or using Sequence 02 ground-truth identities during tracking.

---

## Project Status

| Component | Status |
|---|---|
| Dataset loading and inspection | Completed |
| Cell detection extraction | Completed |
| CNN appearance encoder | Completed |
| Temporal Mamba implementation | Completed |
| Sequence 01 training | Completed |
| Hungarian cell association | Completed |
| Division-event prediction head | Completed |
| Frozen Sequence 02 inference | Completed |
| Identity-purity evaluation | Completed |
| Division and lineage evaluation | Completed |
| Division-failure analysis | Completed |
| CTC-format prediction export | Completed |
| CTC export validation | Completed |
| Official CTC TRA evaluation | Pending |

---

## Research Objective

Cell tracking requires maintaining the identity of individual cells across microscopy frames while handling:

- cell movement;
- appearance variation;
- shape changes;
- temporary ambiguity;
- track fragmentation;
- cell division;
- parent–daughter lineage relationships.

Conventional frame-to-frame association methods may not fully use long-range temporal information. This project investigates whether **Mamba-based selective state-space modeling** can learn useful temporal representations for cell tracking.

The main objectives are:

1. Extract appearance features from individual cells using a CNN.
2. Model temporal cell evolution using Temporal Mamba.
3. Associate detections using appearance, motion, and shape information.
4. Detect mitotic division events.
5. Reconstruct parent–daughter lineage relationships.
6. Evaluate frozen cross-sequence generalization.

---

## Dataset

The experiments use the **DIC-C2DH-HeLa** dataset from the Cell Tracking Challenge.

The current implementation focuses on the two-dimensional HeLa cell sequences:

```text
DIC-C2DH-HeLa/

├── 01/
│   ├── t000.tif
│   ├── t001.tif
│   └── ...
│
├── 01_GT/
│   └── TRA/
│       ├── man_track000.tif
│       ├── man_track001.tif
│       ├── ...
│       └── man_track.txt
│
├── 02/
│   ├── t000.tif
│   ├── t001.tif
│   └── ...
│
└── 02_GT/
    └── TRA/
        ├── man_track000.tif
        ├── man_track001.tif
        ├── ...
        └── man_track.txt
