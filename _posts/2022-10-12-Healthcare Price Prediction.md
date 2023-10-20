---
title: Healthcare Price Prediction Model date: 2022-11-29 categories: [Projects, Machine Learning] tags: [Machine Learning, Healthcare, Decision Tree, SVM, Linear Regression, R] pin: true
---


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


### Vizualizations
* Target Distributions: Skewness of Total costs columns. Keeping the Threshold as 4775 which is 3rd quartile and covers 97% of the data.

![target_bar_graph](https://github.com/chinmay002/chinmay002.github.io/assets/60249099/292cbcce-2c23-45ad-adb2-c284e6405d68)

* Age Category : As we can see from the below graph that People in age 20-25 are more in number  wheras people of age more than 55 are less. Also from boxplot we can infer that People who has expensive health cost has Medain age around 47 whereas medain age is 36 for the ones who pays less .
![age_vs_target](https://github.com/chinmay002/chinmay002.github.io/assets/60249099/9bc72e26-98ce-4f63-a025-74fc7946d394)
* To get more insights we categorized the age data into category called as  "Young","Senior","Aged". From Below its more clear that **Aged(>50) pays has Medain Cost of 4022$ compared to Young(18 to 35) with just 861$.**
![Age_cat_vs_Medain_value](https://github.com/chinmay002/chinmay002.github.io/assets/60249099/d03b04c3-0f79-4031-9c83-f17ea003879f)

* Smokers vs Non_Smokers
* Analyzing our data, we observe that roughly 80% of individuals are non-smokers, while only 19% are smokers. Delving further into the impact on our target variable, we find that smokers tend to allocate a higher portion of their expenses to healthcare costs. Conversely, the majority of individuals with lower healthcare costs are non-smokers.ie **Smokers Median Cost was staggering 8512$ wehereas just 1946$ for Non_Smokers which is 4x times less than what Smokers pay**.
![Smokers_vs_Medain](https://github.com/chinmay002/chinmay002.github.io/assets/60249099/e20ccd00-dc2d-4cb2-8af9-096ed5e4e7f7)


* Exercise:
From below bar plot we can say that people who are Active has Lower health cost comapred to who are not active. where former pays 1463$ and later with costs 2970$

![exercise_vs_medai](https://github.com/chinmay002/chinmay002.github.io/assets/60249099/5d8347c6-c266-4062-a867-7e8001360f8e)


* No of Children : Our Assumption was having more children woudl incur more charges and when we delved deeper we found our assumption to be true. People with 0 children paid 2072$ and poeple with 3+ children paid over 3200$. 
![No_of_childeren_vs_medain](https://github.com/chinmay002/chinmay002.github.io/assets/60249099/c644548a-11d8-4cab-884b-b1528664e022)


* BMI : Initially our BMI coulmn was numerical but we binned the data into "Healthy","Obesity","Overweight","Underweight". What we predicetd was Obesity and Overweight people spend more on Healthcare . And according to below grapgh it turned to be true. Where Obese people pay 3000$ . Underweight spend lowest with 1374$
![bmi_cat_vs_meadin](https://github.com/chinmay002/chinmay002.github.io/assets/60249099/b05e4244-3615-4832-9a66-84266078c5e5)



* Location : Since Cost of Living varies based on where people reside , we decided to check how location and cost varies. To our surprise Newyork people spend more followed by Massachusetts. On the other side Maryland and Connecticut spend least on healthcare.

![location_vs_medain](https://github.com/chinmay002/chinmay002.github.io/assets/60249099/575304ce-ea80-4d8d-bf33-62721f491e34)


## Data Modelling:
* The information obtained from the dataset has been accurately modeled using a few different approaches. These models provide a comprehensible representation of the underlying data sets' reality. Specifically, the following models have been used:

#### Linear Regression :
    * From the insights we got from EDA part we used age, bmi,children,smoker,exercise,hypertension,yearly_physiscal_vist,and target
    * In our regression model, we found out several significant variables namely age, bmi, children,smoker, exercise, hypertension
    * Yearly_physical was somewhat important but did not have a major impact. While location_type, education_level, married, gender have little to no impact.
----![linear_reg](https://github.com/chinmay002/chinmay002.github.io/assets/60249099/316ca95f-e880-4e40-8a3b-9f5e931d4a0d)

#### Decision Tree Classifer :
    * Considering that we put all features in the model, we tried to simplify the model by turning numeric variables into categorical variables. 
    * Using just Smoker, age, bmi,exercise,children,yearly_physoical, hypertension we achieved an accuracy of 88% with Specificity of 95%
   ![DT_confu_matrix](https://github.com/chinmay002/chinmay002.github.io/assets/60249099/e0c318f1-a41a-4f65-bbd3-5fea60dd3162)
   ![DT_all_avriable](https://github.com/chinmay002/chinmay002.github.io/assets/60249099/85b768f4-a32a-4442-a4e7-82b92f9c2492)


# Recommendations:
* We would recommend HMO should introduce insurance policies based on various factorssuch as smoking habits, location, BMI.
* HMO should look into opening small health clinics in big cities so that people have moreaffordable healthcare options



















