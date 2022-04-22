# Probing how SHAP Explanation help Forecast Gold Price by XGBoost

Author: YANYU,CHEN (yc3823@nyu.edu) - Track 2

Referenced Code/Tools:
1. CapitalOne: "Create Synthetic Data by correlation matrix", [https://github.com/capitalone/synthetic-data](url) 
2. Plot_heatmap: "Correlation Matrix Heatmap", https://seaborn.pydata.org/examples/many_pairwise_correlations.html


## 1. Intro & Literature Review
My project is inspired by three papers: See their work summary in file "yc3823_CS3924_Proposal 1", located in this repository. 

In addition to these three papers:


In proposal 2, I added reference papers below to help selecting features of original data used to train XGBoost classifier:



In short, I want to test 2 hypotheses related to SHAP Explainer in my project:

> H1: Kumar explained that SHAP explanation is 
> 
> H2:



## 2. Data
### 2.1 Collect and Clean Raw Data

Jabeur and his team collect the price data of Gold, 

In reference to Jabeur's work, I collect the monthly price records  of features from Nov,2009 to Mar,2022 through website:

Gold Price: https://www.gold.org/
Metal Commodities' Price and Dollar Index: https://www.investing.com/
Geopolotical and Economic Policy Uncertainty indicators: https://www.policyuncertainty.com/gpr.html

Jabeur obtained a feature importance static diagram by the SHAP values explanation:

From this graph, we see the inflation feature contributes most positively to the final result. This correlation observation should be intuitive, because as inflation increases, the face value of products will increase in general. However, I'm more interested in probing the contribution of features besides inflation to the final prediction of XGBoost classifier, and the 


<div align=left><img width="700" height="500" src="https://github.com/Yanyu-Chen1010/AI-Visual-Final-Project/blob/70c6f5b50ee297db426f197e071b3db11c337d4b/correlation_matrix_X.png"/></div>



### 2.2 Create Synthetic Datasets

Since I want to 



## 3. Hypothesis Testing
### 3.1 XGBClassifier Train with original data

### 3.2 Shap.TreeExplainers of dataset in different structure

### 3.3 XGBClassifier Train with shapley values


## 4. Evaluation and Results Visualization

### 4.1 Hypothesis 1
Visualization Design

### 4.2 Hypothesis 2

### 4.3 Interactive tool


## 5. Case Study with Census-Income(KDD) dataset


## References 






