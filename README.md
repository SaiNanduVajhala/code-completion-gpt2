# GPT-2 Code Completion using CodeXGLUE

Fine-tuning GPT-2 for Python source code completion using the CodeXGLUE dataset with the Hugging Face Transformers ecosystem.

---

## Project Highlights

- Fine-tuned GPT-2 for Python code completion
- Trained on approximately 13,000 CodeXGLUE samples
- Achieved Validation Loss: **1.1869**
- Final Perplexity: **3.28**
- Built using PyTorch and Hugging Face Transformers
- Optimized training with FP16 mixed precision and gradient checkpointing
- Implemented an end-to-end pipeline including preprocessing, training, evaluation, and inference

---

## Overview

This project focuses on fine-tuning GPT-2 for source code completion using the CodeXGLUE Code Completion dataset. The objective is to train a transformer-based language model capable of predicting and generating the next sequence of code tokens given a partial code snippet.

The project explores the complete machine learning workflow, including:

- Data preprocessing
- Tokenization
- Model fine-tuning
- Evaluation
- Inference

The implementation was built using Hugging Face Transformers and PyTorch in a Kaggle GPU environment.

---

## Project Objectives

- Fine-tune GPT-2 for code completion tasks.
- Learn transformer-based causal language modeling.
- Build an end-to-end training and evaluation pipeline.
- Optimize training under GPU memory constraints.
- Evaluate model performance using validation loss and perplexity.

---

## Dataset

### CodeXGLUE Code Completion Dataset

The model was trained using the CodeXGLUE Code Completion benchmark dataset, which contains real-world source code samples designed for code generation and completion tasks.

### Dataset Features

- Programming Language: Python
- Task: Next-token / next-line code prediction
- Training Samples Used: ~13,000
- Validation Split: 10%

The dataset was tokenized using the GPT-2 tokenizer and prepared for causal language modeling.

---

## Model Architecture

### GPT-2

GPT-2 is an autoregressive transformer model that predicts the next token in a sequence based on previously observed tokens.

### Model Configuration

| Parameter | Value |
|-----------|--------|
| Base Model | GPT-2 |
| Architecture | Transformer |
| Learning Task | Causal Language Modeling |
| Maximum Sequence Length | 512 Tokens |

---

## Technologies Used

- Python
- PyTorch
- Hugging Face Transformers
- Hugging Face Datasets
- GPT-2
- CodeXGLUE
- Kaggle GPU Environment

---

## Training Configuration

### Hyperparameters

| Parameter | Value |
|------------|---------|
| Learning Rate | 2e-4 |
| Batch Size | 4 |
| Epochs | 3 |
| Sequence Length | 512 |
| Weight Decay | 0.01 |
| Gradient Accumulation Steps | 4 |
| Optimizer | AdamW |

### Training Optimizations

To efficiently train the model within GPU memory limitations, the following techniques were implemented:

- Mixed Precision Training (FP16)
- Gradient Checkpointing
- Gradient Accumulation
- GPU-Accelerated Training
- Memory-efficient Evaluation Pipeline

---

## Engineering Challenges

### CUDA Out-of-Memory Errors

Initial training runs encountered GPU memory limitations during evaluation.

#### Solutions

- Reduced evaluation batch size
- Enabled mixed precision training (FP16)
- Optimized validation workflow
- Implemented gradient checkpointing

---

### Memory Optimization

Training large transformer models under GPU memory constraints required several optimizations.

#### Techniques Used

- Enabled Gradient Checkpointing to reduce memory consumption.
- Used Mixed Precision Training (FP16).
- Applied Gradient Accumulation to simulate larger batch sizes.
- Reduced evaluation batch size to avoid CUDA out-of-memory errors.

---

### Evaluation Optimization

Large validation logits caused memory accumulation issues during evaluation.

#### Solutions

- Switched to loss-only evaluation
- Reduced evaluation memory footprint
- Optimized validation scheduling

---

## Results

### Final Evaluation Metrics

| Metric | Value |
|----------|----------|
| Validation Loss | **1.1869** |
| Perplexity | **3.28** |
| Training Epochs | 3 |

### Validation Loss Progression

| Step | Validation Loss |
|------|-----------------|
| 100 | 1.3592 |
| 200 | 1.2877 |
| 300 | 1.2537 |
| 400 | 1.2308 |
| 500 | 1.2142 |
| 600 | 1.2000 |
| Final | **1.1869** |

The model demonstrated stable convergence throughout training with no significant signs of overfitting.

---

## Sample Inference

### Input

```python
def binary_search(arr, target):
```

### Generated Output

```python
def binary_search(arr, target):
    left = 0
    right = len(arr) - 1

    while left <= right:
        mid = (left + right) // 2

        if arr[mid] == target:
            return mid
```

*Generated output may vary depending on decoding parameters.*

---

## Key Learnings

This project provided practical experience with:

- Transformer Architectures
- GPT-2 Fine-Tuning
- Causal Language Modeling
- Tokenization Pipelines
- Model Evaluation using Perplexity
- GPU Memory Optimization
- Mixed Precision Training
- Hugging Face Ecosystem
- Large-Scale Model Debugging

---

## Future Improvements

Potential future enhancements include:

- Training on the complete CodeXGLUE dataset
- Experimenting with larger GPT-2 variants
- Parameter-Efficient Fine-Tuning (LoRA / QLoRA)
- Integration with code editors for real-time completion
- Benchmarking against CodeGPT and CodeGen models
- Deployment using Hugging Face Spaces

---

## Installation

Clone the repository:

```bash
git clone https://github.com/SaiNanduVajhala/code-completion-gpt2.git
cd code-completion-gpt2
```

Install dependencies:

```bash
pip install torch transformers datasets accelerate evaluate pandas numpy scikit-learn
```

---

## Running the Project

Open the notebook:

```
code-completion-gpt2.ipynb
```

Execute the notebook cells sequentially to:

1. Load and preprocess the dataset
2. Tokenize the input data
3. Fine-tune GPT-2
4. Evaluate model performance
5. Generate code completions

---

## Model Checkpoint

The trained model weights are not included in this repository due to GitHub file size limitations. This repository focuses on the complete training, evaluation, and inference pipeline.

---

## Repository Structure

```text
code-completion-gpt2/
│
├── LICENSE
├── README.md
├── code-completion-gpt2.ipynb
└── outputs/          # Generated during training
```

---

## Author

**Sai Nandu Vajhala**

AI/ML Undergraduate | Python Developer | Machine Learning Enthusiast

Interested in building practical AI applications, language models, data-driven systems, and scalable machine learning solutions.

- GitHub: https://github.com/SaiNanduVajhala/code-completion-gpt2
- Kaggle: https://www.kaggle.com/code/vajhalasainandu/code-completion-gpt2

---

## License

This project is licensed under the Apache 2.0 License.
