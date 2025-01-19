1.	Logistic Regression
i.	The content and structure of the dataset (Facebook_Ads_2.csv)
The dataset includes data on Facebook advertisements, with a particular emphasis on user click-through rates. This is an extensive summary of the dataset:

The dataset contains 499 rows and 6 columns

The columns of the dataset are presented as follows:
Names: The names of the people listed in this column. This is a string (object type) representation of a category feature.

Emails: Email addresses of the persons are listed in this column. This feature is categorical and is shown as a string.

Country: The individual's countries are listed in this column. This feature is categorical and is shown as a string.

Time spent on Site: The amount of time (measured in minutes) users spend on the site is listed in this column. It's a continuous numerical characteristic that has a float representation.

Salary: The information about each person's salary is contained in this column. It is a float-based continuous numerical characteristic.

Clicked: The dependent variable (target) in this column indicates whether or not the person clicked on the advertisement. This categorical characteristic is binary, with an integer representing it (0 for not clicked and 1 for clicked).

The column “Clicked” is the dependent variable of the dataset and due to its binary nature, it can only accept one of two values such that:

0: means that the user did not select the advertisement.
1: means that the user made an advertisement click.

The dataset is especially well-suited for logistic regression, which is intended to predict binary outcome variables, due to its binary character.
Suitability of the dataset for logistic regression task:
logistic regression is a statistical technique for binary classification issues. The following justifies the suitability of this dataset for logistic regression:

Binary Outcome: Because the target variable "Clicked" is binary, logistic regression is a suitable modeling technique.
Logistic regression can be used to model complex associations because the dataset includes both continuous (like Time Spent on Site and Salary) and categorical (like Country) variables.
No Missing Values: The dataset integrity for modeling is ensured by the non-null values present in every column.

Interpretability: The coefficients obtained via logistic regression are comprehensible, offering valuable insights into the influence of individual features on the probability of clicking on the advertisement.

ii.	Loading and preparing the dataset
The dataset was successfully loaded and prepared using the following steps:
a)	Removal of non-numeric and non-essential columns 
The Names and emails columns were removed from the dataset. Since they are not numerical and may not be required for modeling, they are not necessary for the analysis.

b)	Categorical Variables Encoding:
This section uses label encoding to transform the categorical Country column into numerical values. By giving each distinct nation name a unique integer, LabelEncoder converts categorical data into a format that machine learning algorithms can use.

c)	Numerical variables normalization:
The Time Spent on Site and Salary columns were standardized in this section. These numerical variables are normalized by StandardScaler to have a mean of 0 and a standard deviation of 1. The performance and convergence of machine learning algorithms are enhanced by this standardization.
iii.	The dataset was split into two, 80% train and 20% test sets:
The k-fold cross validation was applied with the range of 2 to 20. A range of 2 to 20 offers a decent compromise, enabling the user to see how the mean accuracy score varies with various fold counts and choose an ideal spot without unduly burdening the computer.

In k-fold cross-validation, the optimal value for k is 8, which produced the highest average accuracy score of approximately 0.905 as shown in the results of k-fold cross validation in figure 1.

 
Figure 1: Results of the k-fold cross validation

iv.	The Logistic Regression model was trained and the performance of the model was evaluated using different matrices which are presented in figures 2 and 3.
The performance matrices are briefly explained as follows:
• Accuracy: The percentage of instances among all cases that were correctly predicted.
• Precision: The percentage of all positive predictions that are actually positive.
• Recall: The percentage of all real positives that were true positive predictions.
• F1 Score: The precision and recall harmonic means.
• ROC AUC Score: The model's ability to differentiate between classes is represented by the area under the ROC curve.
 
Figure 2: Logistic regression Confusion matrix

The results of the confusion matrix for the logistic regression model are:  True Positive (TP) = 49, True Negative (TN) = 48, False Positive (FP) = 2, and False Negative (FN) = 1.

 
Figure 3: The ROC curve results for Logistic Regression model
The performance metrics results were presented in table 1 as follows:

Table 1: The summary of performance metrics for the Logistic Regression Model
Performance Metrics	Results
Accuracy	0.97
Precision	0.9607843137254902
Recall	0.98
F1 Score	0.9702970297029702
ROC AUC	0.9763999999999999
 
The outcomes of the logistic regression show that the model did a good job of predicting whether or not people would click on the advertisements. Here is a quick analysis of every metric:
97% Accuracy: This indicates that 97% of the model's predictions are accurate. Although high accuracy indicates the model's effectiveness, it does not distinguish between different kinds of errors.
Precision (0.9608): 96.08% of the predicted positive cases (ads clicked) are actually positives, according to precision. High precision indicates a low false positive rate, indicating that the model does an excellent job of not mislabeling non-clicked ads as clicked.
Recall (0.98): With 98% of actual clicked ads properly detected, recall, also known as sensitivity, gauges how well the model can detect real positives. A high recall rate means that the model hardly ever misses actual clicked ads due to a low false negative rate.
F1 Index (0.9703): The harmonic mean of recall and precision, which strikes a balance between the two, is the F1 score. With a score of 0.9703, the model appears to be in good equilibrium and performs well in terms of recall and precision.
ROC AUC (0.9764): Excellent discriminating capacity is shown by the Receiver Operating Characteristic Area Under the Curve (ROC AUC) score of 0.9764. A score near to 1 indicates a high degree of differentiation between the two classes (clicked vs. not clicked), and it indicates how well the model distinguishes between them.
v.	The data distribution was analysed to choose the best probabilistic distribution for the naïve Bayes classifier. The results are as shown in figure 4.
 
Figure 4: Data distribution
The probabilistic distribution for the Naive Bayes classifier should be selected based on the features of the numerical data (Time Spent on Site and Salary), given their distributions. The histograms demonstrate that the distributions of Time Spent on Site and Salary are relatively bell-shaped, with continuous values. Given that the Gaussian (Normal) distribution is intended for continuous data with a normal distribution, this implies that it should be appropriate.
Gaussian Naive Bayes: Considering the major features of the dataset, Time Spent on Site and Salary: The Gaussian curve-fitting peaks and tails of both measures display a continuous nature, resembling an approximately normal distribution. This situation appears to fit the Gaussian Naive Bayes model's assumption that the features have a normal distribution.
Other types of probabilistic distributions are the multinomial Naïve Bayes, Bernoulli Naïve Bayes and Categorical Naïve Bayes. Analyzing these other approaches to know if they might fit in this case:
The Multinomial Naïve Bayes: Usually this method is applied to discrete features (word counts, for example, in text classification issues). Since Time Spent on Site and Salary are continuous primary features, this dataset is not appropriate for it.
Naive Bernoulli Bayes: This type is suitable for features that are binary or boolean. However, since the primary properties of this dataset are not binary, it is not appropriate for it. It could be applied to the variable of dependent variable “clicked” only in isolation without regard to the predictors which is not the purpose in this case.
Categorical Naïve Bayes: It is usually applied to categorical features with a limited quantity of categories. Although it might be applied to the “Country” feature, however, it is not suitable for the entire dataset due to the continuous nature of the other variables.
In conclusion, the Gaussian Naive Bayes classifier is the most appropriate option for this task, considering the data's features and the visible distributions. It manages continuous data efficiently, and the given features suit the assumption of a normal distribution very well.
Naïve Bayes Model Results
The performance matrix results are as shown in figures 5 and 6, and the summary is presented in table 2.
 
Figure 5: Confusion matrix for Naïve Bayes model
The results of the confusion matrix for the Naïve Bayes model are:  True Positive (TP) = 49, True Negative (TN) = 48, False Positive (FP) = 2, and False Negative (FN) = 1.

 
Figure 6: The ROC curve for Naïve Bayes model

Table 2: The summary of performance matrices for the Naïve Bayes Model
Performance Metrics	Results
Accuracy	0.97
Precision	0.9607843137254902
Recall	0.98
F1 Score	0.9702970297029702
ROC AUC	0.9768
The same confusion matrices for both models show that they perform equally well in terms of classification accuracy. Additionally, it appears from the evaluation measures that both models perform comparably on this dataset. In terms of precision, recall, F1 score, and ROC AUC score, there might be a few minor variations.
The naïve Bayes model achieved similar results to that of logistic regression in all performance metrics except in few cases especially the ROC AUC where the naïve Bayes slightly outperformed the logistic regression with a difference of about 0.0004 approximately.
Both models achieved the same confusion matrices which show that they perform equally well in terms of classification accuracy. Additionally, it appears from the evaluation measures that both models perform comparably on this dataset. In terms of precision, recall, F1 score, and ROC AUC score, there might be a few minor variations.
The results of the logistic regression model and that of Naïve Bayes model summarized in table 3. 
Table 3: Summary of the results of logistic regression model and that of Naïve Bayes model
Performance Metrics	Results of Logistic Regression	Results of Naïve Bayes 
Accuracy	0.97	0.97
Precision	0.9607843137254902	0.9607843137254902
Recall	0.98	0.98
F1 Score	0.9702970297029702	0.9702970297029702
ROC AUC	0.9763999999999999	0.9768

vi.	Observed possible Limitations of Logistic Regression model and Naïve Bayes Model
For Logistic Regression Model:

Despite the logistic regression model's excellent performance measures, a few clear drawbacks exist:
Possibility of Overfitting: A 97% accuracy rate could point to overfitting, a situation in which the model performs remarkably well on training data but might not generalize to new data.
Class Imbalance: High recall and precision indicate a balanced dataset, however these measures may be deceptive if the dataset is unbalanced.
Interpretability: Although the results of logistic regression can be understood, the high performance metrics don't reveal anything about the significance of the features or the underlying data patterns.
Binary Limitation: The use of logistic regression is restricted to issues involving several classes because it can only handle binary outcomes.
The model assumes that the log-odds of the dependent variable and the independent variables have a linear relationship.
Outliers can impact the decision boundary, therefore it is sensitive to them.
It needs a substantial sample size in order to produce reliable and consistent results.

For the Naïve Bayes Model
Naive Bayes has drawbacks despite having excellent performance metrics. The accuracy of the model may be impacted by the assumption of feature independence, which is rarely true in real-world data. Naive Bayes can have drawbacks with correlated features, which can result in biased predictions, although high recall and precision indicate strong performance. It also presumes a normal distribution for continuous data, which may not apply in every case. The little discrepancy between accuracy and ROC AUC suggests some misclassification, particularly in cases of unbalanced data. Therefore, even while the model works well, its application to more complicated datasets may be limited because of its oversimplified assumptions, which might not capture all data intricacies.
