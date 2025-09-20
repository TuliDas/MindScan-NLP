# Exploratory Data Analysis (EDA)

This report presents the exploratory analysis performed on the dataset to understand its structure, distribution, and linguistic characteristics.  

---

## 1. Dataset Structure & Quality
- Dataset shape : (15913 rows, 2 columns)
- Check for missing values : None detected 
The dataset is clean, balanced in terms of structure, and ready for further analysis.
---

## 2. Label Analysis  

We analyzed the distribution of posts across different mental health labels.  

- **Total count of posts per label:**  
  | Label       | Count |
  |-------------|-------|
  | ADHD        | 2000  |
  | Addiction   | 2000  |
  | Anxiety     | 2000  |
  | Depression  | 2000  |
  | Normal      | 2000  |
  | OCD         | 2000  |
  | PTSD        | 2000  |
  | Suicidal    | 1913  |

- **Percentage distribution of labels:**  
  | Label       | Percentage |
  |-------------|------------|
  | ADHD        | 12.57%     |
  | Addiction   | 12.57%     |
  | Anxiety     | 12.57%     |
  | Depression  | 12.57%     |
  | Normal      | 12.57%     |
  | OCD         | 12.57%     |
  | PTSD        | 12.57%     |
  | Suicidal    | 12.02%     |

- **Observations:**  
  - The dataset is mostly balanced across all classes.  
  - Each class contains **~2000 posts**, except **Suicidal**, which has **slightly fewer (1913 posts, 12.02%)**.  
  - This small imbalance is unlikely to significantly affect model performance, but can be handled with class weighting if needed.  

- **Visualization:**  
  ![Posts per Class]([images/eda/posts_per_class.png](https://github.com/TuliDas/MindScan-NLP/blob/main/images/eda/barplots-histplots/sns-barplot-number-of-posts-per-class.png))   

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





