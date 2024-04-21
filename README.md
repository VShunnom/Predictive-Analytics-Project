# Predictive-Analytics-Project

Predicting the Likelihood of Heart Attack

1.	Business Question and Case

1.1.	 Business Question
What are the key risk factors contributing to heart disease and what targeted intervention programs can reduce healthcare costs?
1.2.	Business Case
According to the Centers for Disease Control and Prevention (CDC), heart disease is a global health concern, accounting for approximately 31% of all deaths worldwide. In the United States alone, over 600,000 people die from heart disease each year, making it the leading cause of death for both men and women1. Despite significant advancements in medical technology, many heart attacks are still unpredictable, leading to delayed treatment and increased mortality rates. By identifying the key risk factors associated with heart disease, healthcare providers and insurance companies can design targeted intervention programs to mitigate risks and reduce costs. In fact, Early detection and treatment of heart disease have been demonstrated to decrease the need for expensive interventions like bypass surgery, resulting in significant cost savings of up to $1.5 billion annually, according to a report by the American College of Cardiology in 20172. 
The value proposition of this project is to provide actionable insights to healthcare providers and insurance companies, enabling them to make informed decisions and optimize their resources.

2.	Analytics Question
What is the effect of patient characteristics, such as age, chest pain type (cp), cholesterol levels (chol), maximum heart rate achieved (thalach), and the number of major vessels colored by fluoroscopy (ca) on the likelihood of heart disease? And to what extent do these factors influence the presence of heart disease?
Our analytical question aims to identify the most influential factors contributing to heart disease by examining the relationships between patient characteristics, listed in the analytical question. Key predictors include the aforementioned patient characteristics, which are a mix of numeric, categorical, and binary variables.
Our primary goal for the project is predictive accuracy. This enables informed decisions on prevention, risk management, and personalized treatments while ensuring a comprehensive understanding of factors associated with heart disease.

3.	Data Set Description
The "Heart Disease UCI dataset” is from Kaggle.com and contains information on 303 patients and their characteristics associated with heart disease. The dataset includes 14 quantitative, binary, continuous, and categorical predictors, capturing essential patient characteristics such as age (in years), resting blood pressure, serum cholesterol (in mg/dL), maximum heart rate achieved,thalach (in bpm), and oldpeak (ST depression induced by exercise relative to rest). The categorical variables included sex, chest pain type (typical angina, atypical angina, non-anginal pain, asymptomatic), fasting blood sugar (greater than or equal to 120 mg/dL or less than 120 mg/dL), exercise-induced angina (yes or no), and resting electrocardiographic results show whether the patient had normal or abnormal results, number of major vessels colored by fluoroscopy, and thalassemia represents the blood disorder. The outcome variable of interest is a binary classification variable indicating whether the patient was diagnosed with heart disease.  
Data source: https://www.kaggle.com/datasets/nareshbhat/health-care-data-set-on-heart-attack-possibility )
4.	Descriptive Analytics

4.1 Descriptive Statistics of Key Variables

Visual and Classification Analytics: Again, our outcome variable for this heart disease analysis is the presence or absence of heart disease, a binary classification. The distribution of the outcome variable is relatively balanced, with 55.5% of individuals having heart disease and 45.5% not having heart disease.
Initial descriptive analysis focused on important predictors highlighted above in the "Analytics Question" and "Dataset Description. The dataset contains 207 males (68.3%) and 96 females (31.7%). For chest pain type, 47.2% of the cases are typical angina, while 29.0% are non-anginal pain, 16.5% are atypical angina, and 7.3% are asymptomatic. Regarding resting ECG results, 50.5% are normal, 49.2% have ST-T wave abnormality, and 0.3% show probable or definite left ventricular hypertrophy.
Fig.2, there is a moderate positive correlation between age and resting blood pressure (0.279), indicating that older individuals tend to have higher resting blood pressure. Furthermore, there is a negative correlation between the maximum heart rate achieved and age (-0.399), suggesting that younger individuals typically have a higher maximum heart rate. Also, the outcome variable (presence of heart disease) is negatively correlated with maximum heart rate achieved (r = -0.4) This suggests that higher maximum heart rates tend to be associated with a lower likelihood of heart disease and positively correlated with age (r = 0.2), resting blood pressure (r = 0.15), and oldpeak (r = 0.43).
The ANOVA test results show significant differences in the presence of heart disease across sex (F value: 25.79, P-value: < 0.001), chest pain type (F value: 69.77, P-value: < 0.001), and exercise-induced angina (F value: 70.95, P-value: < 0.001). However, the fasting blood sugar level (P-value: 0.627) and resting electrocardiographic results (P-value: 0.0168) show less significance in differentiating heart disease presence.
Box Plot and Chi-square tests indicate that the presence of heart disease varies by chest pain type (highest in atypical angina), sex (higher in males), and resting electrocardiographic results (higher in those with ST-T wave abnormality). Other categorical variables, like fasting blood sugar (fbs) and exercise-induced angina (exang), do not show significant associations with the presence of heart disease.
Finally, an initial observation that older individuals seem to have a higher prevalence of heart disease led to a chi-square test between age groups (younger than 50, 50-60, 61-70, and older than 70) and heart disease presence. A significant chi-square test result confirms dependence between age group and heart disease presence.

4.2 Data Pre-Processing and Transformations: 
	The data sourced has been preprocessed and there were no omitted values.

	4.3 Initial Set of Predictors:
The initial set of predictors for the heart disease classification model was chosen based on domain knowledge and factors generally considered to influence heart disease risk. These predictors include age(in years), as older individuals are generally more prone to cardiovascular issues; sex, as males and females may have different heart disease risks; chest pain type, which can indicate varying levels of heart disease risk; resting blood pressure (in mmHg), a known risk factor for heart diseases; serum cholesterol, which can contribute to the development of arterial plaque; fasting blood sugar, which may be associated with increased heart disease risk; resting electrocardiographic results, which can indicate potential heart issues; maximum heart rate achieved, as a lower rate might suggest decreased heart adaptability to physical stress; and exercise-induced angina, which could be a sign of underlying heart issues due to insufficient oxygen-rich blood during physical activity.


5.	Modeling Methods and Model Specifications

5.1.	Initial Logistic Regression Modeling
A logistic regression model fit using the 13 predictors for heart disease produced significant estimates, indicating that the model is better at predicting heart disease than the null model. Significant predictors at the .05 significance level include sex, chest pain type (cp), maximum heart rate achieved (thalach), exercise-induced angina (exang), ST depression induced by exercise relative to rest (oldpeak), number of major vessels colored by fluoroscopy (ca), and thalassemia type (thal).
 Initial Logit Model Results
The logistic regression analysis found that the coefficients for sex, cp, thalach, exang, oldpeak, ca, and thal are statistically significant at the 5% level, indicating that these variables are significantly associated with the presence of heart disease. The accuracy of the model is reported as 0.836, indicating that the model can correctly predict the presence or absence of heart disease in approximately 85% of cases. Additionally, there is a notable reduction between the null and residual deviance (49.3%), suggesting that the model is a good fit for the data. Overall, these results suggest that the logistic regression model can identify significant predictors of heart disease and has a reasonable level of predictive accuracy.
5.2.	Logistic Regression Assumptions (Second Set of Predictors)
The stepwise logistic regression model used a smaller set of significant predictors, leading to improved model performance. With the smaller set of predictors, the condition index has dropped to 47.33, indicating acceptable levels of multicollinearity in this specification (XI). Additionally, the highest Variance Inflation Factor (VIF) is 1.49, which is well below the threshold of concern, suggesting that multicollinearity is not a problem for this specification (XI). The accuracy of the stepwise model is 0.852, indicating that it performs well in predicting the presence of heart disease.

5.3.	Model Specification Candidates and Rationale
The first model specification used in this exercise was the initial set of 13 predictors selected based on domain knowledge and clinical understanding. The second model specification was selected using stepwise variable selection at p-value threshold of .05 to include only the most significant predictors. The full model for this variable selection exercise included all predictors. The lower bound was the null model plus “age,” a variable whose inclusion was based on intuition and the positive relationship between it and the outcome variable, regardless of its significance. Stepwise variable selection refined our second specification down to 11 predictors: age, sex, chest pain type (cp), resting blood pressure (trestbps), resting electrocardiographic results (restecg), maximum heart rate achieved (thalach), exercise-induced angina (exang), ST depression induced by exercise relative to rest (oldpeak), slope of the peak exercise ST segment (slope), number of major vessels colored by fluoroscopy (ca), and thalassemia type (thal). All predictors are significant at the .05 significance level except for age and restecg. Due to the variable selection resulting in a subset of predictors, we will refer to this specification as the "small" subset of predictors or specifications.

5.4.	Methods Evaluated:
First, we began our analysis by examining a logistic regression model for our classification, then examined the problem using the stepwise set of predictors. This initial model served as a baseline to compare the performance of more advanced methods that followed.
Next, we examined both random forests and boosted tree models for our classification problem using the same full and stepwise set of predictors. These ensemble methods were chosen to improve predictive accuracy, reduce overfitting, and extract a clearer understanding of which predictors are most "important" in predicting the presence of heart disease. 
5.5.	Cross-Validation Testing and Final Model Selection
In all six combinations of model and specification, we evaluated six different combinations of models and specifications. For each combination, we computed the confusion matrix and assessed the model performance using Accuracy, Sensitivity, ROC, and AUC.
For the logistic regression models, we used the glm function with type = "response" to predict the outcomes and calculate the confusion matrix. We then employed the ROCR package to analyze the AUC and ROC. Interestingly, both the full and reduced logistic models displayed the same sensitivity of 0.97, AUC of 92.7%, and an accuracy of 83.6%.
We also fitted a random forest model for the full dataset, which yielded the following results: an accuracy of 82%, AUC of 94.3%, and sensitivity of 76% for the reduced model. The random forest model with fewer predictors had an accuracy of 83.8%, AUC of 92.9%, and sensitivity of 80%.
Lastly, we evaluated the boosted tree models. The reduced model demonstrated an accuracy of 81.9%, the sensitivity of 97.2%, and AUC of 95%. The full model yielded similar results, with an accuracy of 80.3%, sensitivity of 97.2%, and AUC of 95%.
	
5.6	Final Method/Specification Selected:
Based on the parameters we used for the comparison of the three models, the small model of the boosted trees yielded the best results with an accuracy of .819, sensitivity of 0.972 and area under the curve of 0.95. From the plot, we also see that the graph hugs the top left corner and tends towards the value of 1. 
It is worth noting that We adjusted the tuning parameters for the confusion matrix to 0.3 to encourage the model to classify more positives. Additionally, we set the number of trees to 500, considering the small size of our dataset. To address degrees of freedom issues arising from the limited data points, we allocated 80% of the data for the training set during the partitioning process.
6.	Analysis of Results
The model demonstrates a strong ability to accurately predict patients with a likelihood of heart disease, achieving an accuracy of 82%, which surpasses the threshold for a good model. Moreover, the model exhibits high sensitivity, indicating its effectiveness in classifying patients at risk of heart attacks, which is our primary objective. 
Interestingly, the random forest and boosted tree models identified chest pain (cp), the number of major vessels colored by fluoroscopy (ca), Thalium stress test results (thal), and ST depression induced by exercise relative to rest (old peak) as the most significant contributors to reducing the %MSE. These variables play a crucial role in enhancing the predictive performance of the model for heart disease risk.
	
7.	Conclusions and Lessons Learned

7.1.	Conclusions from the Analysis

Based on our model, the most significant factors contributing to heart attacks include chest pain (cp), the number of major vessels colored by fluoroscopy (ca), Thalium stress test results (thal), ST depression induced by exercise relative to rest (old peak), and maximum heart rate achieved (thalach). Interestingly, age, which was not initially considered significant but was included based on domain knowledge, emerged as the 6th most influential contributor to the reduction of %MSE. Factors such as fasting blood sugar (FBS), sex, and cholesterol trailed far behind in importance.

The variable importance plots from both the boosted trees and random forest models support the conclusion that these predictors are the primary factors influencing the likelihood of heart attacks. The model's purpose is to assist medical institutions in addressing the increasing number of deaths resulting from heart attacks and to save billions in medical expenses. With access to more data, we anticipate even further improvement in the model's predictive power.




 
