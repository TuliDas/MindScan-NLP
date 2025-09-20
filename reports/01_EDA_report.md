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
- **Visualization:**  
  ![Posts per Class](https://github.com/TuliDas/MindScan-NLP/blob/main/images/eda/barplots-histplots/posts_per_class_barplot.png)
  
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
---

## 3. Text Characteristics

We analyzed the text length and word distribution for posts across different classes and datasets.  

### Distribution of Number of Words per Post
- **Histograms** were plotted for both `df_cleaned_ml` (aggressively cleaned) and `df_cleaned_bert` (minimally cleaned).  
- **Observation:** BERT dataset posts have visibly more words per post compared to ML-cleaned dataset due to minimal cleaning.  

<p float="middle">
  <img src="https://github.com/TuliDas/MindScan-NLP/blob/main/images/eda/barplots-histplots/histplot-words-per-post-ml.png" width="500" />
  <img src="https://github.com/TuliDas/MindScan-NLP/blob/main/images/eda/barplots-histplots/histplot-word-per-post-bert.png" width="500" /> 
</p>

### Number of Words per Class
- **Boxplots** show the distribution of word counts per class for both datasets.
   
<p float="left">
  <img src="https://github.com/TuliDas/MindScan-NLP/blob/main/images/eda/barplots-histplots/boxplot-word-count-per-class-ml.png" width="500"/>
  <img src="https://github.com/TuliDas/MindScan-NLP/blob/main/images/eda/barplots-histplots/boxplot-word-count-per-class-bert.png" width="500"/> 
</p>

### Average Text Length per Class

#### Cleaned ML Dataset (`df_cleaned_ml`)
- **Average words per post by class:**
  | Label       | Avg. Words |
  |-------------|------------|
  | ADHD        | 44.63      |
  | Addiction   | 35.34      |
  | Anxiety     | 37.05      |
  | Depression  | 35.14      |
  | Normal      | 38.80      |
  | OCD         | 34.77      |
  | PTSD        | 37.09      |
  | Suicidal    | 35.58      |

- **Average characters per post by class:**
  | Label       | Avg. Chars |
  |-------------|------------|
  | ADHD        | 307.42     |
  | Addiction   | 235.16     |
  | Anxiety     | 248.78     |
  | Depression  | 229.51     |
  | Normal      | 259.75     |
  | OCD         | 232.54     |
  | PTSD        | 252.31     |
  | Suicidal    | 230.25     |

#### Cleaned BERT Dataset (`df_cleaned_bert`)
- **Average words per post by class:**
  | Label       | Avg. Words |
  |-------------|------------|
  | ADHD        | 108.28     |
  | Addiction   | 83.70      |
  | Anxiety     | 89.06      |
  | Depression  | 87.89      |
  | Normal      | 89.91      |
  | OCD         | 85.28      |
  | PTSD        | 90.78      |
  | Suicidal    | 89.28      |

- **Average characters per post by class:**
  | Label       | Avg. Chars |
  |-------------|------------|
  | ADHD        | 576.70     |
  | Addiction   | 435.61     |
  | Anxiety     | 470.66     |
  | Depression  | 451.46     |
  | Normal      | 476.65     |
  | OCD         | 448.24     |
  | PTSD        | 479.80     |
  | Suicidal    | 454.86     |

### Observations
- ML-cleaned dataset posts are shorter due to aggressive removal of stopwords and special characters.  
- BERT dataset posts are longer and closer to the original text content.  
- Among classes, **ADHD posts are consistently longer**, while **OCD and Addiction posts are shorter** across both datasets.  
- Character counts follow a similar trend as word counts.


---

## 4. Word-Level Analysis

## 4. Word-Level Analysis

### 4.1 Initial Word Analysis
- Generated word clouds for each class to visualize most frequent words.  
- Calculated top 20 most frequent words per class (before removing common words).  

**Observation:**  
Many common words such as *not, like, feel, know, want, time, go, think, get* appear in most classes. These are considered noise for EDA purposes.

---

### 4.2 After Removing Common Words
- **Purpose:**  
This step is **for EDA only** to highlight class-distinctive words. These cleaned visualizations are **not used for model training**.
- Removed common/repetitive words appearing in more than 4 classes, including typical stopwords and negations, e.g.:  
```
work, today, year, day, thing, like, feel, know, want, time, go,
think, get, take, people, life, start, help, try, good, bad,
need, tell, way, no, not, never, nor
```
- Re-generated word clouds for each class after removing common words.  
<p float = "middle">
  <img src="https://github.com/TuliDas/MindScan-NLP/blob/main/images/eda/wordclouds/adhd_wc.png" width="300">
   <img src="https://github.com/TuliDas/MindScan-NLP/blob/main/images/eda/wordclouds/addiction_wc.png" width="300">
   <img src="https://github.com/TuliDas/MindScan-NLP/blob/main/images/eda/wordclouds/anxiety_wc.png" width="300">
</p>

<p float = "middle">
  <img src="https://github.com/TuliDas/MindScan-NLP/blob/main/images/eda/wordclouds/depression_wc.png" width="300">
   <img src="https://github.com/TuliDas/MindScan-NLP/blob/main/images/eda/wordclouds/normal_wc.png" width="300">
   <img src="https://github.com/TuliDas/MindScan-NLP/blob/main/images/eda/wordclouds/ocd_wc.png" width="300">
</p>

<p float = "middle">
  <img src="https://github.com/TuliDas/MindScan-NLP/blob/main/images/eda/wordclouds/ptsd_wc.png" width="300">
   <img src="https://github.com/TuliDas/MindScan-NLP/blob/main/images/eda/wordclouds/suicidal_wc.png" width="300">
</p>

**Top 20 words per class (after cleaning):**  

- **ADHD:** adhd, med, medication, find, diagnose, mg, experience, adderall, month, week, long, focus, lot, make, say, anxiety, hour, look, struggle, school  
- **Addiction:** quit, drink, smoke, sober, month, stop, week, addiction, long, thank, alcohol, cigarette, hard, nicotine, well, night, ago, clean, friend, drug  
- **Anxiety:** anxiety, panic, attack, anxious, heart, social, have, make, symptom, happen, talk, health, come, friend, stop, look, experience, die, say, week  
- **Depression:** depression, friend, anymore, hate, well, talk, live, depressed, tired, end, love, hard, care, happy, make, find, die, thought, stop, long  
- **Normal:** lpt, happy, love, friend, look, s, find, lot, say, edit, make, new, come, thank, ask, little, old, talk, see, post  
- **OCD:** ocd, thought, intrusive, anxiety, compulsion, stop, make, happen, have, find, say, fear, come, person, look, brain, right, head, experience, lot  
- **PTSD:** ptsd, trauma, trigger, happen, experience, flashback, have, nightmare, therapy, sleep, talk, find, therapist, come, friend, lot, hard, anxiety, stop, make  
- **Suicidal:** die, suicide, kill, love, live, friend, find, lose, end, wish, hate, anymore, well, leave, family, fuck, brother, month, miss, say

**Observation:**
After cleaning, the distinctive words per class are more meaningful, helping to understand unique linguistic patterns across different mental health classes. Word clouds now provide a clearer picture of class-specific terms.

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





