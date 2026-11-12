# portuguese-dialect-analyzer
A NLP Projects for identifying and classifying national varieties of Portuguese

1. Overview

Portuguese is spoken across multiple countries and communities, with substantial linguistic variation between national varieties. Two of the most widely studied varieties are European Portuguese (PT-PT) and Brazilian Portuguese (PT-BR).

Natural Language Processing (NLP) models can often distinguish these varieties using lexical, orthographic and character-level patterns. However, their predictions may also be influenced by contextual information, such as geographical references, publication sources and topical content.

This project investigates whether NLP models can identify Portuguese linguistic varieties based on their linguistic characteristics independently of geographical and topical context.

2. Research Question

To what extent can NLP models identify Portuguese linguistic varieties independently of geographical and topical context?

The project explores three related questions:

- Which lexical and character-level features are most predictive of PT-PT and PT-BR?

- To what extent does model performance change across different textual domains?

- How do geographical context and topical content influence variety classification?

3. Research Methodology

The project follows an experimental approach, combining supervised text classification, cross-domain evaluation and analysis of model features.

3.1 Dataset

The primary dataset is PtBrVId, a large-scale Portuguese variety identification corpus.

The journalistic configuration is used for initial model development. Additional configurations provide opportunities to investigate cross-domain generalisation.

A separate manually curated news corpus is also used for exploratory external evaluation.

3.2 Preprocessing and Feature Extraction

The initial experiments use TF-IDF representations to extract:

- Word-level features: Unigrams and bigrams.

- Character-level features: Character n-grams (3–5 characters).

The feature representations are combined using scikit-learn's FeatureUnion.

3.3 Classification Model

The initial classification model is Logistic Regression.

This provides an interpretable baseline through its learned feature coefficients, allowing investigation of which lexical and character-level patterns are associated with each variety.

3.4 Experimental Design

The research is organised into four main stages:

- Data Exploration: Examine dataset composition, class distributions and underlying characteristics.

- Baseline Model Development: Train and evaluate TF-IDF-based Logistic Regression models.

- Cross-Domain Evaluation: Investigate how well the classifier generalises across different textual domains.

- Topic vs. Variety Analysis: Explore the influence of geographical context and topical content on classification performance.

