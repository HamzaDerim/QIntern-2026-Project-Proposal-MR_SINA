# Project Mr. Sina: Quantum-Enhanced 3D Neuroimaging and Clinical Decision Support System

[![Event: QIntern 2026](https://img.shields.io/badge/Event-QIntern_2026-blue.svg)](https://qworld.net/qintern-2026/)
[![Status: Research & Development](https://img.shields.io/badge/Status-Proposal_%26_R%26D-orange.svg)]()
[![Live Demo: Web App](https://img.shields.io/badge/Live_App-Mr._Sina_Web-success.svg)](https://mrsina.up.railway.app/)

## 🌐 Live Web Application
You can access the current classical deployment of our Clinical Decision Support System interface here: 
**[Mr. Sina Web Application](https://mrsina.up.railway.app/)**

## 📌 Abstract
Project Mr. Sina is an AI-driven Clinical Decision Support System (CDSS) designed for the objective, early, and personalized diagnosis of chronic psychiatric disorders, particularly Bipolar Disorder and Schizophrenia. 

This research repository aims to transition our existing, fully automated classical neuroimaging pipeline into the NISQ (Noisy Intermediate-Scale Quantum) era. By integrating **Quantum Image Processing (QIP)**, **Quantum Machine Learning (QML)**, and **Quantum Approximate Optimization Algorithm (QAOA)**, this project presents an end-to-end hybrid medical architecture—from voxel-level quantum image enhancement to continuous-time quantum dynamic system modeling.

## ⚙️ 1. Completed Baseline (Classical Pipeline)
In the first phase of the project, we successfully established an automated Linux (Ubuntu/WSL) pipeline that extracts high-dimensional anatomical features from raw brain MRI scans (DICOM):

| Stage | Tool / Command | Description |
| :--- | :--- | :--- |
| **Data Conversion** | `dcm2niix` | Converts raw hospital DICOM data into the 3D NIfTI (`.nii.gz`) medical imaging standard. |
| **Skull Stripping** | FSL `bet` | Asynchronously removes non-brain tissues (skull, eyes, neck) from structural MRI scans. |
| **Image Registration** | FSL `flirt` | Spatially aligns and registers images to a standard anatomical template (MNI152). |
| **Segmentation** | FreeSurfer `recon-all` | Separates gray/white matter boundaries, measures cortical thickness, and performs volumetric segmentation of deep brain structures (e.g., Amygdala, Hippocampus). |
| **Feature Extraction** | `asegstats2table` & `aparcstats2table` | Transforms hundreds of anatomical measurements into numerical matrices for machine learning ingestion. |

## 🚀 2. Proposed Quantum Modules & Methodology
To surpass the limitations of classical deep learning, we are integrating three core quantum layers into the Mr. Sina framework:

### A. Quantum Image Processing (QIP)
* **Quantum State Preparation:** 3D structural MRI data will be encoded into quantum states (using amplitude and angle embeddings) via FRQI or NEQR algorithms.
* **Quantum Voxel Enhancement:** Specialized quantum-domain filters will be designed to suppress microstructural noise and enhance gray-matter contrast in deep subcortical regions where classical filters fall short.

### B. Quantum Machine Learning (QML) & Continuous-Time Modeling
* **Quantum Convolutional Neural Networks (QCNN):** Parameterized Quantum Circuits (PQCs) will be developed to capture spatial features from dimensionality-optimized 3D MR images.
* **Quantum Neural ODEs (Q-ODEs):** Building on our expertise in deep learning for dynamic systems, we will model the longitudinal structural decay trajectories of psychiatric diseases using continuous-time Q-ODEs, solving differential equations via quantum circuits.

### C. Quantum Optimization for Mathematical Biomarker Selection
* **QUBO Formulation:** The problem of selecting the most diagnostically sensitive clinical biomarkers from high-dimensional FreeSurfer outputs (cortical thickness and volume) will be transformed into a Quadratic Unconstrained Binary Optimization (QUBO) model.
* **QAOA Implementation:** To alleviate the computational bottleneck of traditional MILP (Mixed-Integer Linear Programming) models, the QUBO matrix will be solved using QAOA to determine the optimal subset of predictive features.

## 📂 Repository Structure

* `pipeline/`: Automation scripts for DICOM-NIfTI conversion, FSL skull stripping, and FreeSurfer `recon-all`.
* `qip/`: Circuits for 3D MRI amplitude encoding and quantum contrast filtering.
* `qml/`: QCNN architectures, Physics-Informed Quantum Neural Networks (Q-PINNs), and Quantum Neural ODE prototypes.
* `optimization/`: QUBO matrices and QAOA optimization scripts for clinical data.
* `web_app/`: Source code for the FastAPI/Python backend serving the [live application](https://mrsina.up.railway.app/).
* `docs/`: Academic reports, pitch decks, and medical/quantum mathematical foundations.

## 🛠️ Tech Stack

* **Neuroimaging:** FreeSurfer, FSL (FMRIB Software Library), dcm2niix
* **Quantum Computing:** PennyLane, Qiskit
* **Deep Learning & Dynamic Systems:** PyTorch, Torchdiffeq
* **Web & Data Science:** Python, FastAPI, NumPy, Pandas, Railway (Deployment)

## 👨‍💻 Research Team & Contacts

* **Hamza Derim** - *Project Captain / Data Science & AI Specialist*
* **Assoc. Prof. Çiğdem Özer** - *Radiologist / Academic Advisor*
* **Dr. Ekrem Furkan Uçak** - *Psychiatrist / Clinical Advisor*

---
*Project Mr. Sina is advancing through advanced R&D under QIntern 2026 to demonstrate the transformative power of quantum image processing and applied mathematical optimization in clinical psychiatry.*
