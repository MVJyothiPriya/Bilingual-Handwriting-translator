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

This project introduces a **Bilingual Handwriting Translator** powered by **CycleGAN**, a deep generative model capable of *unpaired image-to-image translation.*  
The system learns to map the handwriting style of English and Telugu words — without needing paired samples — and then redraws any given input in the handwriting style of the target script.

By focusing on *style translation* instead of *semantic translation*, this project aims to:

* Bridge the gap between language and visual culture.  
* Support creative and educational applications such as bilingual note-taking, calligraphy design, and cultural digitization.  
* Demonstrate the potential of AI in preserving handwriting diversity and cross-script artistry.

---

## **Project Overview**

This project implements a **CycleGAN-based architecture** for cross-lingual handwriting style transfer.  
It translates the visual handwriting style of English ↔ Telugu while keeping the word’s textual meaning unchanged.

### **Pipeline Overview:**
* Preprocessing and augmentation of handwriting datasets.  
* CycleGAN training using unpaired English and Telugu word images.  
* Integration of **SSIM (Structural Similarity Index)** and **MSE (Mean Squared Error)** metrics for style evaluation and visual similarity.  
* A **Gradio interface** allowing users to upload handwriting samples and visualize the translation interactively.

---

## **Installation and Setup Instructions**

### **1️⃣ Clone this repository**
```bash
git clone https://github.com/MVJyothiPriya/Bilingual-Handwriting-translator.git
cd Bilingual-Handwriting-translator
