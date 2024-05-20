# ML_Classification_Health-Insurance-Cross-Sell-Prediction
![Health Insurance](https://github.com/Sachinvt/ML_Classification_Health-Insurance-Cross-Sell-Prediction/assets/140580938/266b032a-1792-4933-b517-8bff697c3dcd)

# Project Summary
The insurance industry relies on understanding and managing risk. One way insurance companies do this is by assessing whether their existing health insurance policyholders may also be interested in purchasing vehicle insurance. To optimize their business model and revenue, an insurance company wants to predict customer interest in vehicle insurance based on various customer demographics and policy-related factors.

Insurance policies are essentially agreements in which a customer pays a premium to an insurance company in exchange for a guarantee of compensation in the event of specified loss, damage, illness, or death. For example, a health insurance customer pays an annual premium, and in return, the insurance company agrees to cover medical expenses up to a certain amount. The key to how insurance companies can afford to do this lies in the concept of probabilities and risk sharing among policyholders. Not every policyholder will make a claim in a given year, and by pooling premiums from many customers, the insurance company can manage the financial risk.

In this context, the challenge is to build a predictive model to determine whether existing health insurance policyholders would also be interested in purchasing vehicle insurance. Such a model would help the company tailor its communication strategies to reach out to potential customers and optimize its revenue.

The information available for building this predictive model includes:

**Demographics:** This includes information about the customer's gender, age, and region code type. Demographics can be crucial in understanding customer behavior and preferences.

**Vehicle Details:** The age of the customer's vehicle and whether it has been damaged or not are essential factors to consider. Newer vehicles might be more appealing for insurance coverage, and the condition of the vehicle affects the risk.

**Policy Information:** This covers details such as the premium amount the customer pays and the sourcing channel through which they obtained the insurance. Premiums and the way policies are sourced can impact a customer's likelihood to consider additional insurance.

By analyzing and leveraging this data, the insurance company can create a predictive model that identifies patterns and relationships between these factors and a customer's interest in vehicle insurance. Machine learning and data analytics can be powerful tools for this task, enabling the company to:

**Segment Customers:** The model can group policyholders into segments based on their likelihood to be interested in vehicle insurance. For example, it may identify a group of customers with a high probability of interest.

**Tailor Marketing Strategies:** Once customer segments are defined, the insurance company can design and implement targeted marketing and communication strategies for each segment. This ensures that efforts and resources are directed where they are most likely to yield positive results.

**Optimize Revenue:** By successfully identifying potential customers for vehicle insurance, the company can increase its revenue by expanding its customer base and offering additional policies to interested policyholders.

In conclusion, building a predictive model to determine customer interest in vehicle insurance is a valuable strategic initiative for the insurance company. It allows them to leverage their existing customer base, improve customer satisfaction, and grow their business. Using data-driven insights, the company can make informed decisions and tailor their approach to each customer, ultimately benefitting both the company and its policyholders.

# Problem Statement
An insurance company seeks to enhance its business model and revenue by predicting customer interest in vehicle insurance among their existing health insurance policyholders. The goal is to develop a predictive model that can identify which policyholders are likely to consider purchasing vehicle insurance. This model will help the company segment policyholders and inform targeted marketing and communication strategies, ultimately optimizing revenue and increasing customer engagement by offering relevant insurance products to interested policyholders.

# About the Data:
comprehensive dataset containing demographic information, vehicle details, and policy-related data for each customer. The dataset includes 381,109 rows and 12 columns with no missing or duplicate values.

# Data Preprocessing:
Nearly all customers possess a driver's license, which provides limited predictive value and will be excluded from the analysis. Outliers in the Annual_premium variable is addressed using interquartile range capping and flooring.
Preprocessing Steps:
•	**Categorical Encoding:** Apply label encoding to ordinal categorical variables.
•	**Outlier Treatment:** Use interquartile range capping and flooring for the Annual_premium variable.
•	**Class Imbalance:** The dataset exhibits significant class imbalance, with 340,000 "No" responses and 50,000 "Yes" responses. I use random oversampling technique to address this imbalance.
By addressing these preprocessing steps, we ensure the data is well-prepared for developing a robust predictive model.

# Exploratory Data Analysis:
After conducting EDA, it appears that the target audience for insurance companies may primarily consist of middle-aged individuals and teenagers. Middle-aged individuals could be potential customers for various insurance products, while teenagers, who already have insurance coverage and prior experience, may represent an opportunity for additional insurance offerings. This analysis suggests that focusing marketing efforts on these age groups could be an effective strategy to generate more leads for insurance companies.

# Data Preparation:
In the given dataset, there is a significant class imbalance with the "No" category having 340,000 counts and the "Yes" category having 50,000 counts. This imbalance can lead to biased predictive models. Random oversampling is a technique used to address class imbalance by increasing the number of minority class samples. This is achieved by randomly duplicating minority class examples until the classes are balanced.
Choosing a 70:30 split ratio for training and testing data balances the need for a substantial training set with a reasonable evaluation set. Using 70% of the data for training enhances the model's ability to learn complex patterns and relationships, creating a more robust model. The 30% testing set, while smaller, still provides an adequate evaluation of the model's performance, ensuring it generalizes well. This approach is particularly beneficial when dealing with limited data, as it maximizes the data available for training while still allowing for effective performance assessment.

# Model Selection:
Developed baseline models like logistic regression achieved an accuracy of 78.56%. Further experimentation with complex models, such as XGBoost and Random Forest, significantly improved performance. The Random Forest model, in particular, yielded impressive metrics: Recall (0.9943), Precision (0.8800), F1 Score (0.9337), Accuracy (0.9292), and ROC AUC Score (0.9291. Given the significant improvement in accuracy and AUC ROC score with Random Forest, we selected it as our final model.

# Model Training:
I optimize model parameters using grid search techniques to enhance performance. For example, in a Random Forest model, hyperparameters such as max_depth, n_estimators, and min_samples_split can be tuned. Cross-validation is employed to ensure robustness of the model by splitting the data into multiple subsets for training and evaluation. Additionally, feature selection techniques like Recursive Feature Elimination (RFE) or Principal Component Analysis (PCA) can be applied to improve model efficiency and reduce overfitting.

# Model Evaluation:
I assess model performance using several key metrics:
AUC-ROC: Suitable for imbalanced datasets, it gauges the model's ability to distinguish between classes effectively.
Recall: Crucial in scenarios where missing positive instances incurs high costs, like in healthcare, it measures the model's ability to capture true positives.
Precision: Important when the cost of false positives is high, such as in scenarios involving monetary incentives, it gauges the proportion of true positives among predicted positives.
F1-score: Balancing precision and recall, it offers a unified measure of the model's performance, particularly beneficial for imbalanced datasets.
Accuracy: While a common metric, its usefulness depends on dataset balance; higher accuracy indicates a greater proportion of correct predictions across all classes.
Random forest, with its significant performance metrics, emerged as the best model choice.

# Feature Importance:
The correlation heatmap revealed key insights into feature importance, particularly in Random Forest models. By analysing how each feature contributes to reducing impurity within decision tree nodes, we identified significant contributors to predictive accuracy. Notably, independent features like Vintage, Annual_Premium, Vehicle_damage, and Previously_Insured displayed high importance with respect to target variables. Leveraging Scikit-Learn's feature importance scoring method, I gained valuable insights into the crucial role of these features in our predictive model.

# Conclusion
In this analysis, we began by loading our dataset and conducting initial data quality checks. Fortunately, we found no duplicates or missing values, so there was no need for data cleaning.

Exploratory data analysis revealed several key insights:

**Gender Distribution:** The dataset showed a nearly even distribution of gender, with a slightly higher representation of males. The likelihood of purchasing vehicle insurance was also slightly higher among males.

**Interest in Vehicle Insurance:** Only 12.3% of individuals in the dataset expressed interest in purchasing vehicle insurance, while 87.7% were not interested. This suggests a need for effective marketing strategies and competitive pricing to attract more customers and generate leads.

**Driving License (DL):** 99.8% of customers in the dataset held a driving license, while 0.2% did not. Only 12.2% of individuals with a driving license were interested in purchasing vehicle insurance, indicating a possible need for awareness campaigns or competitive offers.

**Prior Insurance History:** About 45.8% of individuals had previous insurance, and among them, 12.2% were interested in purchasing insurance again. This indicates that individuals are willing to pay premiums for risk reduction, especially when there is a significant probability of loss.

**Vehicle Age:** Vehicle age varied, with approximately 4.2% of vehicles being older than two years, 52.6% between one and two years, and 43.2% less than a year old. Interest in purchasing vehicle insurance increased as the vehicle's age exceeded one year, suggesting a correlation between age and the willingness to buy insurance.

**Vehicle Damage:** About 50.5% of the vehicles in the dataset had past damage, and 12.0% of individuals with previously damaged vehicles were interested in acquiring vehicle insurance. This suggests that people with damaged vehicles tend to be more aware of insurance policies and benefits.

**Age Groups:** The dataset had a diverse range of ages, with higher interest in purchasing vehicle insurance among individuals aged 40 to 60. Middle-aged individuals (40-60) showed the highest interest, with 9.3% interested in purchasing insurance.

After the initial data analysis, we proceeded with data preprocessing, including handling outliers and feature encoding. The dataset was split into train and test sets. Six machine learning algorithms were employed to predict customer interest in purchasing vehicle insurance. Additionally, hyperparameter tuning was applied to three models to identify the best-performing model.

The two most influential features in the models were vehicle damage and annual premium. Decision Tree and Random Forest models stood out with ROC AUC scores of 93% and 92%, respectively, outperforming the other algorithms. The conclusion is that these models are well-suited for predicting customer interest in vehicle insurance.

In summary, this analysis revealed valuable insights into the dataset and identified potential target demographics for insurance companies. Additionally, by employing machine learning models, we can make predictions that can assist insurance companies in generating leads and tailoring their marketing strategies. Decision Tree and Random Forest emerged as the top-performing models, demonstrating their effectiveness in this predictive task.

# Future Scope:
Future research could explore advanced ensemble techniques, such as gradient boosting and stacking, to potentially improve model performance further. Additionally, conducting feature engineering to derive new meaningful features or leveraging external datasets could enhance the predictive power of the models. Furthermore, implementing real-time data integration and deploying the models in a production environment for continuous monitoring and updating would be valuable for ensuring the models' effectiveness over time.
In summary, this analysis revealed valuable insights into the dataset and identified potential target demographics for insurance companies. Additionally, by employing machine learning models, we can make predictions that can assist insurance companies in generating leads and tailoring their marketing strategies. Decision Tree and Random Forest emerged as the top-performing models, demonstrating their effectiveness in this predictive task.
