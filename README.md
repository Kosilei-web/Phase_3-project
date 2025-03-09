          Syriatel Customer Churn classification Project 
                           
                        Overview

This binary classification project focuses on conducting a churn analysis for SyriaTel, a telecommunications company based in Syria. 
Syriatel's major challenge is losing customers leading to revenue loss, negative brand perception and increased acquisition costs. It aims at reducing customer churn (customers leaving the network). The management would like to understand the factors that drive churn and create a model that predict it accurately hence helping Syriatel take targeted actions to retain valuable customers. This project aims to develop a machine learning model to predict whether a customer is likely to churn based on various usage patterns, demographic data, and service-related factors.
                        
                       Goal of the project
                     
The goal is to create a machine learning model capable of predicting the likelihood of a customer discontinuing a service, as well as identifying the factors contributing to this churn.
                            
                      Objectives
                      
•	To build a classifier to determine if a customer would ‘soon’ leave SyriaTel,
•	To Identify Customers at High Risk of Leaving Syriatel.
•	To Determine Key Churn Factors.
•	To Identify Reasons for Customer Churn.
•	To Develop a Predictive Churn Model.
•	To Evaluate and Compare Model Performance.
•	To Implement a Churn Prevention Action Plan.
•	To Design Effective Retention Strategies.
•	To Monitor and Measure Plan Effectiveness.
                          
                    Data Exploration

This project uses the SyriaTel Customer churn data set which is retrieved from Kaggle: https://www.kaggle.com/datasets/becksddf/churn-in-telecoms-dataset. The data used has been sourced from Kaggle. The dataset contains a record of 3333 rows and 21 columns (4 are categorical and 17 are numerical) containing different features.
                     
                   Data Cleaning and analysis
              
I examined the dataset to identify any instances of missing or null values and duplicates but there were not missing values and duplicates. I did Univariate, Bivariate and Multivariate analysis to provide a comprehensive understanding of the dataset, uncover underlying patterns and relationships, and inform further modeling and decision-making processes.
                      
                  Univariate Analysis
 ![Alt Text](https://github.com/Kosilei-web/Phase_3-project/blob/main/Univariate%20analysis.png?raw=true)

Account Length: The distribution is positively skewed, indicating that most customers have shorter account lengths. This could lead to potential challenges in churn prediction, as shorter account lengths are more prevalent, but longer account lengths might serve as more significant indicators of customer retention or churn behavior.
Number of Voice Mail Messages: The distribution is relatively even, suggesting that this feature doesn't have a strong predictive power for churn. The lack of variation in voice mail usage may limit its utility in differentiating between customers who are likely to churn versus those who are not.
Total Day Minutes, Calls, and Charge: These features exhibit a positive skew with significant overlap between churned and retained customers. This suggests that while most customers have moderate usage during the day, there is a considerable overlap between the two groups, introducing noise in churn predictions. More advanced techniques or transformations might be necessary to better capture patterns in this data.
Total Evening Minutes, Calls, and Charge: Similar to the Day features, the distribution is positively skewed and shows significant overlap between churned and retained customers. This further reinforces the idea that the evening usage patterns are not easily distinguishable between the two groups, adding noise that might reduce the effectiveness of these features in predicting churn.
Total Nighttime Minutes, Calls, and Charge: The negative skew in these distributions suggests that most customers have lower activity during nighttime hours. Higher nighttime usage could serve as a more reliable predictor for churn, as customers with higher nighttime activity might be more engaged or dependent on their service, potentially indicating higher loyalty or retention.
Total International Minutes, Calls, and Charge: These features share similar distributions to the Total Day features, with a positive skew and significant overlap between churned and non-churned customers. The overlap between classes introduces noise, which might require additional feature engineering or a more refined model to extract meaningful predictive signals

             Bivariate Analysis
 ![Alt Text](https://github.com/Kosilei-web/Phase_3-project/blob/main/Box%20plot.png?raw=true)
The analysis above suggests that contract terminations are more frequent in area codes 415 and 510, based on the boxplot.
Modelling
To achieve the stated goals outlined in the project proposal, we intend to utilize various machine learning algorithms in combination. The projects used the following Binary classifiers
•	Logistic Regression 
•	Decision Trees 
•	Random Forest
During the evaluation of our model performances, we will utilize the ROC_AUC metric as a crucial evaluation criterion. The ROC_AUC metric is particularly suitable for binary classification tasks, as it offers a comprehensive assessment by considering both sensitivity and specificity across different threshold levels. This metric provides a robust indication of the model's capability to distinguish between classes.
                        
            Logistic Regression
            
The model showcased good accuracy (86% on train & test) The model is performing consistently on both sets, which is a good sign. There is no major overfitting, as train and test accuracies are similar.
Lower AUC Score (0.71 on test) 0.71 is good but indicates some difficulty in distinguishing between churners and non-churners. Since AUC is lower than accuracy, the model might be biased toward the majority class (e.g., predicting "No Churn" too often). Looking at the confusion matrix, the model gets most of the predictions right, both when it predicts something is positive and when it predicts something is negative. This suggests that the model is reliable and doesn't make too many mistakes. It's good at classifying both positive and negative cases accurately.                       
  
           Decision Trees
  
The accuracy of the model is 90.25%, indicating that it correctly classifies most of the samples.
The precision of the model is 63.15%, this means that, when the model predicts churn, it is correct 63% of the time, suggesting some false churn predictions.
The recall of the model is 75.79% shows that the model successfully identifies 75.79% of actual churners, making it effective at detecting churn but at the cost of misclassifying some non-churners.
The F1 score, which combines both precision and recall, is 68.9%, representing the balance between precision and recall.
In summary, this model performs well overall with 90.25% accuracy, but it leans more towards detecting churn cases (high recall: 75.79%) rather than making precise churn predictions (moderate precision: 63.16%). This means the model successfully captures most churners but also misclassifies some loyal customers as churners. The F1-score (68.90%) indicates a good balance between precision and recall.
The AUC-ROC score of 0.842 indicates that the model effectively distinguishes between churners and non-churners, correctly ranking them 84.2% of the time. This falls into the "very good" range (0.8–0.9), meaning the model has strong classification ability.
   
           Random Forest
   
The model correctly classifies 94.9% of all instances in the dataset. High accuracy suggests that the model is performing well
Precision (93.51%) Out of all predicted churners (Class 1), 93.51% were actual churners. High precision means fewer false positives
Recall (71.29%) The model correctly identified 71.29% of actual churners. A lower recall suggests the model misses some churners (false negatives).
F1-score (80.90%) Balances precision and recall. A high F1-score (0.81) means a good trade-off between catching churners and avoiding false positives.
  
          Model comparison
          
  ![Alt Text](https://github.com/Kosilei-web/Phase_3-project/blob/main/AUC%20curve.PNG?raw=true)
Based on the AUC scores, the Decision Tree model (AUC = 0.98) appears to be the best at distinguishing between churners and non-churners. However, this might indicate overfitting, meaning the model performs well on the test data but might not generalize well to new data.
The Random Forest model (AUC = 0.93) also performs strongly and is likely more stable since it reduces overfitting by averaging multiple decision trees.
Meanwhile, Logistic Regression (AUC = 0.78) has the lowest AUC, suggesting it may not be capturing complex relationships in the data effectively.
While Decision Tree shows the highest performance, Random Forest is the safer and more generalizable choice.
                           
           Conclusion
                           
Based on the findings, the business conclusion is as follows:
•	Emphasis on Recall: In the realm of predicting customer churn, priority was given to optimizing for Recall. This strategy aimed to minimize the misclassification of churners as non-churners, ensuring that the model effectively identifies customers at risk of leaving.
•	Optimal Model: Among the explored models, the Random Forest classifier stood out as the top performer,
•	Key Churn Influencers: Factors such as total day charge, customer service calls, and the number of voice mail messages emerged as significant contributors to customer churn.
•	With additional time, there's an opportunity to conduct a thorough exploration of potential features and their influence on the model. This may involve analyzing customer behavior, transaction patterns, or other relevant variables that could contribute valuable information for predicting churn.
•	Continuous Improvement: Predicting customer churn is an ongoing endeavor, necessitating constant refinement of the model. Regular monitoring, data collection, and incorporating feedback from stakeholders are crucial for enhancing predictive accuracy and identifying at-risk customers effectively.

