# **Bilingual Handwriting Translator (English ↔ Telugu) Using CycleGAN**

## **Introduction**

Handwriting is more than text — it’s a form of visual identity that reflects language, culture, and personal style.  
However, most AI translation systems today focus only on converting *meaning* between languages (e.g., English → Telugu) rather than the *visual handwriting style* itself.  
This creates a cultural and creative gap: there is no digital tool that can take an English handwritten word and reproduce it in the visual handwriting style of Telugu (and vice versa).

---

## **The Problem**

Designers, educators, and students currently rely on:

* Fixed, typed fonts that lack personality or cultural depth.  
* Manual font creation that is time-consuming and inconsistent.  
* Tools that translate words but not handwriting style, limiting creativity in bilingual or cross-script design.

---

## **Our Goal**

This project introduces a **Bilingual Handwriting Translator** powered by **CycleGAN**, a deep generative model capable of unpaired image-to-image translation.  
The system learns to map the handwriting style of English and Telugu words — without needing paired samples — and then redraws any given input in the handwriting style of the target script.

By focusing on *style translation* instead of *semantic translation*, this project aims to:

* Bridge the gap between language and visual culture.  
* Support creative and educational applications, such as bilingual note-taking, calligraphy design, and cultural digitization.  
* Demonstrate the potential of AI in preserving handwriting diversity and cross-script artistry.

---

## **Project Overview**

This project implements a **CycleGAN-based architecture** for cross-lingual handwriting style transfer.  
It translates the visual handwriting style of English ↔ Telugu while keeping the word’s textual meaning unchanged.

The pipeline includes:

* Preprocessing and augmentation of handwriting datasets.  
* CycleGAN training using unpaired English and Telugu word images.  
* Evaluation using **SSIM (Structural Similarity Index)** and **MSE (Mean Squared Error)** for quality assessment.  
* A **Gradio interface** allowing users to upload handwriting samples and visualize translation results interactively.

---
## **Installation and Setup Instructions**

### **1. Clone this repository**
git clone https://github.com/MVJyothiPriya/Bilingual-Handwriting-translator.git

cd Bilingual-Handwriting-translator


### **2️. Create and activate your environment**

If using **Conda**:

bash
conda create -n handwriting python=3.10
conda activate handwriting



---
## **Dataset Information**

### **1. IAM Handwriting Dataset (English)**

* **Source:** [Kaggle – IAM Handwriting Word Database](https://www.kaggle.com/datasets/nibinv23/iam-handwriting-word-database)
* **Type:** Handwritten English word images (PNG, 300 dpi)
* **Size:** ~1.6 GB (subset of official IAM database)
* **Structure:** Flat image folder with filenames like `a01-000u-00-00.png`, `a01-000u-00-01.png`, etc.
* **Use:** Source domain for English handwriting style.

### **2. IIIT-HW Telugu Dataset (v1)**

* **Source:** [CVIT, IIIT Hyderabad](https://cvit.iiit.ac.in/research/projects/cvit-projects/iiit-indic-hw-words)
* **Type:** Telugu handwritten word images (JPG format)
* **Size:** ~3.6 GB
* **Use:** Target domain for Telugu handwriting style.
* **Folder Example:**
  `E:\datasets\IIIT_Telugu\train\writer_001\...`

### **3. Preprocessing Summary**

* Images standardized to 128×128 pixels
* Grayscale normalization to [-1,1]
* **OpenCV filters** (Gaussian blur, dilation, erosion) applied *during training* for style enhancement
* Augmentation ensures balanced exposure of handwriting types across both datasets

---
### Evaluation and Results
Quantitative Evaluation
Translation Direction	SSIM	MSE
English → Telugu	0.451	4377.38
Telugu → English	0.385	3831.50

Lower SSIM and higher MSE indicate greater stylistic change while maintaining stroke structure.

Qualitative Results

Telugu → English: Sharp and contrast-balanced outputs.

English → Telugu: Authentic Telugu-style strokes after brightness correction.

Stable generator–discriminator convergence achieved at epoch 84.

Known Issues

Slight over-brightness in early epochs (corrected via post-processing).

SSIM may undervalue stylistically accurate outputs that differ visually.

Training time ≈ 8–10 hours on GPU for 84 epochs due to unpaired dataset size
----

## **Author**

**Venkata Jyothi Priya Mulaka**
Master’s in Applied Data Science
University of Florida (2024 – 2026)
📧 Email: [mvjpriya@gmail.com](mailto:mvjpriya@gmail.com)  
🔗 GitHub: [https://github.com/MVJyothiPriya](https://github.com/MVJyothiPriya)
