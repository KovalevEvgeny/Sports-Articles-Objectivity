# Sports-Articles-Objectivity
A final project at "Introduction to Data Science" 1-st year MSc DS course at Skoltech. Dataset: http://archive.ics.uci.edu/ml/datasets/Sports+articles+for+objectivity+analysis

Correct order of the notebooks:

1. texts_eda.ipynb
2. texts_dl.ipynb
3. texts_tfidf.ipynb
4. texts_feature_extraction.ipynb
5. tabular_data.ipynb

In this project the articles' subjectivity has been predicted based on the data of different nature - texts themselves (preprocessed), TF-IDF matrix and tabular data with the attributes of texts, extracted from them directly and by using Stanford POS Tagger. Exploratory Data Analysis has been performed. It showed that there were no evident words-markers in the texts, but, however, some attributes from the tabular data seemed to distinguish the classes in some good way. Also EDA on tabular data after scaling showed that some of the features were constant or almost constant (hence they were dropped because they presumably contained no useful information), and some of the features were linearly dependent, they were also excluded because it might have caused troubles in training linear models such as Logistic Regression. Interesting finding - it was shown that features VB (Frequency of base form verbs) and past (Frequency of past tense verbs with 1st and 2nd person pronouns) are linearly dependent, probably because in the majority of times only past tense was used in the article. After that, machine learning models with tuned hyperparameters have been applied to the task. Three different approaches were compared. Firstly, deep learning models such as LSTM and LSTM with an additional convolutional layer in the top of it were applied to the preprocessed texts. The latter was the better, but it was later shown that this approach provided the worst results among the all three. Secondly, different machine learning models were applied to the TF-IDF matrix obtained from the preprocessed texts. Finally, the same machine learning methods (but with different hyperparameters) were applied to the tabular data. In this approaches XGBoost proved to be the best, and tabular data provided the most useful features.

Using the best algorithm (XGBoost on tabular data), it was possible to interpret the results in order to prove that the model didn't overfit on some noise and its predictions are really valuable. It was shown that feature extraction from texts provided a golden feature - share of the stopwords in the total number of words.

As far as the interpretable model was constructed, it can be applied in a real-life scenario. Its final quality was pretty good, but perhaps in order to bring it to production and successfully use it to completely solve the proposed problem of articles subjectivity it may be useful to train it on a larger dataset, so the impact of this model can become very huge and make bets less biased towards the irrelevant information, saving a lot of money for the betters.

Also probably deep learning models may perform better since they are very widely used to solve NLP tasks, but the proposed problem seem complex (there are no evident words-markers), so the patterns are more difficult to be identified, hence the more complex neural networks architectures are required. Also the bigger dataset is required to increase performance of deep learning approach.
