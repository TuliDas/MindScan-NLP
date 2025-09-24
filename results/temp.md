# Model Performance Analysis

This project compared multiple feature representations and classifiers for the task of **mental health text classification**.  
The experiments covered classical ML with TF-IDF, Word2Vec embeddings, and BERT embeddings, each trained with Logistic Regression and SVM.

---

## Example Predictions

### Example 1 (Label = Depression ; src = ChatGPT)
Input:  
*"Lately I feel empty, nothing excites me anymore. Even simple things like eating or talking to friends feel like a burden. I just want to sleep all day and avoid facing the world."*

- LogReg/TfIdf →
  Predicted Class: Depression
  Confidence Score: **0.494** 
  -----All class probabilities:-----
  ADHD: 0.040 | Addiction: 0.043 | Anxiety: 0.064 | Depression: 0.494 | Normal: 0.054 | OCD: 0.084 | PTSD: 0.147 | Suicidal: 0.073

  Top supporting tokens:
  feel: 0.55 ; anymore: 0.518 ; lately: 0.277 ; want: 0.238 ; burden: 0.203 ; sleep: 0.126  

- SVM/Tf-Idf → Confidence: **0.615**
  Predicted Class: Depression
Confidence Score: 0.615

-----All class probabilities:-----
ADHD: 0.006
Addiction: 0.015
Anxiety: 0.028
Depression: 0.615
Normal: 0.054
OCD: 0.085
PTSD: 0.168
Suicidal: 0.028

Top supporting tokens:
lately: 0.258
feel: 0.236
anymore: 0.212
burden: 0.142
eating: 0.135
sleep day: 0.103
  
- LogReg/Word2Vec → Confidence: **0.325**
  Predicted Class: Depression
Confidence Score: 0.325

-----All class probabilities:-----
ADHD: 0.119
Addiction: 0.119
Anxiety: 0.073
Depression: 0.325
Normal: 0.094
OCD: 0.079
PTSD: 0.125
Suicidal: 0.067

- LogReg/BERT → Confidence: **0.996**
  Predicted Class: Depression
Confidence Score: 0.996

-----All class probabilities:-----
ADHD: 0.000
Addiction: 0.000
Anxiety: 0.001
Depression: 0.996
Normal: 0.001
OCD: 0.000
PTSD: 0.000
Suicidal: 0.003

---

### Example 2 (Label = PTSD ; src = HuggingFace)
Input:  
*"I had some violent flashbacks and brutal compulsive images last night and I know I shouldn’t cut but it’s the only thing that gives me some sense of control right now. I’m losing everyone and everything because of what happened to me when I was younger and what I continue to allowed to happen to me as I got older. I’ve dumped all my trauma on the only person who has loved me unconditionally and now I may lose him too. Fuck what happened to me."*

- LogReg/TfIdf → 
  Predicted Class: PTSD
Confidence Score: 0.498

-----All class probabilities:-----
ADHD: 0.037 , Addiction: 0.062 , Anxiety: 0.034 , Depression: 0.106 , Normal: 0.024 , OCD: 0.057 , **PTSD: 0.498** , Suicidal: 0.182

Top supporting tokens:
trauma: 1.743 , happen: 0.419 , control: 0.155 , violent: 0.148

- SVM/Tf-Idf → Confidence: **0.629**
Predicted Class: PTSD
Confidence Score: 0.629

-----All class probabilities:-----
ADHD: 0.005
Addiction: 0.043
Anxiety: 0.015
Depression: 0.116
Normal: 0.001
OCD: 0.009
PTSD: 0.629
Suicidal: 0.182

Top supporting tokens:
trauma: 0.901
happen: 0.163
control: 0.108
night: 0.08
  
- LogReg/Word2Vec → Confidence: **0.568**
  Predicted Class: PTSD
Confidence Score: 0.568

-----All class probabilities:-----
ADHD: 0.036
Addiction: 0.020
Anxiety: 0.040
Depression: 0.045
Normal: 0.095
OCD: 0.141
PTSD: 0.568
Suicidal: 0.055 
- LogReg/BERT → Confidence: **0.975** (Predicted *Suicidal*)
  Predicted Class: Suicidal
Confidence Score: 0.975

-----All class probabilities:-----
ADHD: 0.000
Addiction: 0.000
Anxiety: 0.000
Depression: 0.008
Normal: 0.000
OCD: 0.000
PTSD: 0.017
Suicidal: 0.975

---

### Example 3 (Label = Suicidal)
Input:  
*"I don’t think my life is worthy anymore. Failure, heartbreak, parent’s death have destroyed me completely. Why would I live? Maybe today is my last day, and it’s my last post ... have a good life fellas."*

- LogReg/TfIdf →
  Predicted Class: Suicidal
Confidence Score: 0.528

-----All class probabilities:-----
ADHD: 0.013
Addiction: 0.103
Anxiety: 0.020
Depression: 0.266
Normal: 0.037
OCD: 0.015
PTSD: 0.019
Suicidal: 0.528

Top supporting tokens:
life: 0.855
death: 0.795
live: 0.382
anymore: 0.237
parent: 0.221
think life: 0.184
 
  
- SVM/Tf-Idf → Confidence: **0.592**
  Predicted Class: Suicidal
Confidence Score: 0.592

-----All class probabilities:-----
ADHD: 0.002
Addiction: 0.037
Anxiety: 0.006
Depression: 0.348
Normal: 0.004
OCD: 0.002
PTSD: 0.008
Suicidal: 0.592

Top supporting tokens:
death: 0.395
life: 0.308
think life: 0.278
live: 0.167
heartbreak: 0.121
- LogReg/Word2Vec → Confidence: **0.586**
  Predicted Class: Suicidal
Confidence Score: 0.586

-----All class probabilities:-----
ADHD: 0.003
Addiction: 0.146
Anxiety: 0.033
Depression: 0.149
Normal: 0.047
OCD: 0.017
PTSD: 0.019
Suicidal: 0.586
- LogReg/BERT → Confidence: **0.965**
  Predicted Class: Suicidal
Confidence Score: 0.965

-----All class probabilities:-----
ADHD: 0.000
Addiction: 0.000
Anxiety: 0.000
Depression: 0.035
Normal: 0.000
OCD: 0.000
PTSD: 0.000
Suicidal: 0.965

---

### Example 4 (Label = Depression)
Input:  
*"I don’t know what I will do in the future. I feel like I’ve wasted three years of my life. That relationship was a curse. Most of my friends have almost completed their PhDs, and here I am, just working on simple ML and NLP projects. Sometimes I wonder how things turned out this way. I never thought I would struggle so much with my academic life, especially since I was always the top girl in school and college. Life has changed so drastically. I don’t even know how I can ever catch up with my friends in the academic field."*

- LogReg/TfIdf → Confidence: **0.297**
Predicted Class: Depression
Confidence Score: 0.297

-----All class probabilities:-----
ADHD: 0.113
Addiction: 0.045
Anxiety: 0.099
Depression: 0.297
Normal: 0.133
OCD: 0.124
PTSD: 0.059
Suicidal: 0.129

Top supporting tokens:
life: 0.394
know: 0.192
feel: 0.174
college: 0.165
relationship: 0.134
   
- SVM/Tf-Idf → 
  Predicted Class: Depression
Confidence Score: 0.276

-----All class probabilities:-----
ADHD: 0.169
Addiction: 0.031
Anxiety: 0.167
Depression: 0.276
Normal: 0.130
OCD: 0.105
PTSD: 0.014
Suicidal: 0.109

Top supporting tokens:
life: 0.124
relationship: 0.077
feel: 0.075
school: 0.062
girl: 0.05  
- LogReg/Word2Vec → Confidence: **0.249** (Predicted *ADHD*)
  Predicted Class: ADHD
Confidence Score: 0.249

-----All class probabilities:-----
ADHD: 0.249
Addiction: 0.041
Anxiety: 0.059
Depression: 0.126
Normal: 0.246
OCD: 0.120
PTSD: 0.123
Suicidal: 0.035  
- LogReg/BERT → Confidence: **0.836** (Predicted *Suicidal*)
  Predicted Class: Suicidal
Confidence Score: 0.836

-----All class probabilities:-----
ADHD: 0.000
Addiction: 0.000
Anxiety: 0.007
Depression: 0.125
Normal: 0.020
OCD: 0.002
PTSD: 0.010
Suicidal: 0.836

---

### Example 5 (Label = Anxiety)
Input:  
*"I keep replaying small conversations in my head, wondering if I sounded rude or stupid 🤦‍♀️. Hours later my chest feels tight 💔 just remembering how I said ‘hi’ wrong or didn’t smile enough. People probably don’t even notice, but my mind won’t stop. I cancel plans often because it feels safer to avoid messing up again 😞."*

- LogReg/TfIdf → Confidence: **0.344**
  Predicted Class: Anxiety
Confidence Score: 0.344

-----All class probabilities:-----
ADHD: 0.047
Addiction: 0.061
Anxiety: 0.344
Depression: 0.066
Normal: 0.241
OCD: 0.167
PTSD: 0.042
Suicidal: 0.032

Top supporting tokens:
chest: 0.447
people: 0.276
probably: 0.226
avoid: 0.138
wrong: 0.128
rude: 0.126
  
- SVM/Tf-Idf →
  Predicted Class: Anxiety
Confidence Score: 0.394

-----All class probabilities:-----
ADHD: 0.010
Addiction: 0.039
Anxiety: 0.394
Depression: 0.065
Normal: 0.262
OCD: 0.218
PTSD: 0.005
Suicidal: 0.007

Top supporting tokens:
chest: 0.256
rude: 0.141
probably: 0.136
people: 0.098
avoid: 0.096
smile: 0.076  

- LogReg/Word2Vec → Confidence: **0.418** (Predicted *Normal*)
Predicted Class: Normal
Confidence Score: 0.418

-----All class probabilities:-----
ADHD: 0.067
Addiction: 0.030
Anxiety: 0.203
Depression: 0.025
Normal: 0.418
OCD: 0.166
PTSD: 0.032
Suicidal: 0.059
  
- LogReg/BERT → Confidence: **0.405** (Predicted *Depression*)
  Predicted Class: Depression
Confidence Score: 0.405

-----All class probabilities:-----
ADHD: 0.000
Addiction: 0.000
Anxiety: 0.022
Depression: 0.405
Normal: 0.009
OCD: 0.000
PTSD: 0.349
Suicidal: 0.215 

---

## Classification Reports

### Logistic Regression + TF-IDF
- **Accuracy:** 0.771  
- Strongest performance among all tested models.  
- Preserves discriminative tokens effectively due to sparse vectorization.  

---

### SVM + TF-IDF
- **Accuracy:** 0.772  
- Similar to Logistic Regression but slightly more stable.  

---

### Logistic Regression + Word2Vec
- **Accuracy:** 0.659  
- Lower than TF-IDF due to information loss in mean-pooled embeddings.  
- Works better for short texts but weak on longer posts (average 230–310 characters).  

---

### Logistic Regression + BERT Embeddings
- **Accuracy:** 0.685  
- Performed better than Word2Vec but still below TF-IDF.  
- BERT embeddings are powerful but mean pooling dilutes key signals in long posts.  
- Some misclassifications show that embeddings capture semantics but lose label-specific cues.  

---

## Key Insights

1. **TF-IDF + Classical ML performed best** for this dataset because:  
   - Posts are long (230–310 chars on average).  
   - Rare tokens and negations carry strong discriminative power.  
   - Sparse features aligned well with linear classifiers.  

2. **Embeddings underperformed** (Word2Vec & BERT mean pooling) because:  
   - Averaging compresses long posts, diluting rare but important features.  
   - Semantic closeness does not always map directly to diagnostic categories.  
---

## Conclusion

- **Best Performing Models:** Logistic Regression and SVM with TF-IDF (~77% accuracy).  
- **Embeddings with Logistic Regression:** Showed weaker performance due to dataset characteristics.  
- **Lesson Learned:** Model performance depends not only on architecture but also on feature representation and dataset nature.  
