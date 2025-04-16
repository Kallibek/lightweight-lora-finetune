# Lightweight Fine‑Tuning with LoRA (Jupyter Notebook)

A self‑contained Jupyter notebook demonstrating parameter‑efficient fine‑tuning (PEFT) of GPT‑2 using LoRA on the SST‑2 sentiment‑classification task.

---

## Table of Contents

1. [Overview](#overview)  
2. [Features](#features)  
3. [Files](#files)  
4. [Prerequisites](#prerequisites)  
5. [Installation](#installation)  
6. [How to Run](#how-to-run)  
7. [Notebook Structure](#notebook-structure)  
8. [Results](#results)  
9. [License](#license)  

---

## Overview

This project contains a single Jupyter notebook (`LightweightFineTuning.ipynb`) that:

- Loads GPT‑2 and evaluates its out‑of‑the‑box performance on SST‑2.  
- Wraps GPT‑2 in a LoRA adapter for parameter‑efficient fine‑tuning.  
- Fine‑tunes on a subset of SST‑2 (10 K train / 500 validation).  
- Compares baseline vs. LoRA‑fine‑tuned accuracy.  

All code—from data loading through training, evaluation, and final comparison—is in one notebook for easy exploration and replication.

---

## Features

- **PEFT Technique:** LoRA (Low‑Rank Adaptation)  
- **Base Model:** GPT‑2 via `AutoModelForSequenceClassification`  
- **Dataset:** SST‑2 (GLUE) subset  
- **Evaluation:** Hugging Face `Trainer` with accuracy metric  
- **Parameter Efficiency:** ≈0.24 % of parameters trained  

---

## Files

- `LightweightFineTuning.ipynb` — self‑contained notebook with all code and commentary  
- `requirements.txt` — list of Python dependencies  

---

## Prerequisites

- Python 3.8+  
- [Virtualenv](https://docs.python.org/3/library/venv.html) or Conda  
- Internet connection (to download pretrained weights & dataset)  

---

## Installation

1. Clone the repository:
   ```bash
   git clone <your‑repo‑url>
   cd <repo‑folder>
   ```

2. Create and activate a virtual environment:
   ```bash
   python -m venv .venv
   source .venv/bin/activate        # Linux / macOS
   .venv\Scripts\activate           # Windows
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

---

## How to Run

1. Launch Jupyter Lab or Notebook:
   ```bash
   jupyter lab
   # or
   jupyter notebook
   ```

2. Open `LightweightFineTuning.ipynb`.

3. Execute all cells from top to bottom.  
   - The notebook will download SST‑2 and GPT‑2, tokenize and evaluate the baseline model, apply LoRA, fine‑tune, and finally report accuracy improvements.

---

## Notebook Structure

1. **Setup & Imports**  
   - Load libraries, configure tokenizer/model.
2. **Data Loading & Preprocessing**  
   - Download SST‑2, tokenize, and set up train/validation splits.
3. **Baseline Evaluation**  
   - Evaluate vanilla GPT‑2 sequence classifier.
4. **LoRA Configuration**  
   - Set up `LoraConfig`, wrap model with PEFT adapter.
5. **Fine‑Tuning**  
   - Trainer setup and 3‑epoch training loop.
6. **Inference & Evaluation**  
   - Reload base model, load LoRA adapter, and re‑evaluate.
7. **Results & Comparison**  
   - Print baseline vs. LoRA‑fine‑tuned accuracy.

---

## Results

| Model               | Accuracy |
|---------------------|---------:|
| GPT‑2 (baseline)    |    ~52 % |
| GPT‑2 + LoRA (PEFT) |    ~73 % |

---
