# iChart-lite: Accessible Charts for the Visually Impaired using Lightweight Extraction Algorithm

[![Paper](https://img.shields.io/badge/Paper-KSC%202023-blue)](https://www.dbpia.co.kr/Journal/articleDetail?nodeId=NODE11705521)  
[![Demo](https://img.shields.io/badge/Demo-YouTube-red)](https://www.youtube.com/watch?v=9E8D6fh1OvI)  
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

**iChart-lite** is a lightweight chart understanding system designed to help visually impaired users interpret bar charts.

# Overview

<p align="center">
<img src="assets/ichart_overview.png" width="850">
</p>

The system automatically:

1. detects chart components
2. extracts numerical values from bars
3. generates textual descriptions
4. converts the descriptions into speech

Unlike many previous chart-understanding systems, iChart-lite is designed to operate **on lightweight devices and real-world charts** rather than synthetic datasets.

- **Conference:** Korea Software Congress (KSC) 2023
- **Organization:** KIISE
- **Paper PDF:** [Full Paper PDF](papers/iChart.pdf)

---

# Method

The system pipeline consists of three stages.

### 1. Object Detection

YOLOv8 is used to detect three chart components:

- bars
- X-axis labels
- Y-axis labels

### 2. Chart Data Extraction

After detection, the system estimates chart values using:

- OCR (Tesseract)
- heuristic matching between bars and labels
- IQR-based outlier removal
- Y-label prefix/suffix estimation

### 3. Description Generation

The extracted chart information is converted into natural language and synthesized using **Google TTS**.

---

# Example Result

<p align="center">
<img src="assets/ichart_result.png" width="700">
</p>

Example output:

The bar chart shows values for categories A, B, C, and D.  
Category B has the highest value, while category D has the lowest.

---

# Demo

Demo video:

https://www.youtube.com/watch?v=9E8D6fh1OvI

---

# Open in Colab

You can run the notebook directly in Google Colab.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/dukim27/ichart-lite/blob/main/iChart.ipynb)

---

# Dataset

The original dataset consists of **68 real-world bar chart images** collected from web sources.

Classes:

bar  
x_label  
y_label

For demonstration purposes, this repository contains a **small sample subset** of images and annotations.

To reproduce the full experimental results reported in the paper, the complete dataset is required.

---

# Experimental Setting

Training environment

GPU: NVIDIA T4  
Platform: Google Colab  
Epochs: 30  
Batch size: 16

Model

YOLOv8

---

# Repository Structure

```text
ichart-lite
│
├── README.md
├── iChart.ipynb
├── requirements.txt
├── LICENSE
├── .gitignore
│
├── assets
│   ├── ichart_overview.png
│   └── ichart_result.png
│
├── papers
│   └── iChart.pdf
│
├── models
│   ├── yolov8s.yaml
│   └── yolov8s-best-82.pt
│
└── data
    ├── data_82.yaml
    ├── train.txt
    ├── val.txt
    ├── images.json
    ├── images
    └── labels
```

---

# Installation

Clone the repository

```bash
git clone https://github.com/dukim27/ichart-lite
cd ichart-lite
```

Install dependencies

```bash
pip install -r requirements.txt
```

Install OCR engine

```bash
sudo apt install tesseract-ocr
```

---

# Running the Notebook

Open the notebook

```text
iChart.ipynb
```

or run it directly in **Google Colab**.

---

# Citation

If you use this code or reference this project, please cite:

```bibtex
@inproceedings{nam2023ichartlite,
  author    = {Gihun Nam and Danu Kim},
  title     = {iChart-lite: Accessible Charts for the Visually Impaired using Lightweight Extraction Algorithm},
  booktitle = {2023 Korea Software Congress},
  year      = {2023},
  pages     = {1562--1564}
}
```

---

# Contact

Danu Kim  
Korea International School, Jeju Campus
Email: dukim27@kis.ac
