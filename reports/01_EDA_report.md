Make a structured narrative of all your findings:

Dataset description

Cleaning steps summary

Lexical diversity comparison

Distinctive keywords (Chi-square)

Word embeddings (visualization + insights)

Sentence/post embeddings (t-SNE + interpretation)



### Observations from BERT Post Embeddings (t-SNE Visualization)

From the t-SNE plot of BERT-based sentence embeddings:

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
