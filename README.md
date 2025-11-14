Bilingual Handwriting Translator (English ↔ Telugu) Using CycleGAN
Introduction

Handwriting is more than text — it’s a form of visual identity that reflects language, culture, and personal style. However, most AI translation systems today focus only on converting meaning between languages (e.g., English → Telugu) rather than the visual appearance of writing itself.
This creates a cultural and creative gap: there is no digital tool that can take an English handwritten word and reproduce it in the visual handwriting style of Telugu (and vice versa).

The Problem

Designers, educators, and students currently rely on:

Fixed, typed fonts that lack personality or cultural depth.

Manual font creation that is time-consuming and inconsistent.

Tools that translate words but not handwriting style, limiting creativity in bilingual or cross-script design.

Our Goal

This project introduces a Bilingual Handwriting Translator powered by CycleGAN, a deep generative model capable of unpaired image-to-image translation.
The system learns to map the handwriting style of English and Telugu words — without needing paired samples — and then redraws any given input in the handwriting style of the target script.

By focusing on style translation instead of semantic translation, this project aims to:

Bridge the gap between language and visual culture.

Support creative and educational applications, such as bilingual note-taking, calligraphy design, and cultural digitization.

Demonstrate the potential of AI in preserving handwriting diversity and cross-script artistry.

Project Overview

This project implements a CycleGAN-based architecture for cross-lingual handwriting style transfer.
It translates the visual handwriting style of English ↔ Telugu while keeping the word’s textual meaning unchanged.

The pipeline includes:

Preprocessing and augmentation of handwriting datasets.

CycleGAN training using unpaired English and Telugu word images.

Integration of SSIM (Structural Similarity Index) and MSE (Mean Squared Error) metrics for style evaluation and visual similarity analysis.

A Gradio interface allowing users to upload handwriting samples and visualize the translation interactively.

Installation and Setup Instructions
1. Clone this repository
git clone https://github.com/<your-username>/Bilingual-Handwriting-Translator.git
cd Bilingual-Handwriting-Translator

2. Create and activate your environment

If using Conda:

conda create -n handwriting python=3.10
conda activate handwriting


Or with venv:

python -m venv handwriting_env
handwriting_env\Scripts\activate      # (Windows)
source handwriting_env/bin/activate   # (Linux/Mac)

3. Install dependencies
pip install -r requirements.txt

4. Verify setup

Run:

jupyter notebook notebooks/setup.ipynb


You should see:

Successful library imports

Dataset paths verified

Sample handwriting images displayed

How to Run the Notebook
1. Dataset Check & Environment Test

Open:

notebooks/setup.ipynb


This notebook:

Loads and previews English (IAM) and Telugu (IIIT-HW) word samples

Confirms dataset accessibility and format

Ensures that the environment is configured correctly

2. Model Training

Run:

notebooks/train_cycleGAN.ipynb


During training:

Images are resized to 128×128, converted to grayscale, and normalized to [-1,1].

OpenCV filters are applied dynamically for style diversity:

Gaussian Blur: simulates soft, cursive pen strokes.

Dilation: produces thicker or bold handwriting styles.

Erosion: creates lighter, finer strokes resembling calligraphy.

These augmentations help the model generalize across different handwriting forms without synthetic fonts.

After training completes:

The generated outputs are saved in /results.

SSIM and MSE metrics are computed automatically to evaluate translation accuracy and visual consistency between original and generated handwriting.

3. Launch the Interactive Interface

After training, open:

cd ui
python app_gradio.py


The Gradio app allows users to:

Upload handwriting images in English or Telugu

Select translation direction (English → Telugu or Telugu → English)

View original and translated handwriting side-by-side

Display SSIM and MSE similarity metrics for each translation

Dataset Information
1. IAM Handwriting Dataset (English)

Source: Kaggle – IAM Handwriting Word Database

Type: Handwritten English word images (PNG, 300 dpi)

Size: ~1.6 GB (subset of official IAM database)

Structure: Flat image folder with filenames like a01-000u-00-00.png, a01-000u-00-01.png, etc.

Use: Source domain for English handwriting style.

2. IIIT-HW Telugu Dataset (v1)

Source: CVIT, IIIT Hyderabad

Type: Telugu handwritten word images (JPG format)

Size: ~3.6 GB

Use: Target domain for Telugu handwriting style.

Folder Example: datasets/TeluguSeg/train/writer_001/...

3. Preprocessing Summary

Images standardized to 128×128 pixels

Grayscale normalization to [−1,1]

OpenCV filters (Gaussian blur, dilation, erosion) applied during training for style enhancement

Augmentation ensures balanced exposure of handwriting types across both datasets

Results and Known Issues
Quantitative Evaluation
Translation	SSIM	MSE
English → Telugu	0.451	4377.38
Telugu → English	0.385	3831.50

Lower SSIM and higher MSE reflect greater stylistic variation while maintaining structure.

Qualitative Observations

Telugu → English: Outputs are clear, with well-balanced contrast and readability.

English → Telugu: Stylized strokes capture Telugu handwriting texture after brightness normalization.

Known Issues

Slight over-brightness in early epochs (fixed through post-processing).

SSIM may undervalue visually correct but stylistically distinct translations.

CycleGAN requires significant GPU time (~8–10 hours for 100 epochs).

Author

Venkata Jyothi Priya Mulaka
Master’s in Applied Data Science
University of Florida (2024 – 2026)
📧 Email: mvjpriya@gmail.com

🔗 GitHub: https://github.com/MVJyothiPriya
