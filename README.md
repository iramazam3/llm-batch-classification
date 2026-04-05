# Batch Classification of Text Data for Personal Health Experience Identification with LLM Batch Prompting

## 📌 Overview

This project presents a scalable approach for classifying large volumes of social media data using **batch prompting with Large Language Models (LLMs)**. Instead of processing one instance at a time, the system classifies multiple text inputs in a single prompt, significantly improving efficiency while maintaining strong classification performance.

The task focuses on identifying **Personal Health Experience (PHE)** tweets, a critical step for public health monitoring and downstream biomedical analysis.

---

## 🎯 Objectives

* Classify tweets into:

  * **PHE (Personal Health Experience)**
  * **Non-PHE**
* Improve scalability using **batch prompting**
* Analyze trade-offs between:

  * Accuracy & F1 score
  * Throughput & latency
  * Cost efficiency

---

## 📂 Dataset

* **12,331 annotated tweets** related to medications

* Collected from real-world social media data

* Labels:

  * 2,962 PHE tweets
  * 9,369 Non-PHE tweets

* Preprocessing:

  * Removed URLs
  * Replaced medication names with `*MEDICINE*`
  * Standardized input for consistent LLM behavior

📌 Dataset referenced from prior work 

---

## 🚀 Features

* Batch classification using LLMs (instead of single-instance inference)
* Supports multiple models:

  * Gemini 2.0 Flash
  * Gemini 2.5 Flash
  * GPT-4o
  * GPT-4o Mini
* Optimized prompt design for structured outputs
* Evaluation across multiple batch sizes (1 → 1000)
* Cost analysis for real-world deployment

---

## 🧠 Methodology

### Pipeline

1. **Input Data**

   * Tweet corpus (12,331 instances)

2. **Preprocessing**

   * Clean text
   * Normalize medication mentions

3. **Batch Prompting**

   * Group tweets into batches
   * Send batch to LLM in a single prompt

4. **LLM Classification**

   * Output structured predictions (Yes/No)

5. **Evaluation**

   * Accuracy, F1 score
   * Throughput (instances/sec)
   * Latency (time per instance)

---

## ⚙️ Key Concept: Batch Classification

Instead of:

* 1 prompt → 1 tweet

We use:

* 1 prompt → N tweets

This improves:

* Efficiency
* Cost
* Scalability

---

## 📊 Results

### 🔹 Model Performance at Optimal Batch Sizes

| Model            | Batch Size | Accuracy  | F1 Score  |
| ---------------- | ---------- | --------- | --------- |
| Baseline (LSTM)  | —          | 0.815     | 0.645     |
| Gemini 2.0 Flash | 150        | 0.814     | 0.674     |
| Gemini 2.5 Flash | 150        | 0.808     | 0.676     |
| **GPT-4o**       | **50**     | **0.843** | **0.703** |
| GPT-4o Mini      | 100        | 0.799     | 0.662     |

👉 GPT-4o achieved the best classification performance.

---

### ⚡ Efficiency (Throughput & Latency)

* Gemini 2.0 Flash:

  * Highest throughput (~23.7 instances/sec)
  * Lowest latency (~3.47 sec)

* GPT-4o:

  * Strong balance between performance and efficiency

---

### 💰 Cost Analysis

| Model            | Cost ($)             |
| ---------------- | -------------------- |
| Gemini 2.0 Flash | **0.005** (cheapest) |
| Gemini 2.5 Flash | 0.271                |
| GPT-4o           | 0.366                |
| GPT-4o Mini      | 0.023                |

👉 Gemini 2.0 Flash is the most cost-efficient
👉 GPT-4o is the most accurate

---

## 📈 Key Insights

* Batch prompting maintains **comparable accuracy** to single-instance classification
* Different models have **different optimal batch sizes**
* Efficiency gains are substantial for large datasets
* Trade-off exists between:

  * Performance (GPT-4o)
  * Cost & speed (Gemini 2.0 Flash)

---

## 🛠 Tech Stack

* Python
* LLM APIs (OpenAI, Gemini)
* Google Colab
* Pandas, NumPy

---

## ▶️ How to Run

```bash
git clone https://github.com/iramazam3/llm-batch-classification
cd llm-batch-classification

pip install -r requirements.txt
python main.py
```

---

## 📷 Example

Input (batch of tweets):

* "I feel dizzy after taking this medicine"
* "What is the dosage for this drug?"

Output:

* Yes
* No

---

## 📚 Citation

If you use this work, please cite:

> Jiang, K., Azam, I., & Bernard, G. B. (2025, December). Batch Classification of Text Data for Personal Health Experience Identification with LLM Batch Prompting. In 2025 IEEE International Conference on Big Data (BigData) (pp. 7971-7978). IEEE.

---

## 👤 Author

Iram Azam

Purdue University
