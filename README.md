# Deep Learning-based Comparative Segmentation of Thyroid Ultrasound Images

## Executive Summary

This repository contains the code and documentation for a deep learning capstone project focused on automating the segmentation of thyroid structures in ultrasound images. The project compares three state-of-the-art architectures—U-Net, SegNet, and Residual U-Net—to select the most robust model for clinical deployment.

| **Project Focus** | **Key Model Selection Rationale** |
| :--- | :--- |
| **Goal** | Evaluate and compare U-Net, SegNet, and Residual U-Net architectures for automated thyroid segmentation, selecting the most **robust and consistently performing** model. |
| **Model Selected** | **Residual U-Net** |
| **Key Performance** | Achieved a high and stable **Dice Coefficient of 0.9732** on the test set. |
| **Training Environment** | Kaggle GPU Environment and Colab GPU Environment. |

***

## 1. Introduction and Problem Statement

The accurate delineation, or **segmentation**, of the thyroid gland in ultrasound scans is a crucial step in diagnosing thyroid diseases. Traditional manual segmentation is prone to inter-observer variability and is time-consuming. This project aims to overcome these challenges by developing and rigorously analyzing advanced **Deep Learning (DL)** models for automated, high-accuracy segmentation.

The central goal was to compare the U-Net, SegNet, and Residual U-Net architectures to identify the most **stable and robust** model suitable for integration into a real-world clinical workflow, prioritizing consistency and steady performance.

***

## 2. Methodology and Technical Approach

### 2.1. Data Preparation and Preprocessing

* **Dataset:** A comprehensive **Thyroid Ultrasound Dataset** of 3,585 high-quality image-mask pairs was used.
* **Data Split:** The data was partitioned into a **training set (2,509 samples)** and a **testing set (1,076 samples)**.
* **Preprocessing:** Images were converted to grayscale, normalized, and uniformly resized to **$256 \times 256$ pixels** to standardize inputs for all models.

### 2.2. Deep Learning Architectures

The three implemented semantic segmentation models were built using the **PyTorch** framework:
1.  **U-Net:** Employed standard **skip connections** to merge multi-scale features.
2.  **SegNet:** Used Max-Pooling indices for memory-efficient upsampling.
3.  **Residual U-Net:** Enhanced the U-Net with integrated **Residual Blocks** to stabilize training, mitigate the vanishing gradient problem, and ensure more consistent feature learning.

### 2.3. Training Environment and Evaluation

* **Environment:** All models were trained across the **Kaggle GPU environment** and the **Colab GPU environment**.
* **Settings:** Training utilized the **Adam Optimizer** (learning rate of $1e-4$) and **Binary Cross Entropy (BCELoss)** for **25 epochs**.
* **Metric:** Performance was evaluated using the **Dice Coefficient** (a measure of spatial overlap).

***

## 3. Key Findings and Model Selection

### 3.1. Final Model Performance Comparison

| Model Architecture | Final Test Dice Coefficient | Comparative Performance/Stability |
| :--- | :--- | :--- |
| U-Net | **0.9765** | Highest peak accuracy, but training curve showed slight volatility. |
| **Residual U-Net** | **0.9732** | Extremely high accuracy with the most **consistent** and stable performance throughout training. **(Selected Model)** |
| SegNet | 0.7783 | Significantly lower performance for this specific segmentation task. |

### 3.2. Selection Rationale: Residual U-Net

The **Residual U-Net** was selected for final deployment over the U-Net. The inclusion of **Residual Blocks** provided the **most stable training curves** and resulted in highly **reproducible high accuracy** (Dice: **0.9732**). For a clinical application, the inherent **robustness and reliability** of the Residual U-Net are superior to a marginal accuracy gain, ensuring consistent performance in a production environment.

***

## 4. Conclusion and Future Scope

The project successfully demonstrated the potential of deep learning to improve diagnostic efficiency, with the **Residual U-Net** architecture chosen for its excellent performance combined with superior stability.

### Future Work:
* **Advanced Architecture Search:** Investigate the use of pre-trained backbones (e.g., ResNet) within the Residual U-Net via transfer learning to optimize feature extraction further.
* **Clinical Integration:** Develop a plan to deploy the trained model as a service that can interface with a hospital's medical imaging system (PACS) for real-time, large-scale validation.
* **Extension to Multi-Nodule:** Expand the model’s capability to perform multi-class segmentation, allowing it to distinguish between various types of thyroid nodules.

## Deployment
* **Streamlit Link:** https://deep-learning-capstone-dep-spg.streamlit.app/
