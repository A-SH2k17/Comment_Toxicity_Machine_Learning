## Problem:
People stop expressing themselves and start seeking other people's opinions when toxic comments full of harassment and threats are all over the internet causing many online communities to shut down their comments or messaging sections comments as a result, our main aim is to reduce negative comments.

## Solution:
Our proposed solution is to implement a machine learning model that would be later be fed into a web application that takes the processed user comments as input and outputs whether the comment is clean or toxic. If the comments are toxic, the model will identify the type of toxicity. 

## Dataset Description:
The dataset is from the toxic comment classification challenge in Kaggle: https://www.kaggle.com/c/jigsaw-toxic-comment-classification-challenge/overview. The dataset contains training and test CSV with more than 100,000 rows of comments. The Training CSV is divided into 8 columns. The first two are the ID and comments, and the other 6, with values 0 or 1, are labeled:
- Toxic
- Severe_toxic
- Obscene
- Threat
- Insult
- identity_hate

## Model Selection:
- Logistic Regression
- Linear SVC
- Multinomial Naive Bayes
- Decision Tree
- Grid search

## Rough Plan for Data Processing:
- Cleaning the text from unnecessary symbols, such as “\n” and punctions, and non-ascii symbols
- Tokenize the sentences
- Vectorize the text using TFIDF


## Difficulties met through pre-processing:
- Non-toxic comments are nearly 10 times greater than toxic comment
- Tokenization of comments into vectors so that model can deal with it
- Understanding TF-IDF and how it vectorizes comments
- Online comments structured differently though having the same meaning (same root different usage: verb, noun, adjective, adverb)
- Dealing with comments that contain emojis and no ascii characters 


## Why was each model selected: 
- Multinomial naïve bayes: simple model, probabilistic classifier to calculate the probability distribution of text data, which makes it well-suited for data with features that represent discrete frequencies or counts of events in various natural language processing (NLP) tasks. as well as being fast model that produce good results when it comes to sentiment analysis models as well as it scales with large dataset
- Linear SVC: efficient when it comes to dealing with multiple features, good performance, binary classification as it naturally deals with binary data so it is easy to classify data for model, and finally its robustness toward complex noisy data. And helped dealing with complex dataset
- Logistic regression: simple and efficient model, provides probabilistic interpretation of likelihood sample belong to which feature of toxicity or being non-toxic; moreover, logistic regression model can help prevent overfitting and finally being suited for binary classification.
- Decision tree: decision tree can be easily understood because of its tree like structure as well as being able to classify relation between linear and non-linear data so it is easy to classify relationship between feature and toxicity, reduce probability of overfitting and improve model generalization, as well as decision trees are best fitted for large data.  

## Insights gained from model evaluation: 
Accuracy of model is not always a good indicator to a model’s performance because as shown in our experiment the huge gap in dataset between percentage of toxic and non-toxic label created a bias towards non-toxic comments. Toxic data is relatively low compared to non-toxic data, and as a result, it would not highly affect the accuracy since; however when we look further into precision and recall, who both focus on true positives, the weakness of the model will appear. 

## Results and matrices used in project: 
 


| Description |	Illustration | 
| -- | -- |
Frequency of toxic data and non-toxic data. Percentage non-toxic is relatively high regarding toxic data | <img width="207" alt="image" src="https://github.com/user-attachments/assets/d53cc6f0-1a4c-463f-b026-9b16589b4ae5">
Total frequency of data and the frequencies of toxic regarding precited data and non-toxic. Example: severe toxic data its total is around 1500, all the 1500 are toxic and 0 is non-toxic  | <img width="213" alt="image" src="https://github.com/user-attachments/assets/8a83d386-7e77-4abb-b570-daccb1aa11bb">
Correlation matrix: presents the relation between every two successive variables and the toxicity level between them. Both insult and obscene have highest toxicity values, which shows a high positive relation between the 2 variables. Example: the correlation coefficient between identity hate and obscene is 0.29 which shows that there isn’t a strong relation between the two variables | <img width="226" alt="image" src="https://github.com/user-attachments/assets/579b03b5-56c3-4be2-ab22-dd2fef2b0465">
This is the visualization of the evaluation for grid search CV model presented with percentages of accuracy, f1, precision, and recall for all labels used (toxic, severe toxic, identity hate, threat, and obscene) | <img width="216" alt="image" src="https://github.com/user-attachments/assets/1ce89b8f-f1a0-40c8-b824-a41f88aaf429">
Example of severe toxic confusion matrix of threat for logistic regression model. All other confusion matrices are present with their percentages of true positive, false positive, etc. | <img width="202" alt="image" src="https://github.com/user-attachments/assets/e4039dd3-391c-4d30-98d8-343503b885cd">
Roc curve that is used to present the TP and FP at each threshold and determine the best one for decision making along with AUC curve that is used to help which categorization method is the best | <img width="258" alt="image" src="https://github.com/user-attachments/assets/9f44d957-0464-453a-b63f-c7eb511374fd">

