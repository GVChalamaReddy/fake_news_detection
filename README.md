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

  -	**Data Sourcing and Preparation:**
    - **Datasets:** Two CSV files were used: `True.csv` (21,417 articles) and `Fake.csv` (23,502 articles).
    - **Labelling:** A target column, `news_label`, was created, with 1 assigned to true news and 0 to fake news.
    - **Consolidation:** The two datasets were merged into a single comprehensive dataframe. Null values were identified and dropped to ensure data quality.
    - **Column Merging:** The `title` and `text` columns were combined into a single `news_text` column to create a unified body of text for each article.

  - **Text Preprocessing:**  To prepare the text for semantic analysis, a two-stage preprocessing pipeline was implemented:
    - **Initial Cleaning:** Standard cleaning operations were performed to reduce noise, including converting text to lowercase, removing punctuation, and stripping out text in square brackets and words containing numbers.
    - **Semantic Filtering:** The spaCy library was used for advanced NLP tasks. This involved `Part-of-Speech (POS) tagging` to retain only nouns (NN, NNS) and proper nouns (PROPN), followed by lemmatization to reduce words to their base forms. This step filtered out less meaningful words (verbs, adverbs, etc.) and focused the analysis on core subjects and entities.

  - **Feature Extraction using Word2Vec:** To convert the processed text into a numerical format suitable for machine learning, the pre-trained `word2vec-google-news-300` model was used. This model contains 300-dimensional vector representations for a vast vocabulary of words. Each news article was transformed into a single 300-dimension vector by averaging the vectors of all its constituent words. This method effectively captures the overall semantic essence of the article.

### Model Training and Evaluation:
- **Data Split:** The vectorized dataset was split into a training set (70%) and a validation set (30%).
- **Model Selection:** Three supervised learning models were chosen for evaluation:
  1.	`Logistic Regression`
  2.	`Decision Tree Classifier`
  3.	`Random Forest Classifier`
- **Hyperparameter Tuning:** `RandomizedSearchCV` was employed to find the optimal hyperparameters for each model, using a 5-fold cross-validation strategy. The F1-Score was selected as the primary metric for optimization, as it provides a balanced measure of precision and recall.
- **Evaluation:** The best-performing version of each model was evaluated on the unseen validation data using four key metrics: `Accuracy`, `Precision`, `Recall`, and `F1-Score`.

### Model Performance and Results:
All three (`Logistic Regression`, `Random Forest`, `Decision Tree`) models were successfully trained and tuned. The `Logistic Regression model` demonstrated the best overall performance on the unseen validation data, achieving the highest `F1-Score`.

<img width="748" height="102" alt="image" src="https://github.com/user-attachments/assets/23c02289-add4-4c89-b7ea-1bdcf42a0eab" />

## Conclusion: 
The project successfully demonstrates that a semantic classification approach using Word2Vec embedding’s highly effective for fake news detection. The final `Logistic Regression model`, with an F1-Score of `0.94`, provides a reliable and scalable solution. The F1-Score was prioritized as the key evaluation metric because it balances the critical needs of minimizing false positives (labelling real news as fake) and false negatives (failing to detect fake news). The distinct linguistic patterns identified in the EDA confirm that true and fake news are semantically separable.

## Technologies Used
- **python** - 3.13.1
- **numpy** - 2.2.1
- **pandas** - 2.2.3
- **matplotlib** - 3.10.0
- **seaborn** - 0.13.2
- **statsmodels** - 0.14.4
- **sklearn** - 1.6.1
- **keras** - 3.8.0
- **PIL** - 11.1.0
- **tensorflow** - 2.18.0
- **sklearn_crfsuite** - 0.5.0
- **nltk** - 3.9.1
- **spacy** - 3.7.5
- **scipy** - 1.12
- **pydantic** - 2.10.5
- **wordcloud** - 1.9.4

## Acknowledgements

- This project was inspired by Upgrad IIIT Bangalore PG program on ML and AI.
- This project was based on Semantic Classification


## Contact
Created by @[GVChalamaReddy](https://github.com/GVChalamaReddy) and @[Sajeev](https://github.com/sajeevmply)- feel free to contact me!

