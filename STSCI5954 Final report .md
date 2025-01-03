﻿Analyzing U.S. Colleges and Universities Data for Strategic Insights
Consulting Group Transformy: Tiancan Wang
Xiaoying Meng, Yinghan Xia, Yuke Zhao, Zixing Zeng
Cornell University
STSCI 5954
Prof. Sreyoshi Das
Dec 14th, 2024
________________
Abstract
This report analyzes data from 777 U.S. colleges and universities to explore the impact of institutional characteristics, such as public/private status and student services, on key performance metrics like application rates, graduation rates, and alumni donations. Employing exploratory data analysis and predictive modeling, the study classifies institutions as elite or non-elite. Random Forest, the best-performing model, achieves superior accuracy and ROC AUC compared to Logistic Regression. Key insights include the significance of out-of-state tuition, academic reputation, and student support services in enhancing institutional outcomes. Recommendations include targeting high-achieving students, increasing international enrollment, and investing in infrastructure to optimize performance and strategic positioning.

Introduction
The key question of this project is: How do institutional characteristics such as public/private status, academic reputation, and student services impact key performance metrics, including application rates, graduation rates, and alumni donations, for U.S. colleges and universities? Based on the key performance metrics, we are able to classify institutions into elite or non-elite categories to evaluate their outcomes more effectively. This analysis is crucial because it provides actionable insights that have the potential to directly benefit students, enhance institutional strategies, and positively impact the broader education sector.

To address this question, we analyze a dataset of 777 U.S. colleges and universities. This analysis involves exploratory data analysis (EDA), predictive modeling, and the evaluation of relationships between variables. We leverage EDA to uncover patterns and relationships within the dataset. In addition, we use predictive modeling techniques to distinguish elite institutions and quantify the factors contributing to their success. Random Forest is identified as the best-performing model, outperforming Logistic Regression in both accuracy and ROC AUC, indicating its superior ability to capture complex relationships between features and target variables. 

Our findings, based on a combination of institutional and performance metrics, will be presented with clear and compelling visualizations, along with data-driven recommendations to guide strategic decision-making. The suggested actionable strategies for colleges include increasing the enrollment of high-GPA students and international students to boost tuition revenues, improving student services and infrastructure to enhance outcomes, and fostering higher acceptance and enrollment rates to cultivate future alumni donations. These insights provide a robust foundation for institutions seeking to optimize their performance and strategic positioning.

Literature/Background
Previous research has established a strong connection between institutional characteristics and key performance metrics. For instance, Bastedo and Bowman found that favorable rankings in widely recognized publications, such as U.S. News & World Report, significantly enhance an institution's reputation. This enhanced reputation often leads to an increase in applications and, consequently, higher alumni contributions. Such findings underscore the importance of academic reputation in driving institutional success.

Further studies in this field suggest that some other factors—including institutional type (e.g., public or private), academic reputation, and the quality of student services—also have a substantial influence on key metrics respectively. These metrics, in turn, contribute to an institution's ability to attain or maintain elite status.
Building on these foundational works, our research incorporates additional independent variables to explore the nuances of these relationships. By integrating more quantitative factors, we aim to provide a deeper, data-driven understanding of what distinguishes elite institutions from their peers, offering a more comprehensive perspective on institutional performance.

Data
We examined a data set containing variables from 777 institutions across the United States. We downloaded it from https://www.statlearning.com/resources-second-editio.
The dataset includes 18 variables, which capture various characteristics of higher education institutions. Key variables include Apps, representing the number of applications received; Accept, the number of applications accepted; and Enroll, the number of students enrolled. Variables such as Top10perc and Top25perc denote the percentage of new students in the top 10% and 25% of their high school class, respectively. Financial metrics like Outstate (tuition for out-of-state students), Room.Board (room and board costs), and Expend (instructional expenditure per student) are expressed in USD. The PhD and Terminal variables measure the percentage of faculty with PhD or terminal degrees. Lastly, the Private variable is categorical, indicating whether the institution is private (Yes) or public (No).
The dataset comprises 777 observations with no missing values. Among the 18 variables, 17 are numeric, and one is categorical. The categorical variable, Private, contains 565 "Yes" values (private institutions) and 212 "No" values (public institutions). This dataset highlights three primary dependent variables of interest: application rates (Apps), graduation rates (Grad.Rate), and alumni donation percentages (perc.alumni). The remaining 15 variables are treated as independent variables to model their impact on the dependent variables.

<img width="580" alt="Screenshot 2025-01-03 at 13 35 28" src="https://github.com/user-attachments/assets/4c867eb6-434d-466e-87de-2b12bfea59b9" />

Figure 1: statistics table  

To prepare the dataset for analysis, a series of data preprocessing steps were undertaken. 
First, missing values were examined, and it was confirmed that the dataset contained no missing entries across its 777 observations, eliminating the need for imputation or data removal.
Outlier detection and correction were then performed. A single outlier was identified in the Grad.Rate variable, where a graduation rate exceeded the logical maximum of 100%. This value was corrected by capping it at 100 to maintain consistency and accuracy in the data.
Finally, data normalization was applied to standardize the numeric variables. All numeric values were scaled to fall within the range of 0 and 1 using min-max normalization. This step ensured that variables with different scales contributed equally to the analysis, enhancing the reliability of the models.
These preprocessing measures ensured the dataset was clean, consistent, and ready for further analysis.

Methods
In this project, we applied two machine learning models, Random Forest and Logistic Regression, to classify U.S. colleges and universities as "elite" or "non-elite" based on various institutional features. The selection of these methodologies was guided by the need to uncover meaningful patterns within the dataset while balancing predictive robustness with interpretability. Random Forest, an ensemble learning method, was chosen for its ability to construct multiple decision trees and output the most frequent class prediction, allowing it to capture complex, non-linear relationships between variables and maintain resilience to overfitting. Logistic Regression, a linear model for binary classification, was included for its simplicity and interpretability, enabling a clear understanding of the relative influence of predictors on the target variable.

The target variable for this analysis was "Elite Status," a binary label indicating whether an institution was considered elite. Institutions were classified as elite if they met three specific criteria: a graduation rate exceeding 75%, a number of applications above the median, and a percentage of alumni who donate also above the median. To predict this target variable, fifteen institutional features were used as input variables. These features encompassed key dimensions of institutional performance, including admissions, academic excellence, and financial resources. Prominent predictors included the number of applications accepted, the number of students enrolled, the percentage of new students in the top 10% of their high school class, out-of-state tuition, and instructional expenditure per student. These variables were selected based on their relevance to elite classification and their potential influence on institutional success metrics.

To ensure data quality and consistency, the dataset underwent a series of preprocessing steps. No missing values were identified in the dataset. However, an outlier in the Graduation Rate column, where one institution reported a value of 118%, was addressed by capping the value at the logical maximum of 100%. Additionally, all numerical features were normalized to a range between 0 and 1 to facilitate model convergence and mitigate the effects of scale differences. This preprocessing ensured that the models could effectively leverage the data without introducing biases from outliers or inconsistent scaling.

Model performance was evaluated using two critical metrics: accuracy and the area under the receiver operating characteristic curve (ROC-AUC). Accuracy measured the proportion of correctly classified institutions, while ROC-AUC assessed the models’ capability to distinguish between elite and non-elite categories, with higher values indicating superior performance. The Random Forest model outperformed Logistic Regression on both metrics, achieving an accuracy of 91.45% and an ROC-AUC score of 0.956. These results underscored its ability to capture intricate, non-linear relationships within the data. Logistic Regression, while slightly less accurate with an accuracy of 89.74% and an ROC-AUC of 0.9345, provided valuable interpretive insights through its coefficients, which highlighted the relative importance of predictors.

By combining the strengths of Random Forest and Logistic Regression, this analysis delivered a balanced approach that maximized predictive performance while offering interpretability. Random Forest excelled at uncovering complex patterns and interactions within the data, whereas Logistic Regression provided a transparent framework for understanding how individual predictors influenced elite classification. Together, these models provided a comprehensive and actionable analysis, equipping the client with insights into the factors driving institutional elite status and laying the foundation for further research or decision-making.

Result
Our analysis identified several key factors that distinguish elite institutions. Institutions with a graduation rate exceeding 75%, application counts above the median (7,777), and higher percentages of alumni donations are more likely to be classified as elite. To classify institutions, we implemented two predictive models: the Random Forest model and Logistic Regression. The Random Forest model outperformed Logistic Regression with an accuracy of 91.45% and an ROC AUC of 95.60%, while Logistic Regression achieved an accuracy of 89.74% and an ROC AUC of 93.45%. 

Key features identified by both models included out-of-state tuition (Outstate), the percentage of students from the top 10% of their high school classes (Top10perc), and expenditure per student (Expend). However, the Random Forest model further highlighted the importance of acceptance rate (Accept) as an influential predictor. The Random Forest model’s ability to capture non-linear relationships and feature interactions contributed to its superior performance, particularly in identifying nuanced patterns in the data.



<img width="625" alt="Screenshot 2025-01-03 at 13 38 32" src="https://github.com/user-attachments/assets/c62153cf-8863-4a46-ba4a-29d6758fa414" />

Figure 2: Top 5 Influential Feature for Random Forest and Logistic Regression



<img width="557" alt="Screenshot 2025-01-03 at 13 39 34" src="https://github.com/user-attachments/assets/02d62b9f-91ec-4f3c-b6d9-9692ccc4e646" />

 Figure 3: The Accuracy and ROC-AUC for Random Forest vs. Logistic Regression Model


  
<img width="455" alt="Screenshot 2025-01-03 at 13 40 06" src="https://github.com/user-attachments/assets/93548128-7bdd-42a5-a753-8c11bef50a19" />

 Figure 4: ROC curve comparison for Random Forest Model vs. Logistic Regression Model


As shown in Figure 2, the coefficients for Logistic Regression emphasize the strong influence of variables like Outstate (coefficient 2.7679) and Top10perc (coefficient 2.1552), demonstrating their significant contributions to predicting elite status. Similarly, Random Forest’s feature importance rankings highlight Outstate (importance 0.1829) and Top10perc (importance 0.1217) as the top predictors, underscoring the consistency across models.

Figure 3 presents a comparison of the models' accuracy and ROC AUC scores, with Random Forest consistently outperforming Logistic Regression in predictive power. These findings suggest actionable strategies for institutions aspiring to elite status. By focusing on increasing out-of-state enrollment, attracting students from the top 10% of their high school classes, and strategically investing in student resources and infrastructure, institutions can improve their standing. Tables and visualizations, such as feature importance rankings and model performance comparisons, provide further clarity for decision-making and highlight the value of integrating data-driven insights into institutional strategies.

Conclusion
This project focused on analyzing data from 777 U.S. colleges and universities to provide strategic insights for a national education consulting firm. The goal was to explore how institutional characteristics such as public/private status, academic reputation, and student services impact key performance metrics, including application rates, graduation rates, and alumni donations. The insights derived from this analysis aimed to support the client in advising schools on improving student outcomes and operational efficiency.

A critical component of the analysis was the evaluation of predictive models to classify institutions as elite or non-elite and to uncover relationships between variables. After thorough model testing, the Random Forest model demonstrated its superiority over Logistic Regression, achieving an accuracy of 91.45% and a ROC AUC score of 95.60%. In comparison, Logistic Regression achieved slightly lower values, with an accuracy of 89.74% and a ROC AUC score of 93.45%. These findings highlight the Random Forest model's ability to capture complex, non-linear relationships between features and target variables, making it the most reliable tool for this analysis.

Key insights were drawn from the data. Elite institutions, characterized by higher out-of-state tuition and a larger percentage of students from the top 10% of their high school classes, were found to have a positive correlation with higher graduation rates. This suggests that tuition pricing and academic reputation are critical factors influencing both applications and graduation outcomes. Additionally, visualization of the data revealed notable variations in tuition levels and graduation rates between public and private institutions. For instance, public institutions often demonstrated higher-than-expected graduation rates compared to their private counterparts, challenging some preconceived notions about institutional performance.

Based on these findings, several recommendations were made for colleges to enhance their operational strategies. Firstly, increasing the enrollment of international students can be a viable strategy to boost tuition revenue and diversify the student body. Secondly, targeting high-achieving students, particularly those with strong academic backgrounds, can improve both institutional prestige and long-term outcomes such as alumni engagement and donations. Moreover, a careful balance in acceptance and enrollment rates could encourage higher student numbers without compromising institutional selectivity. Investment in student services and resources, such as infrastructure and faculty support, was also identified as a key area to improve student satisfaction and retention.
While the Random Forest model excelled in this analysis, there are opportunities for refinement. Collecting additional data, such as more nuanced measures of student demographics or faculty characteristics, could further improve predictive accuracy. Advanced feature engineering and hyperparameter tuning might also yield better results. Additionally, integrating explainability techniques such as SHAP values could provide the client with clearer interpretations of model predictions, enhancing their confidence in data-driven decision-making.

For the client, the next steps involve deploying the Random Forest model in real-world applications and periodically validating its performance with updated data. Continuous data collection and iterative analysis will ensure that the model remains relevant amidst changing trends. Exploring alternative models, such as Gradient Boosting or Neural Networks, may also uncover additional insights, particularly as the dataset grows in size and complexity.
In conclusion, this report provides a comprehensive analysis of U.S. colleges and universities, identifying the key factors that drive performance metrics and offering actionable recommendations for improving student outcomes and operational efficiency. By leveraging advanced predictive modeling techniques, such as the Random Forest, the client can gain deeper insights into institutional dynamics and make informed decisions to support their educational advisory goals. This approach not only strengthens the strategic planning capabilities of the client but also contributes to the broader mission of improving higher education across the country.

References


Bastedo, Michael N., and Nicholas A. Bowman. "Getting on the Front Page: Organizational Reputation, Status Signals, and the Impact of U.S. News and World Report on Student Decisions." Research in Higher Education, vol. 50, 2009, pp. 415-436.
"Bending the Curve: Institutional Factors Associated with Graduation Rates." Higher Education Policy, vol. 36, 2023, pp. 1–22.
"The Correlation Between Satisfaction and Alumni Giving." Ruffalo Noel Levitz, 2015.
Sung, Minjung, and Sung-Un Yang. "Student–University Relationships and Reputation: A Study of the Links Between Key Factors Fostering Students’ Supportive Behavioral Intentions Towards Their University." Higher Education, vol. 57, no. 6, 2009, pp. 787–811.
