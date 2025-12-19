# Hear the Words: An AI Predictor for Lyric Intelligibility

> **A hybrid AI framework designed to predict the intelligibility of song lyrics for listeners with hearing loss by combining source separation, speech recognition, and psychoacoustic modeling.**

![Project Status](https://img.shields.io/badge/Status-Active-success) ![Python](https://img.shields.io/badge/Python-3.8%2B-blue) ![PyTorch](https://img.shields.io/badge/PyTorch-Deep%20Learning-red) ![License](https://img.shields.io/badge/License-MIT-green)

## 📖 About

**Hear the Words** is a project designed to solve the **"Measurement Gap"** in assistive audio technology. Current hearing aids are highly optimized for speech but often fail to render music lyrics intelligibly. With over 430 million people worldwide suffering from disabling hearing loss, the inability to distinguish lyrics from background instrumentation leads to a frustrating listening experience.

This project implements a novel **three-stage AI pipeline** that:
1.  **Isolates** vocals from music.
2.  **Analyzes** them using both linguistic (ASR) and psychoacoustic (HASPI) metrics.
3.  **Fuses** these features to predict a **"Word Correct Rate" (WCR)**.

This system serves as a benchmark tool to help audio engineers and researchers design better hearing aids and audio processing algorithms for music.

---

## 🚀 Key Features

* **State-of-the-art Vocal Isolation:** Utilizes **Hybrid Transformer Demucs (HT-Demucs)** to separate clean vocals from complex musical mixes.
* **Dual-Path Analysis:** Simultaneously evaluates:
    * *Linguistic Clarity* using OpenAI's **Whisper** model.
    * *Perceptual Clarity* using the **HASPI** metric adapted for hearing loss profiles.
* **Acoustic Feature Extraction:** Analyzes pitch ($F0$), energy (RMS), and spectral characteristics using **Librosa** to capture vocal nuances.
* **XGBoost Fusion Model:** Uses an ensemble regression technique to fuse heterogeneous features and predict a final intelligibility score with high correlation to human perception.
* **Scalable Architecture:** Designed to process large music catalogs and diverse hearing profiles efficiently.

---

## ⚙️ System Architecture

The system follows a modular three-stage pipeline:

1.  **Vocal Separation:** The input song is processed to isolate the vocal stem.
2.  **Feature Extraction:** The stem is analyzed for psychoacoustic clarity (HASPI), linguistic accuracy (ASR), and acoustic signal properties.
3.  **Prediction:** These features are fused to predict the Word Correct Rate (WCR).

<img width="700" height="578" alt="image" src="https://github.com/user-attachments/assets/21749917-233e-44f7-9232-e86f0b8f64f1" />

---

## 🛠️ Requirements

To run this project, ensure your environment meets the following specifications:

### Hardware
* **GPU:** NVIDIA GPU (GTX 1650 / RTX series or higher) recommended for efficient model training and inference.

### Software
* **OS:** Windows 10/11 or Linux (Ubuntu recommended for ML tasks).
* **Language:** Python 3.8 or higher.

### Key Libraries
* **Deep Learning:** `PyTorch` (for HT-Demucs and Whisper models).
* **Audio Processing:** `Librosa`, `FFmpeg` (signal processing and format conversion).
* **Machine Learning:** `Scikit-learn`, `XGBoost` (feature processing and regression).

---

## 📊 Performance & Results

The **Hear the Words** system successfully demonstrated that a hybrid approach—combining signal processing, listener modeling, and content analysis—outperforms single-domain metrics.

### Metrics
| Metric | Performance |
| :--- | :--- |
| **ASR Accuracy** | **79.16%** (using Whisper Medium model) |
| **Correlation ($r$)** | **0.72** (Pearson coefficient against ground-truth human data) |

### Impact
By achieving a strong correlation with human perception, this project provides a robust benchmark tool for the **Cadenza CLIP1 Challenge**. This innovation contributes to the development of "smart" hearing aids that can dynamically adjust to musical inputs, ensuring that music remains an enjoyable and inclusive experience for the hearing-impaired community.

### Output Visualization
* **Output 1:** Transcription Accuracy Console.
* **Output 2:** Predicted vs. Actual Correlation Plot.

<img width="531" height="353" alt="image" src="https://github.com/user-attachments/assets/efaea60b-05f1-45e8-822e-e786eb2d7fa4" />

---

## 📄 References

1.  G. Roa Dabike et al., “ICASSP 2026 Cadenza Challenge: Predicting Lyric Intelligibility,” Cadenza Challenge Website, 2025.
2.  A. Défossez, S. Rouard, and F. Massa, “Hybrid Transformer Demucs for Music Source Separation,” Proc. IEEE ICASSP, 2023.
3.  J. M. Kates and K. H. Arehart, “The Hearing-Aid Speech Perception Index (HASPI),” J. Acoust. Soc. Am., vol. 135, no. 4, 2014.
4.  A. Radford et al., “Robust Speech Recognition via Large-Scale Weak Supervision,” Proc. ICML, 2022.
5.  S. Syed et al., “Exploiting Music Source Separation for Automatic Lyrics Transcription with Whisper,” Proc. IEEE ICASSP, 2024.
