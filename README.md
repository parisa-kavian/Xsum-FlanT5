<div align="center">

# Xsum-FlanT5

### Parameter-efficient abstractive news summarization with FLAN-T5 + LoRA

<img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white"/>
<img src="https://img.shields.io/badge/Hugging%20Face-FFD21E?style=flat-square&logo=huggingface&logoColor=black"/>
<img src="https://img.shields.io/badge/PEFT%20%C2%B7%20LoRA-444?style=flat-square"/>
<img src="https://img.shields.io/badge/Model-google%2Fflan--t5--large-blue?style=flat-square"/>
<img src="https://img.shields.io/badge/Dataset-XSum-orange?style=flat-square"/>

</div>

> Fine-tuning **`google/flan-t5-large`** for **extreme (single-sentence) abstractive summarization** on the **XSum** news dataset — using **Parameter-Efficient Fine-Tuning (PEFT)** with **LoRA** to cut compute and memory cost dramatically while adapting a large model on modest hardware.

---

## The idea

XSum is an *extreme summarization* benchmark: each article is condensed into a single, highly abstractive sentence. Full fine-tuning of a `flan-t5-large` model is expensive, so this project instead trains only a small set of **low-rank adapter matrices (LoRA)** while keeping the base weights frozen. The result: a fraction of the trainable parameters, a fraction of the memory, and a model that still adapts to the summarization task.

| Without LoRA | With LoRA (this project) |
| --- | --- |
| Update **all** ~780M parameters | Update only small **low-rank adapters** |
| High GPU memory | Fits on constrained hardware |
| Slow, costly | Fast, cheap to train |

---

## Setup at a glance

| Component | Choice |
| --- | --- |
| **Base model** | `google/flan-t5-large` |
| **Dataset** | XSum (news articles → one-sentence summaries) |
| **Fine-tuning** | PEFT + LoRA (base weights frozen) |
| **Training subset** | 10,000 samples from XSum train |
| **Test subset** | 100 samples from XSum test |
| **Max input length** | 512 tokens |
| **Max summary length** | 39 tokens |
| **Output** | Generated summaries collected in a `pandas` DataFrame |

> Subsets were used deliberately to keep the experiment runnable under limited compute, while still demonstrating the full PEFT/LoRA workflow end to end.

---

## Pipeline

```
XSum dataset
     │  flan-t5-large tokenizer (input ≤ 512, summary ≤ 39 tokens)
     ▼
[ Preprocess & tokenize ] ──► [ Wrap flan-t5-large with LoRA adapters (PEFT) ]
     │
     ▼
[ Train adapters on 10k samples ] ──► [ Generate summaries on test set ]
     │
     ▼
[ Collect predictions in a DataFrame ]
```

---

## Features

- **Efficient fine-tuning** — PEFT + LoRA slash trainable parameters and memory footprint.
- **Strong base model** — instruction-tuned `flan-t5-large`.
- **Established benchmark** — XSum, the standard for extreme abstractive summarization.
- **Reproducible inference** — generates and stores summaries for the test set.

---

## Getting started

```bash
git clone https://github.com/parisa-kavian/Xsum-FlanT5.git
cd Xsum-FlanT5
pip install -r requirements.txt
```

Then open the notebook and run the cells to fine-tune the adapters and generate summaries.

---

## Possible next steps

- [ ] Report **ROUGE-1/2/L** to quantify the base vs. LoRA-tuned gain
- [ ] Scale to the full XSum training set
- [ ] Compare LoRA ranks / target modules
- [ ] Push the adapter to the Hugging Face Hub for one-line reuse

---

## Tech stack

`Hugging Face Transformers` · `PEFT` · `LoRA` · `Datasets` · `google/flan-t5-large` · `pandas`

---

## Author

**Parisa Kavianpour** — Applied ML Researcher
[Website](https://parisa-kavian.github.io/) · [Google Scholar](https://scholar.google.com/citations?user=Y5cXz8QAAAAJ&hl=en) · [LinkedIn](https://www.linkedin.com/in/parisa-kavianpour/) · [GitHub](https://github.com/parisa-kavian)
