# Clinical-Diagnostic-Classifiers-BIOINF-580-Final-Project-
CNN to detect skin lesions and ECG sinus rythym detection algorithm 

## Project Overview
This repository contains the code and analysis for my Master's final project in BIOINF 580, Intro to Signal Processing and Machine Learning. The project consists of two independent clinical diagnostic tasks using deep learning:
1.  **ECG Signal Analysis:** A binary classifier to distinguish between normal sinus rhythm and atrial fibrillation (AFib).
2.  **Dermatoscopic Image Analysis:** A multi-class Convolutional Neural Network (CNN) to categorize skin lesions into 7 diagnostic types.

**Status:** Completed Academic Project
**Language:** Python

---

## Task 1: ECG Signal Classification

### Objective
Build a model to classify 300 Hz ECG recordings as either **Healthy** or **AFib**.

### Methodology
* **Architecture:** Implemented a **Hybrid CNN-Transformer** model.
    * **CNN Encoder:** Three 1D-convolutional blocks to extract local physiological features.
    * **Transformer:** A 2-layer Transformer Encoder with positional embeddings to capture long-range temporal dependencies and heartbeat sequencing.
* **Data Handling:** Utilized 3,000 training samples and 500 validation samples.
* **Optimization:**
    * Applied **loss weighting** to address class imbalance between healthy and AFib samples.
    * Determined the optimal decision threshold using the **Precision-Recall curve** on training data to maximize the F1 score without data leakage.

### Performance
| Metric | Score |
| :--- | :--- |
| **AUROC** | **0.9748** |
| **F1 Score** | **0.8175** |

---

## Task 2: Skin Lesion Classification (DermaMNIST)

### Objective
Develop a multi-class classifier to identify 7 distinct types of skin lesions using dermatoscopic images from the **DermaMNIST** dataset.

### Methodology
* **Architecture:** Custom **Convolutional Neural Network (CNN)** optimized for 64x64 RGB medical images.
* **Preprocessing:** Utilized standard image normalization and resizing suitable for the MedMNIST benchmark.
* **Evaluation:** Performance was evaluated using the One-vs-Rest (OvR) Area Under the Curve (AUC) metric, averaging performance across all 7 diagnostic categories.

### Performance
| Metric | Score |
| :--- | :--- |
| **Mean OvR AUC** | **0.9088** |

---

## Installation & Usage

### Prerequisites
* Python 3.8+
* Jupyter Notebook

### Dependencies
Install the required libraries:
```
pip install numpy torch scikit-learn medmnist
```
Running the Project

1. Clone this repository.

2. Ensure you have data files (ecg_train_data.npz, ecg_valid_data.npz) in the root directory. Note: Original .npz files exceed GitHub sharing limits, but custom ECG data can be obtained/generated for testing. Note2: The DermaMNIST data is downloaded automatically by the script.

3. Open the notebook:
```
jupyter notebook Final_Project_jarbaas.ipynb
```
4. Run all cells to train the models and reproduce the results.

Acknowledgments

- Course: BIOINF 580 (University of Michigan)

- Datasets: Private course data (ECG) and MedMNIST (Derma).

- AI Tools: Gemini was used to assist with debugging pytorch tensor shapes and optimizing transformer syntax.


