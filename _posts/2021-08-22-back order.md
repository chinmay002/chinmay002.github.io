---
 title: BackOrder Prediction Model 
 date: 2021-08-12 
 categories: [Projects, Machine Learning] 
 tags: [Machine Learning, Random Forest, SVM, XGB CLassifier, SMOTE, Statistical Analysis] 
 pin: True

---
## Goal : Classify the products whether they would go into Backorder(Yes or No) based on the historical data of 1.9M and 24 features from inventory, supply chain and sales .

[Working Model](https://www.linkedin.com/feed/update/urn:li:activity:6841362356040278016/)

## Introduction
Backorders are unavoidable, but by anticipating which things will be backordered, planning can be streamlined at several levels, preventing unexpected strain on production, logistics, and transportation. ERP systems
generate a lot of data (mainly structured) and also contain a lot of historicaldata; if this data can be properly utilized, a predictive model to forecast backorders and plan accordingly can be constructed. Based on past data from
inventories, supply chain, and sales, classify the products as going into backorder (Yes or No).

## Proposed Solution
The proposed solution for this project is Machine learning algorithms can be implemented to predict backorder. Considering various features like inventory quantity,previous performance, minimum_balance,
forecast_sales , actual_sales etc as inputs from the web app, the implemented classification model will predict the output Here, we have used Random Forest Classifier to predict . However, drawing a baseline
model is important since it tells us how well other models have performed compared to base model. 

## Tech Stack Used
![tech_stak](https://github.com/chinmay002/chinmay002.github.io/assets/60249099/44e0a478-2889-4e15-aa97-6046168b5286)

## Design Details
### Process Flow
![process FLow](https://github.com/chinmay002/chinmay002.github.io/assets/60249099/1ce2f229-3e90-4d61-8810-6dc32dfc34bb)

### Deployment Flow
![Deployemnt Process](https://github.com/chinmay002/chinmay002.github.io/assets/60249099/f7332bba-edfd-4b7c-aff5-9c042f68015e)

## Experiments
### Data Cleaning 
* We had a data containing 1.9M rows with 24 columns describing Sales forecast for month 1,3,6,9 ,Sales Performance average, Transit ti,e stock Keeping time (SKU) etc.
* We checked for null values and found that column Lead Time had 11K missing values . When checked the distribution ,ww found it was skewed hence we opted for Median Imputation and for columns with normal distribution we used Mean Imputation
* Column Inventory had some neagtive numbers, since inventory cannot be neagtive we replaced neagtive values with 0.

### EDA

*  We wanted to know how our target column was distributed. Upon analzying the data we found that our dataset was heavily imbalanced with less than 10% were backorder data and <90% were not backordered
![back_order_cnt](https://github.com/chinmay002/chinmay002.github.io/assets/60249099/e6143c6e-dd6d-44d0-a0b2-d334e0c687f2)

* As we analyzed the data we found some interesting realtions such as sales vs forecast for backorder and not_backorder. Sales and forecast columns seems to be directly proportional for not_backorder data

![foreacste_vs_sales](https://github.com/chinmay002/chinmay002.github.io/assets/60249099/b1d369b0-1306-4d12-81a7-4f8ac9b45471)

* We found that our data had extreme outliers . to overcome that  we implemtned 3 Std Deviation rule which catures 99% of the data 
![outlier_det](https://github.com/chinmay002/chinmay002.github.io/assets/60249099/41b14502-0e11-47e6-b9ee-c8c09b74e591)

* Since we had 24 columns we wanted to know whether each columns correlates with any of the other columns hence plotted heatmap as below. Found that Sales and Forecast columns were highly correlated . Having both type of columns increases the complexity , hence we decided to use only one of those.
![heatmap](https://github.com/chinmay002/chinmay002.github.io/assets/60249099/7c8bf7e3-eb07-4497-8fdd-f01bd0141adb)


#### Statistical Tests
  * **VIF** : To check for multicollinarity and choose the final numcerical columns we used Variance Inflation Factor.
   ![vif](https://github.com/chinmay002/chinmay002.github.io/assets/60249099/aa5af77d-df94-470f-82f2-d4aab95718bb)


  * **Chi2** : To check if categorical column has any effect on Target. If yes including it in the model will help the model
  ![chi2](https://github.com/chinmay002/chinmay002.github.io/assets/60249099/e12a7d19-6b97-479e-9d9b-e1152c513f7b)



## Modeling .
* We used Random FOrest, Support Vecotr Classifier, Decision Tree and XGB Classifier for our experimentation.
![base_model_code](https://github.com/chinmay002/chinmay002.github.io/assets/60249099/c455f2c6-3cd5-4a24-973a-f9e8425263c4)
![result](https://github.com/chinmay002/chinmay002.github.io/assets/60249099/ece22e43-6c7e-4270-9d81-ee1f5a0a5991)

#### Hyperparameter Tuning for XGB as final model.

![Hyperparameter](https://github.com/chinmay002/chinmay002.github.io/assets/60249099/3c8d28fa-0422-4e77-b29f-83bd909d3a8e)
![Best_para](https://github.com/chinmay002/chinmay002.github.io/assets/60249099/0258ac42-e9e7-4421-bad6-7b55bc96ba23)
![Final Results](https://github.com/chinmay002/chinmay002.github.io/assets/60249099/1a199745-f831-43e1-8ab3-23eaf5f9291a)

# Results
After tuning our model we were able to achieve  f1-score of 95% , recall 93% and precision 97%.


# HeroKu Deploying. 
* Used Heroku PLatform and built a flask API . Currenlty Heroku platform has removed the free toer access and hence app may not be working.

![App_working](https://github.com/chinmay002/chinmay002.github.io/assets/60249099/542eb64d-f087-4ddb-a537-5243c60fc3c5)




















