# Fake News Detection 
**Problem Statement:** 
The spread of fake news has become a significant challenge in today’s digital world. With the constant flow of news articles published daily, it is becoming harder to distinguish between credible and misleading information. This creates a need for systems that can automatically classify articles as true or fake, helping reduce misinformation and protect public trust.

## Table of Contents
* [General Info](#general-information)
* [Conclusions](#conclusions)
* [Technologies Used](#technologies-used)
* [Acknowledgements](#acknowledgements)

<!-- You can include any other section that is pertinent to your problem -->

## General Information
  ### Business Objective:
  The objective of this assignment is to develop a Semantic Classification model that uses the Word2Vec method to detect recurring patterns and themes in news articles. Using supervised learning models, the goal is to build a system that classifies news articles as either fake or true.

  ### Data Description: 
  In this assignment, there are two data sets: The true news data set includes 21,417 true news, whereas the fake news data set comprises 23,502 fake news articles. Each data set includes the following three key attributes:
  - **Title:** The headline of the news article
  - **Text:** The main body content of the article
  - **Date:** The publication date of the article

  ### Methodology: 
  The project followed a structured pipeline, progressing from raw data to a fully evaluated classification model.

  1.	**Data Sourcing and Preparation:**
  - **Datasets:** Two CSV files were used: `True.csv` (21,417 articles) and `Fake.csv` (23,502 articles).
  - **Labelling:** A target column, `news_label`, was created, with 1 assigned to true news and 0 to fake news.
  - **Consolidation:** The two datasets were merged into a single comprehensive dataframe. Null values were identified and dropped to ensure data quality.
  - **Column Merging:** The `title` and `text` columns were combined into a single `news_text` column to create a unified body of text for each article.

  2.	**Text Preprocessing:**  To prepare the text for semantic analysis, a two-stage preprocessing pipeline was implemented:
  - **Initial Cleaning:** Standard cleaning operations were performed to reduce noise, including converting text to lowercase, removing punctuation, and stripping out text in square brackets and words containing numbers.
  - **Semantic Filtering:** The spaCy library was used for advanced NLP tasks. This involved `Part-of-Speech (POS) tagging` to retain only nouns (NN, NNS) and proper nouns (PROPN), followed by lemmatization to reduce words to their base forms. This step filtered out less meaningful words (verbs, adverbs, etc.) and focused the analysis on core subjects and entities.

  3.	**Feature Extraction using Word2Vec:** To convert the processed text into a numerical format suitable for machine learning, the pre-trained `word2vec-google-news-300` model was used. This model contains 300-dimensional vector representations for a vast vocabulary of words. Each news article was transformed into a single 300-dimension vector by averaging the vectors of all its constituent words. This method effectively captures the overall semantic essence of the article.

### Model Training and Evaluation:
- **Data Split:** The vectorized dataset was split into a training set (70%) and a validation set (30%).
- **Model Selection:** Three supervised learning models were chosen for evaluation:
1.	`Logistic Regression`
2.	`Decision Tree Classifier`
3.	`Random Forest Classifier`
- **Hyperparameter Tuning:** `RandomizedSearchCV` was employed to find the optimal hyperparameters for each model, using a 5-fold cross-validation strategy. The F1-Score was selected as the primary metric for optimization, as it provides a balanced measure of precision and recall.
- **Evaluation:** The best-performing version of each model was evaluated on the unseen validation data using four key metrics: `Accuracy`, `Precision`, `Recall`, and `F1-Score`.
