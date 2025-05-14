# Span-Labelling Named Entity Recognition (NER) with Encoder-Only and Decoder-Only Models

This repository contains code and resources for a comparative study of span-based Named Entity Recognition (NER) using both encoder-only (BERT) and decoder-only (Llama 3.1 8B) neural architectures. The project benchmarks both full (complex) and simplified (BIO-only) tagsets across in-domain and out-of-domain test sets.

## Dataset

- **Source:** [UniversalNER](https://github.com/UniversalNER)
- **Corpora:**  
  - `en_ewt` (English Web Treebank): split into train, dev, test  
  - `en_pud` (Parallel Universal Dependencies): used as out-of-domain test set

---

## Models

### BERT Encoder-Only

- **Model:** `bert-base-uncased` (via Hugging Face Transformers)
- **Tagsets:**  
  - *Complex*: 7-label set (B-LOC, I-LOC, B-PER, I-PER, B-ORG, I-ORG, O)  
  - *Simple*: BIO-only (B, I, O)

### Llama 3.1 8B Decoder-Only

- **Model:** Llama 3.1 8B Instruct (via Hugging Face Transformers, quantized with bitsandbytes)
- **Approach:** Prompt-based inference for BIO tag generation; no fine-tuning
- **Limitations:**  
  - Model failed to produce correct NER outputs (all main metrics were zero)

---

## Evaluation
  - Token-level Precision, Recall, F1
  - Span-level (labelled and unlabelled) Precision, Recall, F1
  - Macro and Micro F1
- **Evaluation:**  
  - Both in-domain (`en_ewt` test) and out-of-domain (`en_pud` test) splits

---

## How to Run

1. **Clone the repository:**
2. **Install dependencies:**

3. **Download datasets:**  
The scripts automatically download and preprocess the UniversalNER datasets.

4. **Run BERT Model (Jupyter/Colab):**
- Open `BERT_Complex.ipynb` or `BERT_Simple.ipynb`
- Run all cells to train and evaluate

5. **Run Llama Model (Jupyter/Colab):**
- Open `Decoder_Simple.ipynb` or `Decoder_Complex.ipynb`
- Ensure you have access to the Llama weights and Hugging Face token
- Run all cells for prompt-based inference

---




