# Text Mining and Topic Modeling of U.S. Presidential Speeches

---

## Purpose
This program focuses on analyzing the speeches of U.S. presidents using advanced text mining techniques. It begins by collecting speeches from a dataset that includes the top 10 most popular presidents (as identified by a reputable source), along with additional speeches from Presidents Trump and Biden. Through systematic preprocessing and analysis, the program uncovers patterns and themes within the data using clustering and topic modeling methods.

---

## Objectives
1. **Dataset Collection**: Collect and integrate speeches from notable U.S. presidents, ensuring the dataset is comprehensive and representative.
2. **Data Cleaning**: Perform systematic data cleaning to prepare the text for analysis.
3. **Text Transformation**: Transform the text using TF-IDF, providing a foundation for clustering and topic modeling.
4. **Clustering Algorithms**: Explore clustering algorithms suitable for text mining.
5. **Model Evaluation**: Interpret the results of clustering models and compare their effectiveness.
6. **Topic Modeling**: Apply three topic modeling techniques (LDA, NMF, BERTopic) and interpret the results.

---

## Features

- **Comprehensive Dataset**: Includes speeches from notable U.S. presidents, including modern and historical figures.
- **Advanced Text Mining**: Employs systematic text preprocessing and mining techniques.
- **Multiple Clustering Methods**: Utilizes algorithms such as K-Means, Agglomerative Clustering, DBSCAN, and Spectral Clustering.
- **Topic Modeling**: Explores Latent Dirichlet Allocation (LDA), Non-Negative Matrix Factorization (NMF), and BERTopic for topic analysis.
- **Visualization**: Provides interactive and static visualizations to interpret results.

---

## Dataset: Inaugural Corpus

The **Inaugural Corpus** is a prebuilt dataset provided by the Natural Language Toolkit (**NLTK**) library. It contains the full text of the inaugural addresses delivered by U.S. presidents, starting from George Washington's first address in 1789 to more recent speeches.

### Key Features of the Inaugural Corpus:

1. **Historical Significance:**  
   - The corpus spans centuries of U.S. history, offering valuable insights into changes in political language, priorities, and issues over time.

2. **Rich Source for Text Analysis:**  
   - It provides a diverse and high-quality dataset for natural language processing (NLP) tasks, such as topic modeling, sentiment analysis, and linguistic evolution studies.

3. **Diverse Perspectives:**  
   - By analyzing these speeches, researchers can explore how different presidents addressed various national and global challenges.

4. **Preformatted for Easy Access:**  
   - The dataset is already tokenized and structured, making it easy to extract, preprocess, and analyze.

### Selected Presidents:

This list is based on the most **popular** and **newsworthy U.S. Presidents** of the past 100 years.  
Criteria for selection included:
- Their impact on U.S. domestic and foreign policies.
- Media coverage and public opinion.
- Rankings from historical surveys and reputable websites.

The following source was used to guide this selection:  
- [C-SPAN's Historians Survey of Presidential Leadership](https://www.c-span.org/presidentsurvey2021/?page=overall)

### Included Presidents:

| No. | President               | Term         | Highlights                                                                                  |
|-----|-------------------------|--------------|--------------------------------------------------------------------------------------------|
| 1   | Franklin D. Roosevelt  | 1933–1945    | Led the U.S. through the Great Depression and World War II. Established the New Deal.      |
| 2   | Theodore Roosevelt     | 1901–1909    | Known for progressive reforms and conservation efforts. Expanded U.S. influence globally.  |
| 3   | Harry S. Truman        | 1945–1953    | Made the decision to drop the atomic bombs in WWII. Initiated the Marshall Plan.           |
| 4   | Dwight D. Eisenhower   | 1953–1961    | Oversaw post-war prosperity and the construction of the Interstate Highway System.          |
| 5   | John F. Kennedy        | 1961–1963    | Handled the Cuban Missile Crisis and promoted the Space Race. Advocated for civil rights.  |
| 6   | Lyndon B. Johnson      | 1963–1969    | Passed the Civil Rights Act and launched the Great Society programs.                       |
| 7   | Richard Nixon          | 1969–1974    | Ended the Vietnam War and opened diplomatic relations with China. Resigned due to Watergate.|
| 8   | Jimmy Carter           | 1977–1981    | Promoted human rights and negotiated the Camp David Accords. Faced energy shortages.       |
| 9   | Ronald Reagan          | 1981–1989    | Led the conservative revolution and played a significant role in ending the Cold War.      |
| 10  | Bill Clinton           | 1993–2001    | Presided over economic growth and globalization. Faced impeachment but remained popular.   |
| 11  | Barack Obama           | 2009–2017    | Passed the Affordable Care Act. Managed the economic recovery after the 2008 financial crisis.|
| 12  | Donald Trump           | 2017–2021    | Oversaw significant policy changes in trade and immigration. Dominated the media.          |
| 13  | Joe Biden              | 2021–Present | Focused on pandemic recovery and strengthening alliances. Oldest president at inauguration.|

---

## Analysis and Interpretation of Clustering Results

### Clustering Algorithm Performance

1. **K-Means:**
   - **Silhouette Score:** 0.03
   - **Interpretation:**  
     K-Means performed poorly on this dataset. The low Silhouette Score indicates that the clusters are not well-defined, and data points may not be correctly assigned to clusters.

   ![K-Means Clustering (PCA Visualization, Silhouette Score: 0.03)](images/kmeans_pca.png)

2. **Agglomerative Clustering:**
   - **Silhouette Score:** 0.45
   - **Interpretation:**  
     Agglomerative Clustering showed moderate performance. The Silhouette Score of 0.45 indicates that the clusters are reasonably well-formed, but there is still room for improvement.

   ![Dendrogram for Agglomerative Clustering](images/agglomerative_dendrogram.png)

3. **DBSCAN:**
   - **Davies-Bouldin Index:** Cannot be calculated (only one cluster or no clusters).
   - **Interpretation:**  
     DBSCAN failed to create meaningful clusters due to unsuitable parameter choices (`eps` and `min_samples`). The algorithm treated most data points as noise or created only a single cluster.

   ![DBSCAN Clustering (UMAP Visualization)](images/dbscan_umap.png)

4. **Spectral Clustering:**
   - **Davies-Bouldin Index:** 0.47
   - **Interpretation:**  
     Spectral Clustering performed the best among the tested algorithms. The Davies-Bouldin Index of 0.47 indicates very good clustering quality, with well-separated clusters.

   ![Spectral Clustering (UMAP Visualization)](images/spectral_umap.png)

### Visualization of Results

#### Silhouette Score:
- **Best Algorithm:** Agglomerative Clustering  
  The highest Silhouette Score of 0.45 indicates that Agglomerative Clustering formed the most cohesive clusters.

#### Davies-Bouldin Index:
- **Best Algorithm:** Spectral Clustering  
  A Davies-Bouldin Index of 0.47 signifies high-quality clusters, as lower values represent better clustering.

   ![Davies-Bouldin Index for Spectral Clustering](images/spectral_davies_bouldin.png)

### Recommendations

1. **Best Algorithm:**  
   - **Spectral Clustering** is recommended as the top choice. Its ability to form well-separated clusters makes it the most suitable algorithm for this dataset.

2. **Alternative Algorithm:**  
   - **Agglomerative Clustering** also demonstrated acceptable performance, particularly in terms of Silhouette Score. It can be a secondary option if computational simplicity is desired.

3. **Improving DBSCAN:**  
   - DBSCAN's failure suggests that the parameters (`eps` and `min_samples`) were not optimal. Tuning these parameters may lead to better results.

### Next Steps

1. **Adopt Spectral Clustering for further analysis** to explore the themes and patterns in speeches.
2. **Fine-tune DBSCAN parameters** to assess whether it can provide meaningful clusters with this dataset.
3. **Visualize clusters** using dimensionality reduction techniques like UMAP or t-SNE for better interpretation.

---

## Topic Modeling Results and Comparison

### Interpretation of Topic Modeling Results Across Three Methods

This section presents a detailed interpretation and comparison of topic modeling results obtained using three distinct methods on the corpus of presidential speeches:

1. **Latent Dirichlet Allocation (LDA):** A probabilistic approach to topic modeling.
2. **Non-Negative Matrix Factorization (NMF):** A matrix factorization-based method.
3. **BERTopic:** A modern technique leveraging transformers and clustering algorithms.

---

### Comparison of Results

#### **Latent Dirichlet Allocation (LDA)**

**Identified Topics:**

- The LDA model identified 5 main topics:
  - **Topic 0:** Related to freedom and civil rights (e.g., ["freedom", "nation", "rights"]).
  - **Topic 1:** Economic growth and jobs (e.g., ["economy", "growth", "jobs"]).

**Strengths:**

- Effectively captures high-level themes like politics and economy.
- Outputs interpretable topic-word distributions.

**Weaknesses:**

- Predefining the number of topics limits flexibility.
- Sensitive to parameter tuning (e.g., alpha, beta values).

---

#### **Non-Negative Matrix Factorization (NMF)**

**Identified Topics:**

- NMF identified 6 topics, examples include:
  - **Topic 0:** Legal and judicial issues (e.g., ["justice", "laws", "court"]).
  - **Topic 1:** Education and societal development (e.g., ["education", "students", "schools"]).

**Strengths:**

- Generates sharp and actionable insights due to its reliance on factorization.
- Efficient for sparse datasets with distinct word distributions.

---

#### **BERTopic**

**Identified Topics:**

- BERTopic grouped the speeches into 3 main clusters:
  - **Topic -1:** Undefined or noise, including speeches with mixed content.
  - **Topic 0:** Primarily political speeches.
  - **Topic 1:** Economic policies and related themes.

**Strengths:**

- Context-aware embeddings led to refined clustering.
- Automatic topic number selection simplified the process.

---

### Detailed Comparison

![Topic Modeling Comparison Table](images/topic_modeling_comparison.png)

---

### Conclusion

1. **LDA** provided a clear view of overarching themes like civil rights and economic development but required precise parameter tuning and predefined topic numbers.
2. **NMF** excelled at isolating actionable insights from speeches with distinct themes but showed some topic overlap in interconnected areas.
3. **BERTopic** emerged as the most context-aware approach, adept at capturing nuanced patterns in speech content. Its advanced embeddings made it particularly suitable for rich text corpora but demanded significant computational resources.

**Recommendation:**

For highly structured datasets with clear thematic separation, **LDA** or **NMF** may suffice. However, for analyzing complex and context-rich data like presidential speeches, **BERTopic** is recommended despite its computational intensity.

---

## Prerequisites

- Python 3.8+
- Libraries: Gensim, Scikit-learn, Pandas, Matplotlib, PyLDAvis, BERTopic, Sentence-Transformers

---

## Structure and Sections
- **Introduction**: Overview of the project.
- **Data Preparation**: Steps for data cleaning and text preprocessing.
- **Text Transformation**: Converting raw text into numerical representations (TF-IDF).
- **Clustering**: Implementation of clustering algorithms.
- **Topic Modeling**: Analysis using LDA, NMF, and BERTopic.

---

## About the Author and Institution

This project was completed as part of the **Master's Program in Advanced Research in Management of Information Systems (ARAMIS)** at [University Grenoble Alpes (Grenoble IAE - INP)](https://iae.grenoble-inp.fr/). The program emphasizes the development of critical analysis and innovative research skills in information systems, supported by the **CERAG Research Center**, one of the top research institutions in France.

### About Me:
**Hossein Habibinejad**  
- Master's student in ARAMIS.  
- Passionate about text mining, machine learning, and AI-driven modeling for advancing green finance.  
- Connect with me on [LinkedIn](https://www.linkedin.com/in/hossein-habibinejad-5a792048/).

---

## CSV Files

This project includes **12 CSV files** stored in the same repository. They can be accessed directly through the GitHub folder structure for further exploration and analysis.
