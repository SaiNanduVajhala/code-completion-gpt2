# code-completion-gpt2
# GPT-2 Code Completion using CodeXGLUE

## Overview

This project focuses on fine-tuning GPT-2 for source code completion using the CodeXGLUE Code Completion dataset. The objective is to train a transformer-based language model capable of predicting and generating the next sequence of code tokens given a partial code snippet.

The project explores the complete machine learning workflow, including data preprocessing, tokenization, model fine-tuning, evaluation, and inference using Hugging Face Transformers and PyTorch.

---

## Project Objectives

* Fine-tune GPT-2 for code completion tasks.
* Learn transformer-based causal language modeling.
* Build an end-to-end training and evaluation pipeline.
* Optimize training under GPU memory constraints.
* Evaluate model performance using validation loss and perplexity.

---

## Dataset

### CodeXGLUE Code Completion Dataset

The model was trained using the CodeXGLUE Code Completion benchmark dataset, which contains real-world source code samples designed for code generation and completion tasks.

Dataset Features:

* Programming language: Python
* Task: Next-token / next-line code prediction
* Training subset used: ~13,000 samples
* Validation split: 10%

The dataset was tokenized using the GPT-2 tokenizer and processed for causal language modeling.

---

## Model Architecture

### GPT-2

GPT-2 is an autoregressive transformer model that predicts the next token in a sequence based on previously observed tokens.

Model Configuration:

* Base Model: GPT-2
* Transformer Architecture
* Causal Language Modeling Objective
* Maximum Sequence Length: 512 tokens

---

## Technologies Used

* Python
* PyTorch
* Hugging Face Transformers
* Hugging Face Datasets
* GPT-2
* CodeXGLUE
* Kaggle GPU Environment

---

## Training Configuration

### Hyperparameters

| Parameter                   | Value |
| --------------------------- | ----- |
| Learning Rate               | 2e-4  |
| Batch Size                  | 4     |
| Epochs                      | 3     |
| Sequence Length             | 512   |
| Weight Decay                | 0.01  |
| Gradient Accumulation Steps | 4     |
| Optimizer                   | AdamW |

### Training Optimizations

To efficiently train the model within GPU memory limitations:

* Mixed Precision Training (FP16)
* Gradient Checkpointing
* Gradient Accumulation
* Multi-GPU Training
* Memory-efficient Evaluation Pipeline

---

## Challenges Encountered

During development, several engineering challenges were addressed:

### CUDA Out-of-Memory Errors

Initial training runs encountered GPU memory limitations during evaluation.

Solutions:

* Reduced evaluation batch size
* Enabled mixed precision training (FP16)
* Optimized validation workflow
* Implemented gradient checkpointing

### Training Stability

While experimenting with layer freezing and selective fine-tuning, training failures occurred due to zero trainable parameters after switching model variants.

Solutions:

* Verified trainable parameter counts
* Corrected layer unfreezing logic
* Validated optimizer configuration

### Evaluation Optimization

Large validation logits caused memory accumulation issues during evaluation.

Solutions:

* Switched to loss-only evaluation
* Reduced evaluation memory footprint
* Optimized validation scheduling

---

## Results

### Final Evaluation Metrics

| Metric          | Value  |
| --------------- | ------ |
| Validation Loss | 1.1869 |
| Perplexity      | 3.28   |
| Training Epochs | 3      |

### Validation Loss Progression

| Step  | Validation Loss |
| ----- | --------------- |
| 100   | 1.3592          |
| 200   | 1.2877          |
| 300   | 1.2537          |
| 400   | 1.2308          |
| 500   | 1.2142          |
| 600   | 1.2000          |
| Final | 1.1869          |

The model demonstrated consistent convergence throughout training with no significant signs of overfitting.

---

## Sample Inference

Example prompt:

```python
def binary_search(arr, target):
```

Example generation:

```python
def binary_search(arr, target):
    left = 0
    right = len(arr) - 1

    while left <= right:
        mid = (left + right) // 2

        if arr[mid] == target:
            return mid
```

*(Generated output may vary depending on sampling parameters.)*

---

## Key Learnings

Through this project, the following concepts were explored and implemented:

* Transformer architectures
* GPT-2 fine-tuning
* Causal Language Modeling
* Tokenization pipelines
* Model evaluation using perplexity
* GPU memory optimization
* Mixed precision training
* Hugging Face ecosystem
* Large-scale model debugging

---

## Future Improvements

Potential enhancements include:

* Training on the complete CodeXGLUE dataset
* Experimenting with larger GPT-2 variants
* Parameter-efficient fine-tuning (LoRA / QLoRA)
* Integration with code editors for real-time completion
* Benchmarking against CodeGPT and CodeGen models
* Deployment using Hugging Face Spaces

---

## Repository Structure

```text
├── code-completion-gpt2.ipynb
├── README.md
└── outputs/
```

---

## Author

Sai Nandu Vajhala

AI/ML Undergraduate | Python Developer | Machine Learning Enthusiast

Focused on building AI applications, language models, data-driven systems, and practical machine learning solutions.
