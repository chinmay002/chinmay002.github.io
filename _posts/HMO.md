# DATA ANALYSIS FOR HEALTH MANAGEMENT ORGANIZATION

## Goal:
* Analyze the healthcare data and predict which patients will be spending more 
* Provide Recommendation to Heath Management Organization on how they can reduce the total health costs.
## Overview:
* **Dataset Description** : The project involves analyzing a dataset containing various personal attributes, such as smoking habits, exercise routines, and living locations, with a total of 13 attributes per individual.
* **Focus on Cost Analysis** : The primary focus of the project is to determine what factors influence a person's healthcare expenditure, classifying them as 
 "expensive" or "not-expensive" in terms of healthcare spending.
* **Statistical Analysis** : The project aims to apply statistical techniques to uncover the factors affecting healthcare expenditure. This will involve using data analysis and statistical methods to draw insights from the dataset.
* **Actionable Insights** : The objective is to provide actionable insights to the client, a Health Management Organization, on areas where they can reduce their total healthcare costs. These insights will be derived from the analysis of factors that contribute to high healthcare spending.
* **Healthcare Cost Reduction** : The project will offer recommendations on how the Health Management Organization can improve and reduce overall healthcare costs based on the findings. These recommendations will be data-driven and focused on cost-saving measures.
* ** Predictive Insights ** : Additionally, the project aims to provide insights into which category of individuals is likely to have higher health-related spending in the coming year. This predictive aspect will help the client plan and allocate resources effectively.
* **Client-Focused** : The project's ultimate goal is to assist the Health Management Organization in making informed decisions to enhance their healthcare cost management and planning strategies.


## Exploratory Data Analysis and Preprocessing.
* Dealing with missing data points: we removed 158 missing data points in bmi and hypertension variables.
* Inspecting the data set: There are 7,502 examples with 14 features related to personal health information (cost, age, bmi, number of children, and etc.).
* Performing binning and transformation on variables 
    * Numeric to Categorical: age, bmi
    * Categorical to Logical: education level, the number of children
* Setting the boundary for expensive or not expensive : Since our target value was highly skewed we opted for 3rd quatile as threshold  since **97%** of people were inside this quartile to convert the numerical values into Categorical values. So people whose cost was above 4775 were labelled as **Expensive** , while people with charges below were labelled as  **Not_Expensive**






