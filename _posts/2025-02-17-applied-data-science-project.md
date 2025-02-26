---
layout: post
author: Jessica (part of Team 7)
title: "Applied Data Science Project Documentation"
categories: ITD214
---
## Project Background
**Overall Business Goal:** 
Analyse global news, industry discussions, government policies, and customer feedback from Jan 2024 till-date, to help Tech giant (Apple) identify risks and/or opportunities and plan for its next iPhone rollout

**My Objectives:** 
Track and analyse customer feedback on iPhones to:
- detect shifts in user preferences and behavior
- decide if to continue with iPhone future rollout

## Work Accomplished

### Data Preparation
First, I used Python to scrape online reviews from Apple’s distribution partners, including Trustpilot and Amazon.
Second, I leveraged Reddit’s API to extract discussions from active iPhone communities such as r/iphone, r/iPhone15, and r/apple.
Additionally, I sourced datasets from Kaggle, particularly those with pre-scraped iPhone reviews, and gathered YouTube review comments. 
However, data biases exist. Reviews tend to be skewed based on demographics, personal opinions, and regional differences.
For consistency, I focused on the iPhone lineup, selecting reviews for base storage models, as they are typically bestsellers with the highest number of reviews.

### Data Understanding and Selection
After collecting the data, I selected key fields relevant to the analysis. These include: 
- The review text, which is the most critical component for sentiment analysis.
- Ratings, where available, to correlate user sentiment with scores.

The word cloud visualization highlights frequently mentioned terms like “iPhone,” “app,” “screen".
![image](https://github.com/user-attachments/assets/6e99985b-c91d-4ba1-9b5a-bd9d659aa52d)

The word frequency distribution graph confirms the most discussed topics.
![image](https://github.com/user-attachments/assets/10d43359-2588-46c2-872d-83092198038a)

Next, I explored the dataset to understand its quality and structure. I generated summary statistics and checked for missing or duplicate values.
Some reviews contained unnecessary punctuation, special characters, and stopwords, which required preprocessing. 

### Data Cleaning and Transformation
To clean the data, I tokenized text into words and sentences, removed stopwords and punctuation, and applied stemming and lemmatization to standardize words. With a cleaned dataset, I engineered additional features such as word count, character count, and stopword rate to enrich analysis.

These steps set the foundation for sentiment analysis, helping me detect positive and negative trends in customer feedback.
In summary, by leveraging multiple data sources and applying robust preprocessing techniques, I can analyse customer sentiment and identify emerging trends.
The cleaned and structured data will now be used for sentiment analysis to assess whether user sentiment is shifting positively or negatively over time.

### Modelling Design
Next, I extracted features using two key techniques: Bag of Words and TF-IDF, transforming the text data into numerical representations suitable for machine learning models. The steps I had taken are detailed below: 
- I divided the dataset into training (80%) and testing (20%) sets.
- Creates separate training and testing sets for both Bag of Words (BoW) and TF-IDF features, then
- Trained three different classifiers: Naïve Bayes, Logistic Regression, and Support Vector Machine (SVM)

### Model Assessment & Evaluation
- Trains each model on the respective feature representation (BoW or TF-IDF).
- Predicts sentiment labels on the test set.
- Evaluates model performance using confusion matrix and also classification_report(), assessing accuracy, precision, recall, and F1-score to determine the most effective approach for sentiment detection.

![image](https://github.com/user-attachments/assets/215375dd-92ee-4319-83a5-4434ffe5876d)

![image](https://github.com/user-attachments/assets/2ddfc94c-d9c6-4789-9504-b87e7fb761ec)

Key observations from the confusion matrix include:
- The model performs very well on Positive sentiment, with 3242 correctly classified and very few misclassifications.
- The model struggles more with Neutral sentiment, misclassifying many Neutral cases as either Negative or Positive.
- The model overpredicts Positive sentiment, sometimes misclassifying Negative or Neutral cases as Positive.
- The lowest accuracy appears to be for Neutral sentiment, which may indicate that the model has difficulty distinguishing Neutral from other sentiments.

## Recommendation and Analysis
SVM (BoW) is the best model overall due to its high accuracy, balanced precision-recall trade-off, and strong macro-averaged performance. But if speed is important, Logistic Regression (BoW) might be a good alternative. 
Overall, a positive sentiment was predicted and hence Apple should continue rolling out their iPhones. 

However, there are three enhancements which I can make to improve my model:
1. Use Advanced Sentiment Analysis Models: Examples include BERT or other transformer-based models to better understand the nuances in customer feedback, particularly for capturing subtle shifts in sentiment and detecting changes in user behavior over time.
2. Fine-Tune the Model for iPhone-Specific Terms: Fine-tune the vectorizer and model by focusing on specific terminology related to iPhones, such as features (e.g., camera, battery life, screen size) or product versions, to more accurately capture shifts in user sentiment toward different aspects of the iPhone.
3. Use a more balanced dataset with 50-50 positive-negative sentiments.

## AI Ethics and Considerations
- Privacy: Ensure compliance with GDPR/CCPA by anonymizing user data and avoiding personal identifiers; adhere to platform terms of service, especially for web scraping and data collection
- Fairness: Address demographic and platform-specific biases to ensure diverse user representation; Regularly audit models for bias, especially in sentiment classification across different user groups
- Accuracy: Use aspect-based sentiment analysis to capture nuanced opinions on different iPhone features; Improve NLP models to detect sarcasm, slang, and contextual sentiment shifts
- Accountability: Clearly define responsibility for data collection, model decisions, and impact assessments; Implement human oversight to validate AI-driven insights before making business decisions
- Transparency: Disclose methodology, data sources, and limitations when presenting sentiment findings; Use explainable AI techniques to justify sentiment scores and avoid black-box decision-making

## Source Codes and Datasets
https://github.com/hyenajessica/hyena-hacks
