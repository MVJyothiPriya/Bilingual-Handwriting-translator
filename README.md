# Bilingual Handwriting Translator (English ↔ Telugu) Using CycleGAN

## Introduction

Handwriting is more than text — it’s a form of visual identity that reflects language, culture, and personal style. However, most AI translation systems today focus only on converting meaning between languages (e.g., English → Telugu) rather than the visual appearance of writing itself.
This creates a cultural and creative gap: there is no digital tool that can take an English handwritten word and reproduce it in the visual handwriting style of Telugu (and vice versa).

### The Problem

Designers, educators, and students currently rely on:

* Fixed, typed fonts that lack personality or cultural depth.
* Manual font creation that is time-consuming and inconsistent.
* Tools that translate words but not handwriting style, limiting creativity in bilingual or cross-script design.

### Our Goal

This project introduces a **Bilingual Handwriting Translator** powered by **CycleGAN**, a deep generative model capable of unpaired image-to-image translation.
The system learns to map the handwriting style of English and Telugu words — without needing paired samples — and then redraws any given input in the handwriting style of the target script.

By focusing on style translation instead of semantic translation, this project aims to:

* Bridge the gap between language and visual culture.
* Support creative and educational applications, such as bilingual note-taking, calligraphy design, and cultural digitization.
* Demonstrate the potential of AI in preserving handwriting diversity and cross-script artistry.

---

## Project Overview

This project implements a CycleGAN-based architecture for cross-lingual handwriting style transfer.
It translates the visual handwriting style of English ↔ Telugu while keeping the word’s textual meaning unchanged.

The pipeline includes:

* Preprocessing and augmentation of handwriting datasets.
* CycleGAN training using unpaired English and Telugu word images.
* Integration of an **EasyOCR** module for content validation (text-fidelity check).
* A **Streamlit interface** allowing users to upload images or type text and visualize the translation interactively.

---

## Installation and Setup Instructions

### 1. Clone this repository

```bash
git clone https://github.com/<your-username>/Bilingual-Handwriting-Translator.git
cd Bilingual-Handwriting-Translator
```

### 2. Create and activate your environment

If using Conda:

```bash
conda create -n handwriting python=3.10
conda activate handwriting
```

Or with venv:

```bash
python -m venv handwriting_env
handwriting_env\Scripts\activate      # (Windows)
source handwriting_env/bin/activate   # (Linux/Mac)
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Verify setup

Run the setup notebook to verify environment and dataset paths:

```bash
jupyter notebook notebooks/setup.ipynb
```

You should see:

* ✅ Environment setup complete
* ✅ Sample plots of English and Telugu handwriting images

---

## Dataset Information

### 1. IAM Handwriting Database (English)

* **Source:** [IAM Handwriting Database](https://fki.tic.heia-fr.ch/databases/iam-handwriting-database)
* **Type:** Handwritten English word images (PNG, 300 dpi)
* **Size:** ~2.8 GB (115,320 word samples)
* **Structure:** Nested subfolders by writer IDs (e.g., a01, b02, …)
* **Use:** Source domain for English handwriting style.

### 2. IIIT-HW Telugu Dataset (v1)

* **Source:** [CVIT, IIIT Hyderabad](https://cvit.iiit.ac.in/research/projects/cvit-projects/iiit-indic-hw-words)
* **Type:** Telugu handwritten word images (JPG format)
* **Size:** ~3.6 GB
* **Use:** Target domain for Telugu handwriting style.
* **Path Example:** `E:\datasets\IIIT_Telugu\train\writer_001\...`

### 3. Preprocessing

* Images resized to 128×128, converted to grayscale, and normalized to [-1,1].
* Real-time image augmentations applied:

  * Gaussian blur
  * Dilation/Erosion
  * Brightness and contrast adjustments
  * Random rotation/cropping
* This approach preserves dataset diversity without adding synthetic font data.

---

## How to Run the Notebooks

### 1. Data Exploration and Environment Check

Open:

```
notebooks/setup.ipynb
```

Functions:

* Verifies dataset paths and counts
* Displays random handwriting samples
* Confirms correct environment setup

### 2. Model Training

Once verified, run:

```
notebooks/train_cycleGAN.ipynb
```

This notebook:

* Loads English and Telugu word images
* Trains the CycleGAN model for unpaired translation
* Saves checkpoints and generated results in /results

### 3. User Interface (Streamlit)

After training, launch:

```bash
cd ui
streamlit run app.py
```

The Streamlit app provides:

* Image upload or text entry options
* Direction selection (English → Telugu or Telugu → English)
* Visual display of:

  * Original handwriting
  * OCR-detected text
  * Generated translated handwriting
* Downloadable output and OCR match confidence score

---

## Author

**Venkata Jyothi Priya Mulaka**
Master’s in Applied Data Science
University of Florida (2024–2026)
📧 Email: [[your-email@ufl.edu](mailto:your-email@ufl.edu)]
🔗 GitHub: [https://github.com/<your-username>](https://github.com/<your-username>)

---

## Acknowledgements

* **IAM Handwriting Database** — University of Bern
* **IIIT-HW Telugu Dataset** — Center for Visual Information Technology (CVIT), IIIT Hyderabad
* **CycleGAN Paper:** Zhu et al., *Unpaired Image-to-Image Translation using Cycle-Consistent Adversarial Networks*, ICCV 2017
* **EasyOCR:** Jaided AI Library
