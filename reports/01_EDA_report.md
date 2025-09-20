# Exploratory Data Analysis (EDA)

This report presents the exploratory analysis performed on the dataset to understand its structure, distribution, and linguistic characteristics.  

---

## 1. Dataset Structure & Quality
- Dataset shape : (15913 rows, 2 columns)
- Check for missing values : None detected 
The dataset is clean, balanced in terms of structure, and ready for further analysis.
---

## 2. Label Analysis
- Total count of posts per label  
- Barplot: Number of posts per class  
- Percentage distribution of labels  

---

## 3. Text Characteristics
- Distribution of number of words per post (histplot)  
- Number of words per class (boxplot)  
- Average text length per class  

---

## 4. Word-Level Analysis

### 4.1 Initial Word Analysis
- Word clouds for each class  
- Top N most frequent words per class  

### 4.2 After Removing Common Words
- Cleaned word clouds for each class  
- Updated Top N most frequent words per class  

---

## 5. Lexical Diversity
- Mean lexical diversity (unique word ratio) per class  
- Comparison between `df_cleaned_ml` and `df_cleaned_bert` datasets  
- Barplot of lexical diversity scores  

---

## 6. Statistical Distinctive Keywords (Chi-Square)
- Top 10 statistically distinctive words per class (barplots)  

---

## 7. Embedding Visualization
### 7.1 Observations from word2Vec Word Embedding (t-TSNE Visualization)  

### 7.2 Observations from BERT Post Embeddings (t-SNE Visualization) 
From the t-SNE plot of BERT-based sentence embeddings:
![BERT + t-SNE -Post Embeddings](https://github.com/TuliDas/MindScan-NLP/blob/main/images/eda/embeddings/BERT_tSNE_Post_Embeddings.png)
- **Clear Clusters**:  
  - Posts belonging to **ADHD, Addiction, PTSD, OCD, and Normal** form relatively well-separated clusters.  
  - This indicates that the language patterns in these classes are distinctive enough for the embedding model to group them apart.

- **Anxiety**:  
  - The **Anxiety** class also shows a visible cluster.  
  - However, there are a few noticeable overlaps with **PTSD** posts, which is expected since symptoms and discussions around Anxiety and PTSD often share similar vocabulary and themes.

- **Depression vs Suicidal**:  
  - A significant overlap exists between **Depression** and **Suicidal** classes.  
  - This is understandable, as suicidal ideation is strongly correlated with depressive symptoms, and the linguistic signals used in posts often intersect.  
  - As a result, distinguishing between these two categories based solely on embeddings may be challenging.

### Key Insight:
The embedding visualization suggests that some mental health conditions (e.g., ADHD, Addiction, OCD) have distinct linguistic signatures, while others (especially Depression and Suicidal) are semantically intertwined. This overlap highlights the **real-world complexity** of language use in mental health discourse.

---

## 8. Key Insights & Observations
- Summary of findings from all sections  
- Notable patterns, class differences, and data quality remarks  





