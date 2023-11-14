# Recipe-Cite-Traffic-Prediction

The objective of this initiative is to employ machine learning methods to anticipate popular recipes with high traffic on a recipe website. The forecasts generated will empower the website's product manager to make informed decisions, enhancing user engagement and overall website traffic.

Summary of the Project This project seeks to develop a predictive model capable of reliably recognizing recipes that are prone to attract high traffic. Through the analysis of historical data encompassing recipe attributes and traffic trends, a machine learning model will be trained to forecast the probability of a recipe gaining popularity and attracting substantial traffic. I Additionally, a performance comparison graph between Random Forest and SVC is presented.

Data Validation
This dataset has 947 rows and 8 columns.I have validated all variables and realized that "servings" variable has object type and I converted into numeric type.

recipe : numeric values without missing values, same as description. No cleaning is needed.

calories : numeric values with 52 missing values. Same as description. Cleaning is needed.

carbonhydrate : numeric values with 52 missing values. Same as description. Cleaning is needed.

sugar : numeric values with 52 missing values. Same as description. Cleaning is needed. protein : numeric values with 52 missing values. Same as description. Cleaning is needed.

category : 11 categories without missing values. Same as description. No cleaning is needed.

servings : object data with 3 missing values. Not same as description. Cleaning is needed.

high_traffic : object data with 373 missing values. Same as description. Cleaning is needed.

As there are some missing values, I needed to check the distribution of the variables with missing values to decide which handling strategy would be best. Therefore, I examined the variables 'recipe', 'calories', 'carbohydrate', 'sugar', and 'protein'. Based on the presence of outliers within the variables, especially where the distribution is right-skewed, I decided to use the 'median imputation' method.

In the 'servings' variable, there were only three NaN values. I filled those with the average value of the variable and converted them into numerical values.

For the 'high_traffic' variable, I converted NaN values into 'Not High,' as I will be using it as the target variable in my binary prediction later on.

Explatory Analysis
I have displayed four graphs in order to gain a deeper understanding of the data. In the first one, I displayed the number of recipes in each category, where breakfast has the largest number (slightly over 100), followed by chicken breast and beverages (just under 100).

In the second graph, I checked if there is a class imbalance in the data. This is crucial because it could lead to biased analysis later on. I realized that there is a 60% vs. 40% class imbalance in the 'high_traffic' variable.

In the third one, I wanted to show which recipes within categories have the highest traffic, where 'vegetable' has the biggest difference between high-traffic and low-traffic quantities, followed by 'potato' and 'pork.' This is important because it means that certain categories of foods are more popular in comparison to others.

In the last graph, I used a scatterplot matrix of nutritional ingredients, servings, and high traffic. Based on this graph, as each nutritional ingredient increases, traffic also increases. Moreover, the highest demand for servings is 4.

Model Fitting and Evaluation
Predicting high_traffic is a classification problem in machine learning, and addressing the class imbalance is crucial in this context. I've chosen to use the Random Forest Classifier as the baseline model due to its robustness and the ability to handle imbalanced data effectively. Additionally, I've employed the Support Vector Classifier (SVC) as a comparative model to as it is known for its strong performance in various scenarios, including complex, high-dimensional spaces. It can handle non-linear relationships between features and the target variable. SVC aims to find the optimal decision boundary that maximizes the margin between different classes, which can lead to better separation of classes. Moreover, SVC is particularly effective for binary classification tasks, making it suitable for the problem of categorizing recipes into "High Traffic" and "Not High" classes. Lastly, SVC allows for parameter tuning, enabling me to optimize its performance further.

For the evaluation of these models, precision for the 'High' traffic class is of paramount importance. I aim to correctly predict high traffic recipes with at least 80% precision. Precision is a critical metric in this context as it measures the accuracy of positive predictions, which directly impacts the goal of correctly identifying high-traffic recipes.

Prepare Data for Modeling
I handle the imbalanced data.

I split the data as train and test sets.

I have encoded categorical variables.

Model Comparison:
Accuracy: The Support Vector Classifier (SVC) outperforms the Random Forest Classifier in terms of accuracy, achieving an accuracy of 0.77 compared to 0.695 for Random Forest.

Precision: For the 'High' traffic class, SVC has a precision of 0.80, indicating that it correctly predicts high traffic recipes with an 80% precision rate. In contrast, the Random Forest Classifier achieves a precision of 0.70 for the same class.

Recall: SVC also exhibits a higher recall (sensitivity) for the 'High' traffic class (0.81) compared to Random Forest (0.84), meaning it captures a larger proportion of actual high traffic recipes.

F1-score: SVC has a higher F1-score for both the 'High' and 'Not High' classes, indicating a better balance between precision and recall.

Confusion Matrix: While both models have similar confusion matrix structures, SVC has a higher true positive rate (TPR) for the 'High' traffic class.

In conclusion, the Support Vector Classifier (SVC) performs better than the Random Forest Classifier in terms of accuracy, precision, and recall, making it a more suitable model for the task of predicting high traffic recipes.

I also displayed a graph which shows the performance differences among the metrics.

Business Metrics
Business Metric: Precision
Definition: Precision measures the accuracy of the model in correctly identifying recipes that will generate high traffic. It is the ratio of correctly predicted high-traffic recipes to the total number of recipes predicted as high-traffic.

Formula: precision = (True Positives) / (True Positives + False Positives)

In this metric:
True Positives (TP) are the number of recipes correctly predicted as high-traffic. False Positives (FP) are the number of recipes incorrectly predicted as high-traffic. Importance: Precision is crucial for the business as it quantifies the model's ability to precisely identify recipes that will attract a significant audience. Achieving a high precision means that when the model predicts a recipe as high-traffic, it is highly likely to be accurate. This is critical for optimizing marketing efforts, content promotion, and resource allocation.

How my Model Perform Using This Approach:
The Support Vector Classifier (SVC) achieves a precision of 0.80, indicating that it correctly predicts high-traffic recipes with an 80% precision rate. The Random Forest Classifier, while achieving a precision of 0.70, falls slightly short of the desired 80% precision target for predicting high-traffic recipes.

The SVC model outperforms the Random Forest Classifier in terms of precision. This means that when the SVC predicts a recipe as high-traffic, it is more likely to be accurate compared to the Random Forest model. For the business, this implies that the SVC model is better at identifying recipes that will generate high traffic and, therefore, is a more suitable choice for recipe recommendation and promotion.

Recommendations:
Model Deployment: Deploy the trained Support Vector Classifier (SVC) model into the production environment to predict high traffic recipes.

Monitoring: Continuously monitor the model's performance in the production environment to ensure it maintains the desired level of precision for predicting high traffic recipes. Set up alerts for any significant deviations from the target precision.

Retraining: Periodically retrain the model with new data to keep it up-to-date and adapt to changing patterns in recipe popularity.

Feedback Loop: Establish a feedback loop with users or recipe consumers to gather insights and feedback on recipe preferences and traffic. This feedback can be used to enhance the model and improve recipe recommendations.

Exploratory Analysis: Conduct further exploratory analysis to understand factors influencing recipe popularity, which can provide valuable insights for recipe creation and promotion.

Marketing Strategy: Utilize the insights from the analysis to inform marketing and promotion strategies for recipes in different categories.

Content Generation: Invest in content generation for recipes in categories that show high potential for popularity based on the analysis, aiming to increase the number of high-traffic recipes.

Customer Engagement: Engage with customers through surveys, ratings, and feedback mechanisms to understand their preferences better and tailor recipes accordingly.

Data Quality: Ensure data quality by regularly auditing and cleaning the dataset to maintain the accuracy and reliability of the model.

Ethical Considerations: Be mindful of ethical considerations related to data privacy and bias when collecting and using data for recipe recommendations.

In conclusion, the Support Vector Classifier (SVC) is recommended for deployment as it excels in identifying high-traffic recipes with the desired precision. Continuous monitoring, retraining, and user feedback are essential for maintaining and improving the model's performance over time. This approach will enable the business to maximize recipe visibility and engagement, ultimately leading to increased user satisfaction and business success.
