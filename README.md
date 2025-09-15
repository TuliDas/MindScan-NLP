# MindScan: Multi-class Mental Health Detection from Social Media

🚧 **Work in Progress** — This repository is under active development.  

## Overview
This project explores **multi-class mental health detection** from social media (Reddit) posts.  
The goal is to classify user posts into mental health categories such as:
- Anxiety
- Depression
- OCD
- PTSD
- ADHD
- Addiction
- Suicidal
- Normal

## Methods
The project will compare several modeling approaches:
1. **Baseline**: Logistic Regression (TF-IDF) — simple, interpretable
2. **Classical ML**: SVM, Random Forest
3. **Neural Model**: BiLSTM with pretrained embeddings
4. **Transformer**: DistilBERT / BERT-base fine-tuning

Evaluation will include **accuracy, precision, recall, F1-score**, and **explainability** with tools like **LIME/SHAP**.

## Data
- Data is collected from **public Reddit posts** across mental-health related subreddits.  
- Posts are preprocessed with length filters, English-only check, and deduplication.  
- *⚠️ Sample data is included for demonstration purpose, but post IDs and personal info are removed for privacy.*

## Roadmap
- [x] **Data collection**
- [ ] Cleaning & EDA
- [ ] Baseline ML experiments  
- [ ] Neural sequence modeling (BiLSTM)  
- [ ] Transformer fine-tuning (BERT/DistilBERT)  
- [ ] Explainability (LIME/SHAP)  
- [ ] Final evaluation & comparison  

## Disclaimer
This project is for **research and educational purposes only**.  
It is **not intended for clinical or diagnostic use**.
---

