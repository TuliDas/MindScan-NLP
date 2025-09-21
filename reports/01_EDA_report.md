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

- **Total count and percentage of posts per label:**

| Label      | Count | Percentage | 
|------------|-------|------------|
| ADHD       | 2000  | 12.57%     |
| Addiction  | 2000  | 12.57%     | 
| Anxiety    | 2000  | 12.57%     | 
| Depression | 2000  | 12.57%     | 
| Normal     | 2000  | 12.57%     | 
| OCD        | 2000  | 12.57%     | 
| PTSD       | 2000  | 12.57%     | 
| Suicidal   | 1913  | 12.02%     |

- **Visualization:**  
  ![Posts per Class](https://github.com/TuliDas/MindScan-NLP/blob/main/images/eda/barplots-histplots/posts_per_class_barplot.png)
  
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

#### Cleaned ML Dataset (`df_cleaned_ml`) and Cleaned Bert Dataset (`df_cleaned_bert`)
- **Average words and char per post by class:**

| Label      | Avg. Words (ML) | Avg. Chars (ML) | Avg. Words (BERT) | Avg. Chars (BERT) |
|------------|----------------|----------------|------------------|------------------|
| ADHD       | 44.63          | 307.42         | 108.28           | 576.70           |
| Addiction  | 35.34          | 235.16         | 83.70            | 435.61           |
| Anxiety    | 37.05          | 248.78         | 89.06            | 470.66           |
| Depression | 35.14          | 229.51         | 87.89            | 451.46           |
| Normal     | 38.80          | 259.75         | 89.91            | 476.65           |
| OCD        | 34.77          | 232.54         | 85.28            | 448.24           |
| PTSD       | 37.09          | 252.31         | 90.78            | 479.80           |
| Suicidal   | 35.58          | 230.25         | 89.28            | 454.86           |

### Observations
- ML-cleaned dataset posts are shorter due to aggressive removal of stopwords and special characters.  
- BERT dataset posts are longer and closer to the original text content.  
- Among classes, **ADHD posts are consistently longer**, while **OCD and Addiction posts are shorter** across both datasets.  
- Character counts follow a similar trend as word counts.


---

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

### 5.1 What is Lexical Diversity?
Lexical diversity measures the **variety of vocabulary** used within a text. It is typically calculated as the ratio of **unique words to total words** (also known as the *type-token ratio*).  
\[
\text{Lexical Diversity} = \frac{\text{Number of Unique Words (Types)}}{\text{Total Number of Words (Tokens)}}
\]  
A higher lexical diversity score indicates richer vocabulary usage, while a lower score suggests more repetition of words.

---

### 5.2 Why is it Important?
- Helps to understand the **expressiveness** of language within each mental health class.  
- Indicates whether users in different categories rely on **repetitive words** (e.g., symptom-related keywords) or use a **broader vocabulary**.  
- Useful in **feature analysis** for NLP tasks, as lexical richness may impact model generalization.  

---

### 5.3 Methodology
Lexical diversity was calculated for each text as the ratio of unique words to total words.  
Afterwards, the **mean lexical diversity score was computed for each class** in both datasets (**df_cleaned_ml** and **df_cleaned_bert**) to allow comparison across mental health categories.  

### 5.4 Results : Comparison of Lexical Diversity (ML vs BERT Datasets)

| Label      | Lexical Diversity (ML) | Lexical Diversity (BERT) |
|------------|-------------------------|---------------------------|
| ADHD       | 0.801                   | 0.725                     |
| Addiction  | 0.839                   | 0.779                     |
| Anxiety    | 0.813                   | 0.753                     |
| Depression | 0.818                   | 0.739                     |
| Normal     | 0.820                   | 0.758                     |
| OCD        | 0.800                   | 0.746                     |
| PTSD       | 0.824                   | 0.751                     |
| Suicidal   | 0.825                   | 0.747                     |

### 5.5 Observations
- **ML dataset** generally shows **higher lexical diversity** compared to the BERT-cleaned dataset.  
- The difference is expected because **BERT preprocessing involves text normalization**, which reduces variation (e.g., lowercasing, token standardization).  
- **Addiction** and **Suicidal** classes show the **highest lexical diversity** in ML dataset, indicating varied expressions in these categories.  
- **ADHD** and **OCD** show comparatively **lower lexical diversity**, suggesting repetitive usage of medical terms (e.g., “adhd”, “ocd”, “medication”).  
- Overall, lexical diversity drops in the BERT dataset due to aggressive preprocessing but still preserves relative class-level trends.  

### 5.6 Visualization
- A **bar plot** can highlight the differences between classes and between the two datasets.  
- Two bars per class: one for `df_cleaned_ml`, one for `df_cleaned_bert`  

![lexical-diversity-comparison-by-class](https://github.com/TuliDas/MindScan-NLP/blob/main/images/eda/barplots-histplots/lexical-diversity-comparison-by-class.png)

---

## 6. Statistical Distinctive Keywords (Chi-Square)

### 6.1 What Are Distinctive Keywords?
While frequent word counts show which terms appear most often in each class, they do not capture whether a word is **truly distinctive** for that class compared to others.  
For example, words like *“feel”* or *“want”* are common across multiple categories, so they are not useful discriminators.  

To address this, we use **statistical tests** such as the **Chi-Square test** to identify words that occur significantly more often in one class than in others. These words are more **class-specific** and are better indicators for classification.

### 6.2 Why Chi-Square?
- **Chi-Square** evaluates the association between each word and the target class.  
- It answers: *“Is the presence of this word strongly linked to this class compared to others?”*  
- A high Chi-Square score means the word is a strong discriminator for that class.  
- This is more **robust and interpretable** than raw frequency because it discounts words that are common everywhere.

### 6.3 Methodology
1. Convert text into **bag-of-words representation** using `CountVectorizer` (removing stopwords, applying min_df to filter rare terms).  
2. For each class, compute **Chi-Square statistics** between word occurrence and class labels.  
3. Rank words by their Chi-Square score.  
4. Select the **Top 10–15 distinctive words per class**.  
5. Visualize results using **bar plots** (per class).  

### 6.4 Distinctive Keywords per Class
Below are the top statistically distinctive words (via Chi-Square) for each class:

- **ADHD**:  
  `adhd, adderall, med, medication, vyvanse, mg, concerta, diagnose, stimulant, focus`  

- **Addiction**:  
  `quit, sober, smoke, drink, addiction, nicotine, cigarette, alcohol, craving, relapse`  

- **Anxiety**:  
  `anxiety, panic, attack, anxious, heart, social, health, symptom, chest, palpitation`  

- **Depression**:  
  `depression, depressed, anymore, antidepressant, tired, hate, care, sad, loser, shit`  

- **Normal**:  
  `lpt, happy, edit, buy, save, travel, thought, small, item, award`  

- **OCD**:  
  `ocd, thought, intrusive, compulsion, obsession, pocd, theme, erp, contamination, harm`  

- **PTSD**:  
  `ptsd, trauma, flashback, trigger, nightmare, abuse, assault, emdr, therapist, sexual`  

- **Suicidal**:  
  `suicide, kill, die, grief, commit, death, suicidal, wish, son, dad`  

### 6.5 Observations
- The Chi-Square method successfully identifies **domain-specific markers** for each class.  
- **ADHD** and **OCD** show clear clinical/medical terminology (e.g., *adderall, medication, intrusive, compulsion*).  
- **Addiction** highlights behavior and recovery-related terms (e.g., *sober, relapse, nicotine*).  
- **Anxiety** emphasizes physiological symptoms (*panic, attack, chest, palpitation*).  
- **Depression** and **Suicidal** classes share emotional and existential markers, but Suicidal also contains explicit terms (*suicide, kill, die*).  
- **Normal** includes casual/non-clinical terms (*lpt, happy, edit, travel*), showing contrast with mental health categories.  
- This statistical filtering is **more informative than raw word frequency**, making it valuable for feature engineering and model explainability.

### 6.6 Visualization
- For each class, bar plots of **Top 10 distinctive words** clearly illustrate the strength of association.  

<p float = "middle">
  <img src="https://github.com/TuliDas/MindScan-NLP/blob/main/images/eda/distinctive-words/addiction-distinctive-class-barplot.png" width="500">
   <img src="https://github.com/TuliDas/MindScan-NLP/blob/main/images/eda/distinctive-words/adhd-distinctive-class-barplot.png" width="500">
   <img src="https://github.com/TuliDas/MindScan-NLP/blob/main/images/eda/distinctive-words/anxiety-distinctive-class-barplot.png" width="500">
    <img src="https://github.com/TuliDas/MindScan-NLP/blob/main/images/eda/distinctive-words/depression-distinctive-class-barplot.png" width="500">
   <img src="https://github.com/TuliDas/MindScan-NLP/blob/main/images/eda/distinctive-words/normal-distinctive-class-barplot.png" width="500">
   <img src="https://github.com/TuliDas/MindScan-NLP/blob/main/images/eda/distinctive-words/ocd-distinctive-class-barplot.png" width="500">
   <img src="https://github.com/TuliDas/MindScan-NLP/blob/main/images/eda/distinctive-words/ptsd-distinctive-class-barplot.png" width="500">
   <img src="https://github.com/TuliDas/MindScan-NLP/blob/main/images/eda/distinctive-words/suicidal-distinctive-class-barplot.png" width="500">
</p>
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





