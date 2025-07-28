# bias-audit-toxic-language
Using Explainable AI to detect and understand bias in toxicity classifiers



# 🔍 Bias Audit of Toxic Language Classifiers using Explainable AI

**Can AI be fair if we don’t understand its decisions?**  
This project investigates the **hidden social biases** in machine learning models designed to detect toxic or hateful language. We combine **text classification**, **explainability tools (LIME)**, and **statistical fairness analysis** to reveal how identity-based terms (like race or gendered names) influence model outputs — even in neutral contexts.

---

## 🎯 Project Objectives

- 🧠 Train a custom toxicity classifier on real-world Twitter data  
- 🧪 Audit the model for **racial and gender bias** using identity-swapped sentence templates  
- 🔍 Use **LIME (Local Interpretable Model-Agnostic Explanations)** to understand *why* specific predictions are made  
- 📊 Compare model behaviour across identity groups using **visualisation** and **statistical testing**  
- 🔄 Benchmark our model’s behaviour against **Google’s Perspective API** — a widely used, production-grade API for toxicity detection  
- ✍️ Reflect on the findings to demonstrate the power of explainable AI in **uncovering fairness issues** beyond just metrics

---

## 🧪 Key Methods Used

### 1. **Custom Model Training**
We trained a logistic regression classifier on the [Kaggle Hate Speech and Offensive Language Dataset](https://www.kaggle.com/datasets/mrmorj/hate-speech-and-offensive-language-dataset). The model classifies tweets as **Toxic** or **Non-Toxic**.

### 2. **Explainable AI (LIME)**
LIME helps us see **which words** in a sentence influenced the model’s decision. This is critical for identifying hidden bias. For instance:
> `"Jamal is loud"` was marked more toxic than `"David is loud"` — LIME revealed the name “Jamal” was contributing to the toxicity score.

### 3. **Identity-Based Bias Testing**
We created 100–200 test sentences using templates like:
- “_Name_ is aggressive.”
- “_Name_ is loud.”
- “_Group_ people are annoying.”

We systematically swapped **racial**, **gender**, and **religious** identity terms to observe changes in toxicity predictions.

### 4. **Statistical Analysis**
We grouped predictions by identity group (e.g., White, Black, Arabic, Asian) and:
- Calculated mean toxicity scores  
- Measured variance within each group  
- Ran **ANOVA tests** to detect statistically significant differences  

### 5. **Perspective API Comparison**
We ran the same test sentences through Google’s **Perspective API** to benchmark our model.

#### 🧩 Key Finding:
- Perspective API gave consistently high/low scores with **little variation between identities**
- Our model, by contrast, **showed more individual bias cases**, where certain names or terms triggered unexpectedly high toxicity
- **LIME helped us catch these subtleties** — making explainability essential for real bias detection

---

## 📊 Sample Results

| Sentence | Model Toxicity | Perspective API Toxicity |
|----------|----------------|---------------------------|
| Jamal is loud | 0.70 | 0.30 |
| David is loud | 0.58 | 0.30 |
| Ahmed is annoying | 0.75 | 0.32 |
| Michael is annoying | 0.59 | 0.32 |

Even when **Perspective API scores were flat**, our model's responses varied — and **LIME** showed *why*. It’s this interpretability that enabled true auditing.

---

## 💡 Why This Matters

Without LIME, we would have **missed these biases**.

Your average score might look fair — but:
- ⚠️ **Are certain names or groups unfairly penalised?**
- ⚠️ **Are toxic labels triggered by identity alone?**
- ⚠️ **Can a “fair” model still make harmful individual decisions?**

🧠 Explainable AI gives us the tools to **ask and answer these questions.**

---

## 🧾 Project Structure

bias-audit-toxic-language/
├── data/
│ ├── labeled_data.csv # Original Kaggle dataset
│ └── test_templates.csv # Custom test sentences
├── notebooks/
│ └── bias_analysis.ipynb # Full analysis notebook
├── results/
│ ├── group_scores.png # Bar chart of average toxicity by group
│ └── lime_explanations/ # Visual LIME outputs
├── requirements.txt # Python dependencies
├── README.md # This file


---

## 📦 Requirements

Install dependencies with:

pip install -r requirements.txt

🔧 Tech Stack
Python (scikit-learn, pandas, matplotlib)

LIME

Google Colab

Google Perspective API

Statistical tests (ANOVA, variance)

Explainable AI



✍️ Author & Credits
Created by Purvi Jain
Part of the AI Ethics Explorer initiative
🔗 https://purvi9399.github.io/

