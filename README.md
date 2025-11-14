project:
  title: "Bilingual Handwriting Translator (English ↔ Telugu) Using CycleGAN"

sections:

  - Introduction: |
      Handwriting is more than text — it’s a form of visual identity that reflects language, culture, and personal style.
      However, most AI translation systems today focus only on converting *meaning* between languages (e.g., English → Telugu)
      rather than the *visual handwriting style* itself. This creates a cultural and creative gap:
      there is no digital tool that can take an English handwritten word and reproduce it
      in the visual handwriting style of Telugu (and vice versa).

  - Problem: |
      Designers, educators, and students currently rely on:
        - Fixed, typed fonts that lack personality or cultural depth.
        - Manual font creation that is time-consuming and inconsistent.
        - Tools that translate words but not handwriting style, limiting creativity in bilingual or cross-script design.

  - Goal: |
      This project introduces a **Bilingual Handwriting Translator** powered by **CycleGAN**, 
      a deep generative model capable of *unpaired image-to-image translation*.
      The system learns to map the handwriting style of English and Telugu words — without needing paired samples —
      and then redraws any given input in the handwriting style of the target script.

      **Objectives:**
        - Bridge the gap between language and visual culture.
        - Support creative and educational applications such as bilingual note-taking, calligraphy design, and cultural digitization.
        - Demonstrate AI’s potential in preserving handwriting diversity and cross-script artistry.

  - Project_Overview: |
      This project implements a **CycleGAN-based architecture** for cross-lingual handwriting style transfer.
      It translates the visual handwriting style of English ↔ Telugu while keeping the word’s textual meaning unchanged.

      **Pipeline Overview:**
        - Preprocessing and augmentation of handwriting datasets.
        - CycleGAN training using unpaired English and Telugu word images.
        - Integration of **SSIM (Structural Similarity Index)** and **MSE (Mean Squared Error)** metrics for style evaluation.
        - A **Gradio interface** that allows users to upload handwriting samples and visualize translations interactively.

  - Installation_and_Setup:
      - Step_1_Clone_Repository: |
          ```bash
          git clone https://github.com/MVJyothiPriya/Bilingual-Handwriting-translator.git
          cd Bilingual-Handwriting-translator
          ```
      - Step_2_Create_Environment: |
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
      - Step_3_Install_Dependencies: |
          ```bash
          pip install -r requirements.txt
          ```
      - Step_4_Verify_Setup: |
          ```bash
          jupyter notebook notebooks/setup.ipynb
          ```
          Expected:
            - Successful library imports
            - Dataset paths verified
            - Sample handwriting images displayed

  - How_to_Run_the_Notebook:
      - Dataset_Check: |
          Open:
          ```
          notebooks/setup.ipynb
          ```
          This notebook:
            - Loads and previews English (IAM) and Telugu (IIIT-HW) samples
            - Confirms dataset accessibility and structure
            - Ensures correct environment configuration
      - Model_Training: |
          Run:
          ```
          notebooks/train_cycleGAN.ipynb
          ```
          During training:
            - Images resized to 128×128, converted to grayscale, normalized to [-1,1]
            - OpenCV augmentations applied dynamically:
              - Gaussian Blur → cursive handwriting
              - Dilation → bold strokes
              - Erosion → calligraphic thin strokes
          After training:
            - Generated outputs saved in `/results`
            - **SSIM** and **MSE** metrics computed automatically
      - Launch_Interface: |
          ```bash
          cd ui
          python app_gradio.py
          ```
          Features:
            - Upload handwriting images
            - Select translation direction (English → Telugu or Telugu → English)
            - View original vs. translated samples
            - Display SSIM and MSE metrics

  - Dataset_Information:
      - IAM_Handwriting_Dataset:
          Source: "https://www.kaggle.com/datasets/nibinv23/iam-handwriting-word-database"
          Type: "Handwritten English word images (PNG)"
          Size: "~1.6 GB"
          Use: "Source domain for English handwriting style"
      - IIIT_Telugu_Dataset:
          Source: "https://cvit.iiit.ac.in/research/projects/cvit-projects/iiit-indic-hw-words"
          Type: "Telugu handwritten word images (JPG)"
          Size: "~3.6 GB"
          Use: "Target domain for Telugu handwriting style"
      - Preprocessing:
          - Images resized to 128×128 pixels
          - Normalized to [-1,1]
          - Augmentation: Gaussian blur, dilation, erosion
          - Balanced exposure across handwriting domains

  - Results_and_Known_Issues:
      - Quantitative_Evaluation:
          Table:
            - Translation: "English → Telugu"
              SSIM: 0.451
              MSE: 4377.38
            - Translation: "Telugu → English"
              SSIM: 0.385
              MSE: 3831.50
          Notes: "Lower SSIM and higher MSE indicate stronger style variation with preserved structure."
      - Qualitative_Observations: |
          - Telugu → English: Outputs are sharp and contrast-balanced.
          - English → Telugu: Stylized strokes successfully mimic Telugu handwriting after brightness normalization.
      - Known_Issues:
          - Slight over-brightness in early epochs (fixed post-processing)
          - SSIM undervalues stylistic accuracy
          - Long GPU training (~8–10 hours for 100 epochs)

  - Author:
      Name: "Venkata Jyothi Priya Mulaka"
      Role: "Master’s in Applied Data Science"
      University: "University of Florida (2024–2026)"
      Email: "mvjpriya@gmail.com"
      GitHub: "https://github.com/MVJyothiPriya"

  - References:
      - "[1] J.-Y. Zhu, T. Park, P. Isola, and A. A. Efros, 'Unpaired Image-to-Image Translation Using Cycle-Consistent Adversarial Networks,' IEEE CVPR, 2017. Available: https://arxiv.org/abs/1703.10593"
      - "[2] Kaggle, 'IAM Handwriting Word Database,' 2023. Available: https://www.kaggle.com/datasets/nibinv23/iam-handwriting-word-database"
      - "[3] IIIT Hyderabad CVIT, 'Indic Handwritten Data (Telugu Script),' 2023. Available: https://cvit.iiit.ac.in/research/projects/cvit-projects/indic-hw-data"
      - "[4] Hugging Face, 'Gradio Documentation,' 2024. Available: https://www.gradio.app/docs"
      - "[5] V. J. P. Mulaka, 'Bilingual Handwriting Translator – CycleGAN Project Repository,' University of Florida, 2025. Available: https://github.com/MVJyothiPriya/Bilingual-Handwriting-translator"

metadata:
  last_updated: "November 2025"
  language: "Python 3.10"
  framework: "PyTorch"
  interface: "Gradio"
  gpu_training: true
  reproducibility: "Fully reproducible end-to-end following setup instructions"
