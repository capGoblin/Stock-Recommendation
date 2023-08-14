# Stock Recommender Trained from r/wallstreetbets Posts
A stock recommender system that trained based on posts from the r/wallstreetbets subreddit to provide stock recommendations. Used Yahoo Finance API to extract ticker symbols mentioned in the posts, and then classifies the posts into "best" and "not best" categories based on the % increase of the associated stock price from the post's publication date to 90 days later (for supervised algos).<br> A post is considered "good" if the stock price increases by more than 6%, otherwise it is categorized as "bad".

Extracted ticker symbols from r/wallstreetbets posts using the Yahoo Finance API (yfinance).<br>
Used Word Embedding (Glove) and term frequency-inverse document frequency (TD-IDF) vectorizer from Scikit-Learn for Feature Extraction.<br>
Performed hyperparameter grid search for various classifiers.<br>
Evaluated model performance using accuracy, precision, recall, and F1-score.<br><br>
Trained using two different approaches: Word Embedding (Glove) and TfidfVectorizer.<br>The classification models employed in the training process include:

### With Word Embedding (Glove)
Logistic Regression (L1):<br>
Best Parameters: {'C': 1.0, 'max_iter': 100, 'penalty': 'l1', 'solver': 'liblinear'}<br>
Best Score: 0.6318382715232276

Logistic Regression (L2):<br>
Best Parameters: {'C': 1.0, 'max_iter': 100, 'penalty': 'l2', 'solver': 'lbfgs'}<br>
Best Score: 0.6222725969069208

LinearSVC:<br>
Best Parameters: {'C': 0.1, 'class_weight': 'balanced', 'dual': False, 'loss': 'squared_hinge', 'max_iter': 1000, 'penalty': 'l2'}<br>
Best Score: 0.6567347930261574

XGBoost Classifier:<br>
Best Parameters:
colsample_bytree: 0.8
learning_rate: 0.01
max_depth: 10
n_estimators: 100
subsample: 0.8<br>
Accuracy: 0.7279693486590039

### With Tfidf Vectorizer
Logistic Regression (L1):<br>
Best Parameters: {'C': 1.0, 'max_iter': 100, 'penalty': 'l1', 'solver': 'liblinear'}<br>
Best Score: 0.6864598730705025

Logistic Regression (L2):<br>
Best Parameters: {'C': 10, 'max_iter': 400, 'penalty': 'l2', 'solver': 'lbfgs'}<br>
Best Score: 0.7027636213882822

XGBoost Classifier:<br>
Best Parameters:
colsample_bytree: 0.8
learning_rate: 0.01
max_depth: 10
n_estimators: 100
subsample: 0.8<br>
Best Score: 0.6951173325685206

Multinomial Naive Bayes:<br>
Best Parameters: {'alpha': 0.1, 'class_prior': [0.4, 0.6], 'fit_prior': True}<br>
Best Score: 0.6490195104177018

LinearSVC:<br>
Best Parameters: {'C': 1.0, 'class_weight': None, 'dual': False, 'loss': 'squared_hinge', 'max_iter': 1000, 'penalty': 'l2'}<br>
Best Score: 0.7200304746762066

Max Reached:<br>
Logistic Regression (L1) - Accuracy: 0.7126436781609196<br>
Logistic Regression (L2) - Accuracy: 0.6819923371647509<br>
Multinomial Naive Bayes - Accuracy: 0.6398467432950191<br>
Precision: 0.6376811594202898<br>
Recall: 0.6666666666666666<br>
F1-Score: 0.6518518518518518<br>
LinearSVC - Accuracy: 0.7624521072796935<br>
XGBoost Classifier - Accuracy: 0.7241379310344828<br>
