# 🤖 Advanced Artificial Intelligence & Data Engineering Portfolio

![Python](https://img.shields.io/badge/Python-3670A0?style=flat&logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat&logo=pytorch&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat&logo=scikit-learn&logoColor=white)
![OpenCV](https://img.shields.io/badge/OpenCV-3670A0?style=flat&logo=opencv&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat&logo=jupyter&logoColor=white)
![Stable-Baselines3](https://img.shields.io/badge/Stable--Baselines3-0A9EDC?style=flat)
![License: MIT](https://img.shields.io/badge/License-MIT-green?style=flat)

### Production-Grade Pipelines: Deep Reinforcement Learning, Cyber Threat Intelligence & Biomedical Image Segmentation

This repository is a **machine learning portfolio** with three end-to-end projects: **Deep Reinforcement Learning** (DQN, PPO, A2C on Lunar Lander v3), **unsupervised cyber threat detection** on firewall logs (K-Means, Hierarchical Clustering, DBSCAN, Apriori, FP-Growth), and **medical image segmentation** of knee X-rays with a **U-Net** in **PyTorch**. It showcases practical data engineering, data quality validation, hardware optimization and visual analytics applied to advanced Artificial Intelligence domains.

All pipelines run as fully reproducible **Jupyter Notebooks** with clean, production-grade code, interactive dashboards and detailed scientific telemetry.

---

## 🗺️ Quick Project Navigation

*   [**Architecture Overview**](#-architecture-overview) — How the three pipelines are structured.
*   [**Project 1: Lunar Lander v3 (Deep RL)**](#-project-1-lunar-lander-v3--deep-reinforcement-learning-benchmark) — Continuous physical spacecraft simulation.
*   [**Project 2: Cyber Threat Intelligence**](#-project-2-unsupervised-cyber-threat-intelligence--data-qa-pipeline) — Unsupervised behavioral aggregation & clustering pipeline.
*   [**Project 3: Biomedical Vision Segmentation**](#-project-3-biomedical-semantic-segmentation--data-validation-pipeline) — U-Net topology with hardware-agnostic optimizations.
*   [**Installation & Execution**](#%EF%B8%8F-requirements-and-installation) — Production readiness deployment instructions.

---

## 🧭 Architecture Overview

```mermaid
flowchart LR
    subgraph P1["Project 1 - Deep Reinforcement Learning"]
        direction LR
        A1["Gymnasium<br/>LunarLander-v3"] --> A2["VecNormalize<br/>Reward Normalization"]
        A2 --> A3["DQN / PPO / A2C<br/>Stable-Baselines3"]
        A3 --> A4["Shannon Entropy<br/>Policy Audit"]
        A4 --> A5["Champion: PPO<br/>93.3% Safe Landings"]
    end

    subgraph P2["Project 2 - Cyber Threat Intelligence"]
        direction LR
        B1["Raw Firewall Logs"] --> B2["Source IP<br/>Behavior Profiles"]
        B2 --> B3["Data QA<br/>VarianceThreshold + Correlation Filter"]
        B3 --> B4["K-Means / Hierarchical / DBSCAN"]
        B3 --> B5["Apriori / FP-Growth<br/>Threat Signatures"]
        B4 --> B6["PCA and t-SNE<br/>Plotly Dashboards"]
    end

    subgraph P3["Project 3 - Biomedical Vision"]
        direction LR
        C1["Digital Knee<br/>X-ray Dataset"] --> C2["Stratified Split<br/>70 / 15 / 15"]
        C2 --> C3["Target-Aware Augmentation<br/>torchvision v2"]
        C3 --> C4["U-Net<br/>Skip Connections"]
        C4 --> C5["mIoU 0.9569<br/>Dice 0.9772"]
        C5 --> C6["Clinical Overlay<br/>Diagnostics"]
    end
```

---

## 🚀 Project 1: Lunar Lander v3 — Deep Reinforcement Learning Benchmark

This framework presents a comprehensive engineering project in **Deep Reinforcement Learning (Deep RL)** applied to the continuous physical control of the **Lunar Lander v3** environment (Gymnasium). The primary objective is to train and audit intelligent agents capable of reading vector telemetries from a spacecraft and firing thrusters in a coordinated manner to execute a safe landing on a lunar pad.

### 💡 Technical Highlights of the DRL Pipeline
* **100% In-Memory Architecture (RAM):** The training ecosystem is decoupled from physical disk writes. Environments, training buffers, logs, and convergence history are processed strictly in volatile memory.
* **Gradient Stabilization:** Utilization of monitored environments wrapped with **Adaptive Reward Normalization (`VecNormalize`)** to mitigate the noisy impact of score spikes (+100 for landing / -100 for crashing).
* **Algorithm Competition:** A simultaneous comparative evaluation among three major logical families from the `Stable-Baselines3` framework: **DQN** (value-based), **PPO** (policy gradient-based), and **A2C** (synchronous Actor-Critic architecture).
* **Auditing via Shannon Entropy:** Implementation of fine-grained mathematical diagnostics to measure neural network behavioral plasticity post-training, shielding the repository against the *Policy Collapse* phenomenon.

### 📊 Quantitative Results Summary (300k Steps)
Following a controlled budget of **300,000 interaction timesteps** under independent stochastic seeds, the **PPO** algorithm emerged as the absolute champion:

| Algorithm | Mean Reward | Standard Deviation (Stability) | Safe Landing Rate (Success) | Shannon Entropy | Policy Health Status |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 🏆 **PPO** | **+184.20** | **14.50** | **93.3%** | **1.91 bits** (Max: 2.00) | ✅ Healthy & Dynamic |
| 🥈 **A2C** | -42.10 | 38.60 | 15.0% | 1.10 bits | ⚠️ Late Degradation |
| 🥉 **DQN** | -125.40 | 45.10 | 0.0% | 0.32 bits | 🚨 Collapse Alert |

* **Champion Firing Profile (PPO):** Idle/Drifting (25.5%), Left Lateral Thruster (17.6%), Right Lateral Thruster (17.3%), Main Vertical Braking Thruster (39.7%).

<div align="center">
  <img src="assets/lander.gif" alt="Lunar Lander v3 agent trained with PPO landing a spacecraft using Deep Reinforcement Learning" width="80%" />
</div>

---

## 🛡️ Project 2: Unsupervised Cyber Threat Intelligence & Data QA Pipeline

This pipeline implements a multi-algorithm **Unsupervised Learning infrastructure** designed to ingest raw, noisy, unlabeled corporate firewall transactional logs, aggregate events into entity-level behavioral profiles, and extract actionable indicators of network reconnaissance, automated scanning aggression, and boundary security policy collisions.

### 💡 Technical Highlights of the Unsupervised Pipeline
* **Entity Behavioral Shift:** Pivots the perspective of raw logs from individual continuous packet streams to discrete **Source IP Behavior Matrix Profiles** (`Src IP`), tracking historical network footprint metrics.
* **Data Quality & Feature Engineering:** Incorporates a dynamic data validation pipeline that ensures data *completeness* and *accuracy*, filters zero/low-variance features (`VarianceThreshold`), and automatically purges cross-redundant colinear variables (threshold > 0.85) to eliminate geometric bias in distance calculations.
* **Multi-Family Cluster Auditing:** Implements concurrent modeling paths comparing geometric partitioning (**K-Means**), topological taxonomy (**Agglomerative Hierarchical Clustering**), and density-based data spatial scanning (**DBSCAN**).
* **High-Impact Manifold Projections:** Embeds interactive visualization engines (**2D PCA** & **t-SNE** via Plotly) allowing real-time geometric inspections with embedded tooltips displaying individual malicious Source IPs.

### 📊 Structural Results Summary (Firewall Benchmark)
The models are automatically ranked based on intrinsic structural validation metrics to judge the geometric isolation quality of the vector spaces:

| Clustering Algorithm | Partitions (K) | Silhouette Score (Higher=Better) | Davies-Bouldin Index (Lower=Better) | Calinski-Harabasz Index (Higher=Better) | Execution Time (s) | Status & Interpretation |
| :--- | :---: | :---: | :---: | :---: | :---: | :--- |
| 🏆 **Hierarchical (Ward)** | 4 | **0.7025** | 0.5747 | **24.98** | **0.00199** | Highest cluster cohesion & density integration |
| 🥈 **K-Means** | 4 | 0.6763 | **0.1916** | 20.88 | 0.22504 | Optimal partition separation index |
| 🥉 **DBSCAN (eps=0.5)** | 1 | *nan* | *nan* | *nan* | 0.00204 | Surgically isolates anomalies as standalone **Noise (-1)** |

* **Discovered Threat Signatures (Apriori & FP-Growth):** Both association mining algorithms extract identical network signatures with a **Lift Factor > 7.00**, isolating rigid multi-stage connection dependencies across port 443.

<div align="center">
  <img src="assets/mosaico.jpg" alt="Clustering results for firewall logs: K-Means, Hierarchical and DBSCAN with PCA and t-SNE projections" width="80%" />
</div>

---

## 🧬 Project 3: Biomedical Semantic Segmentation & Data Validation Pipeline

This phase presents an end-to-end medical computer vision ecosystem designed for the automated boundary extraction and area tracking of the joint space in knee radiographs using the **Digital Knee X-ray** dataset. The framework serves as a clinical diagnostic tool to analyze cartilage degradation and structural changes associated with Osteoarthritis development.

### 💡 Technical Highlights of the Biomedical Pipeline
* **Topological Skip-Fusions (U-Net):** Evolves the computational graph from standard Fully Convolutional Networks (FCNs) into a symmetrical U-Net architecture. It integrates multi-scale *Skip Connections* that concatenate early high-resolution tissue textures directly into the transpose-convolution decoder blocks, preventing blurred boundaries.
* **Hardware-Agnostic Optimization:** Automatically routes operations based on the active workstation architecture. On CPU systems, it enforces single-threaded mini-batch constraints to eliminate OS scheduling collisions. On GPU infrastructures, it activates an aggressive *In-Memory GPU Caching Layer* (`VRAMKneeDataset`), loading the entire continuous matrix pool directly into the graphics card memory to eliminate physical disk I/O bottlenecks.
* **Synchronized Target-Aware Augmentations:** Leverages the modern `torchvision.transforms.v2` API via `tv_tensors` abstractions to execute stochastic spatial transformations (rotations and color jittering) symmetrically across both image and ground-truth mask planes.
* **Data Drift & Consistency Management:** Monitors input data distributions to detect distribution drift between training cohorts and clinical test sets, smoothing backpropagation convergence graphs using an `AdamW` optimizer (Weight Decay = 10⁻⁴).
* **In-Memory Checkpoint Layer:** Captures the highest-scoring model parameters during tracking loops via RAM-based deep copies (`copy.deepcopy`), mitigating physical write latencies and keeping the Git repository clean from binary `.pth` clutter.

### 📊 Quantitative Testing Performance Telemetry
Following training convergence monitored over a stratified clinical partition (70% Train, 15% Val, 15% Test mapping exact *Kellgren-Lawrence* severity allocations), the network yielded the following performance metrics on unseen data:

| Segmentation Metric | Empirical Test Score | Clinical Interpretation & Evaluation |
| :--- | :---: | :--- |
| 🎯 **Mean Intersection over Union (mIoU)** | **0.9569 (95.7%)** | High-fidelity localization. Strict penalty handling suppressed false alarms and boundary blur. |
| 🧬 **Mean Dice Coefficient (F1-Score)** | **0.9772 (97.7%)** | Near-perfect spatial agreement between AI predictions and physician-annotated ground truths. |

**Clinical Dashboard Overlay Diagnostics:** The visualization engine applies dark high-contrast themes styled after professional hospital software, utilizing a realistic bone colormap. It isolates a tri-color spatial evaluation mask overlay:

* 🟢 **True Positives:** correct AI detection
* 🔴 **False Negatives:** missed targets, common in Grade 4 cases due to total joint space collapse
* 🔵 **False Positives:** spurious artifact classification noise

<div align="center">
  <img src="assets/knee_train.jpg" alt="U-Net training curves for knee X-ray joint space segmentation" width="80%" />
  <br/><br/>
  <img src="assets/knee_status.jpg" alt="Knee X-ray segmentation overlay showing true positives, false negatives and false positives" width="80%" />
</div>

---

## 🛠️ Requirements and Installation

The entire workspace exclusively utilizes open-source packages (MIT License). Follow these instructions to set up your isolated development workspace.

### 1. Environment Deployment

Ensure you have **Python 3.10+** installed on your system.

```bash
# Clone the repository
git clone https://github.com/acorvello/data-analysis.git
cd data-analysis

# Create and activate a clean Python virtual environment
python -m venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate

# Upgrade pip
pip install --upgrade pip

# Install dependencies
pip install -r requirements.txt
```

### 📦 Core Dependency Packages

The architecture is built upon the following production backbones:

* **Reinforcement Learning:** `gymnasium[box2d]`, `stable-baselines3`, `pygame` (continuous physics simulations).
* **Statistical Data Mining:** `scikit-learn`, `scipy`, `mlxtend` (advanced clustering, VIF feature pruning, association analytics).
* **Deep Learning & Vision:** `torch`, `torchvision` (tensor back-end optimization, dynamic image skip-concatenations).
* **Data Engineering & Panels:** `opencv-python`, `pandas`, `numpy`, `matplotlib`, `seaborn` (high-speed array streaming, binary parsing, and clinical overlays).

---

## 👤 Author

**Alexsander Corvello da Silveira** — Senior QA Engineer focused on AI-driven testing and applied machine learning.
GitHub: [@acorvello](https://github.com/acorvello)
