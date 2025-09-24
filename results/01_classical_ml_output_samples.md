# Classical ML Model Performance Analysis

The experiments covered classical ML with TF-IDF, Word2Vec embeddings, and BERT embeddings, each trained with Logistic Regression and SVM.

---

## Example Predictions

### Example 1 (True Label = Depression ; src = ChatGPT)  
**Input Post:**  
*"Lately I feel empty, nothing excites me anymore. Even simple things like eating or talking to friends feel like a burden. I just want to sleep all day and avoid facing the world."*

| **Model** | **Prediction** | **Confidence** | **Notes** |
|-----------|----------------|----------------|------------|
| LogReg / TF-IDF | **Depression** | 0.494 | Top tokens: feel, anymore, lately, burden |
| SVM / TF-IDF | **Depression** | 0.615 | Top tokens: lately, feel, anymore, burden |
| LogReg / Word2Vec | **Depression** | 0.325 | — |
| LogReg / BERT | **Depression** | 0.996 | Very confident |

---

### Example 2 (True Label = PTSD ; src = HuggingFace)  
**Input Post:**  
*"I had some violent flashbacks and brutal compulsive images last night and I know I shouldn’t cut but it’s the only thing that gives me some sense of control right now. I’m losing everyone and everything because of what happened to me when I was younger..."*

| **Model** | **Prediction** | **Confidence** | **Notes** |
|-----------|----------------|----------------|------------|
| LogReg / TF-IDF | **PTSD** | 0.498 | Top tokens: trauma, happen, control, violent |
| SVM / TF-IDF | **PTSD** | 0.629 | Top tokens: trauma, happen, control, night |
| LogReg / Word2Vec | **PTSD** | 0.568 | — |
| LogReg / BERT | ❌ **Suicidal** | 0.975 | Misclassified |

---

### Example 3 (True Label = Suicidal)  
**Input Post:**  
*"I don’t think my life is worthy anymore. Failure, heartbreak, parent’s death have destroyed me completely. Why would I live? Maybe today is my last day, and it’s my last post ... have a good life fellas."*

| **Model** | **Prediction** | **Confidence** | **Notes** |
|-----------|----------------|----------------|------------|
| LogReg / TF-IDF | **Suicidal** | 0.528 | Top tokens: life, death, live, anymore |
| SVM / TF-IDF | **Suicidal** | 0.592 | Top tokens: death, life, think life, heartbreak |
| LogReg / Word2Vec | **Suicidal** | 0.586 | — |
| LogReg / BERT | **Suicidal** | 0.965 | Very confident |

---

### Example 4 (True Label = Depression)  
**Input Post:**  
*"I don’t know what I will do in the future. I feel like I’ve wasted three years of my life. That relationship was a curse. Most of my friends have almost completed their PhDs, and here I am, just working on simple ML and NLP projects..."*

| **Model** | **Prediction** | **Confidence** | **Notes** |
|-----------|----------------|----------------|------------|
| LogReg / TF-IDF | **Depression** | 0.297 | Top tokens: life, know, feel, relationship |
| SVM / TF-IDF | **Depression** | 0.276 | Top tokens: life, relationship, feel |
| LogReg / Word2Vec | ❌ **ADHD** | 0.249 | Misclassified |
| LogReg / BERT | ❌ **Suicidal** | 0.836 | Misclassified |

---

### Example 5 (True Label = Anxiety)  
**Input Post:**  
*"I keep replaying small conversations in my head, wondering if I sounded rude or stupid 🤦‍♀️. Hours later my chest feels tight 💔 just remembering how I said ‘hi’ wrong or didn’t smile enough..."*

| **Model** | **Prediction** | **Confidence** | **Notes** |
|-----------|----------------|----------------|------------|
| LogReg / TF-IDF | **Anxiety** | 0.344 | Top tokens: chest, people, avoid, wrong |
| SVM / TF-IDF | **Anxiety** | 0.394 | Top tokens: chest, rude, people, avoid |
| LogReg / Word2Vec | ❌ **Normal** | 0.418 | Misclassified |
| LogReg / BERT | ❌ **Depression** | 0.405 | Misclassified |

---

## Classification Reports

- **Logistic Regression + TF-IDF:** Accuracy = **0.771**  
- **SVM + TF-IDF:** Accuracy = **0.772**  
- **Logistic Regression + Word2Vec:** Accuracy = **0.659**  
- **Logistic Regression + BERT Embeddings:** Accuracy = **0.685**

---

## Key Insights

1. **TF-IDF + Classical ML performed best** for this dataset because:  
   - Posts are long (230–310 chars on average).  
   - Rare tokens and negations carry strong discriminative power.  
   - Sparse features aligned well with linear classifiers.  

2. **Embeddings underperformed** (Word2Vec & BERT mean pooling) because:  
   - Averaging compresses long posts, diluting rare but important features.  
   - Semantic closeness does not always map directly to diagnostic categories.  

