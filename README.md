# portuguese-dialect-analyzer
A NLP Projects for identifying and classifying national varieties of Portuguese

# 1. Overview

Portuguese is spoken across multiple countries and communities, with substantial linguistic variation between national varieties. Two of the most widely studied varieties are European Portuguese (PT-PT) and Brazilian Portuguese (PT-BR).

Natural Language Processing (NLP) models can often distinguish these varieties using lexical, orthographic and character-level patterns. However, their predictions may also be influenced by contextual information, such as geographical references, publication sources and topical content.

This project investigates whether NLP models can identify Portuguese linguistic varieties based on their linguistic characteristics independently of geographical and topical context.

# 2. Research Question

To what extent can NLP models identify Portuguese linguistic varieties independently of geographical and topical context?

The project explores three related questions:

- Which lexical and character-level features are most predictive of PT-PT and PT-BR?

- To what extent does model performance change across different textual domains?

- How do geographical context and topical content influence variety classification?

# 3. Research Methodology

The project follows an experimental approach, combining supervised text classification, cross-domain evaluation and analysis of model features.

### 3.1 Dataset

The primary dataset is PtBrVId, a large-scale Portuguese variety identification corpus.

The journalistic configuration is used for initial model development. Additional configurations provide opportunities to investigate cross-domain generalisation.

A separate manually curated news corpus is also used for exploratory external evaluation.

### 3.2 Preprocessing and Feature Extraction

The initial experiments use TF-IDF representations to extract:

- Word-level features: Unigrams and bigrams.

- Character-level features: Character n-grams (3–5 characters).

The feature representations are combined using scikit-learn's FeatureUnion.

### 3.3 Classification Model

The initial classification model is Logistic Regression.

This provides an interpretable baseline through its learned feature coefficients, allowing investigation of which lexical and character-level patterns are associated with each variety.

### 3.4 Experimental Design

The research is organised into four main stages:

- Data Exploration: Examine dataset composition, class distributions and underlying characteristics.

- Baseline Model Development: Train and evaluate TF-IDF-based Logistic Regression models.

- Cross-Domain Evaluation: Investigate how well the classifier generalises across different textual domains.

- Topic vs. Variety Analysis: Explore the influence of geographical context and topical content on classification performance.

# 4. Model Evaluation 

### 4.1 Baseline Model 

The combined word-level and character-level TF_IDF model achieved the following validation results. 
| Metric   |    Score |
|:---------|---------:|
| Accuracy | 0.953333 |
| Macro F1 | 0.953328 |



### 4.2 Cross-domain evaluation
The baseline model, which was trained on journalistic texts, achieved the following results. 

| Domain       |   Accuracy |   Macro F1 |
|:-------------|-----------:|-----------:|
| journalistic |      0.967 |   0.967    |
| legal        |      0.751 |   0.749738 |
| literature   |      0.551 |   0.544329 |
| politics     |      0.887 |   0.886138 |
| social_media |      0.572 |   0.481386 |
| web          |      0.17  |   0.167198 |

The unexpectedly low performance on the web configuration also raises questions about label consistency and the suitability of the configuration for direct evaluation.

### 4.3 Topic vs Variant analysis
A manually curated corpus, which contains 30 Portuguese news articles and 30 Brazilian news articles was used to investigate the model dependencies on geographical references such as "portugal", "brasil", and "lisboa" and many more. 

| variety   | geographical_scope   |   n_articles |   correct |   accuracy |
|:----------|:---------------------|-------------:|----------:|-----------:|
| pt-br     | domestic             |           15 |        15 |   1        |
| pt-br     | international        |           15 |        10 |   0.666667 |
| pt-pt     | domestic             |           12 |        12 |   1        |
| pt-pt     | international        |           18 |         8 |   0.444444 |   

This suggests that geographical context, topic, publisher characteristics or other distributional differences may influence model predictions. However, the pilot corpus is too small and contains source and topic imbalances, so these results should be treated as exploratory rather than causal evidence.



