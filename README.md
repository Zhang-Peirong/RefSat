# 🛰️ Referring Multi-Object Tracking in Satellite Videos

This repository supports our paper:

> **Referring Multi-Object Tracking in Satellite Videos: A New Benchmark and Baseline**  
> *Submitted to ACM Multimedia 2025 – Dataset Track (under review)*

We present a novel dataset for **Referring Multi-Object Tracking in Satellite Videos (RMOT-SV)**, that aims to track single or multiple objects in satellite videos guided by natural language queries.


![image](https://github.com/user-attachments/assets/38768965-eed0-4e54-8721-3b8318aaf07a)

## 📦 Dataset Download

The full dataset used in our paper is available at the following link:

🔗 **[Download from Google Drive](https://drive.google.com/drive/folders/1QwfT6oN6j6L4Vh_hCDoKMzhaSzTgsZES?usp=sharing)**




## 📚 Dataset Overview

Each data sample in the dataset consists of:
- A satellite video clip (multi-frame RGB sequence).
- Frame-by-frame **bounding box annotations** for **all visible objects** in the scene, including object IDs.
- A **textual query** describing one or more specific targets.
- The **ground truth identities** of the objects that match the given query.


### 📁 File Structure

```bash
RefSat/
├── videos/              # Satellite video clips ( .jpg sequences)
├── gt/            # xml: bounding boxes, object IDs for MOT
├── language queries/       # JSON: text queries, corresponding object IDs, and frame IDs.
├── train.txt    # train/test splits
└── test.txt
```







## 📘 Motion Pattern Estimation – Variable & Function Definitions
---
The following table provides detailed definitions of the variables and functions used in Algorithm 1 of the paper.

![image](https://github.com/user-attachments/assets/dcacc719-e5bb-4d59-895e-eae32f89ac36)


| Symbol / Function      | Type        | Description |
|------------------------|-------------|-------------|
| `B_t`                  | Input       | Object bounding box or mask at frame *t* |
| `Size(B_t)`            | Function    | Returns the size of `B_t`, used to distinguish small objects |
| `τ`                    | Parameter   | Size threshold to decide whether to apply SAM |
| `center(B_t)`          | Function    | Computes geometric center of `B_t` (box center or mask centroid) |
| `SAM(B_t)`             | Function    | Applies Segment Anything Model to extract a mask from `B_t` |
| `C_t`                  | Intermediate| Estimated object center at frame *t* |
| `~C_t`                 | Intermediate| Smoothed/interpolated center sequence after temporal filtering |
| `TemporalFilter({C_t})`| Function    | Applies smoothing and fills missing points due to occlusion |
| `θ_t`                  | Intermediate| Motion direction at frame *t* |
| `v_t`                  | Intermediate| Object velocity at frame *t* |
| `d~C_t/dt`             | Derived     | Velocity vector computed from the filtered trajectory |
| `DeriveKinematics(...)`| Function    | Computes motion direction and velocity from smoothed trajectory points. |
| `Δθ_t`                 | Derived     | Change in direction between frames |
| `a_t`                  | Derived     | Acceleration (velocity change rate) |
| `PatternMatch(...)`    | Function    | Classifies motion pattern (e.g., turning, approaching) |
| `M_t`                  | Output      | Predicted motion label at frame *t* |
| `AggregatePattern({M_t})` | Function | Aggregates frame-level labels into final motion category |






## 📄 License

This dataset is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license.


**Attribution Required** — You must give appropriate credit, provide a link to the license, and indicate if changes were made.  
More info: [https://creativecommons.org/licenses/by/4.0/](https://creativecommons.org/licenses/by/4.0/)


© 2025 the Aerospace Information Research Institute, the Key Laboratory of Target Cognition and Application Technology (TCAT), Chinese Academy of Sciences, Peirong Zhang
