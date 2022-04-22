# Probing how SHAP Explanation help Forecast Gold Price by XGBoost

Author: YANYU,CHEN

Email: yc3823@nyu.edu

Track 2: [My Colab Code, update in progress](https://colab.research.google.com/drive/1WLl-zUAC1ABH-5olDNBtKFWHZTIAqIzS?usp=sharing)

# Introduction
## 1. Literature Review and Project Description
My project is inspired by three papers: 
> Jabeur, et.al. "Forecasting gold price with the XGBoost algorithm and SHAP interaction values"
> 
> Kumar, et.al. "Problems with Shapley- value-based explanations as feature importance measures"
> 
> Mokhtari, et.al. "Interpreting financial time series with SHAP values"

<br/>

Their work summary is in file "yc3823_CS3924_Proposal 1", located in this repository. 

<br/>

In proposal 2, I added below reference papers to help collect features data to train XGBoost classifier:
> James Ross McCown, "Investment  potential  and  risk  hedging  characteristics  of  platinum group  metals"
> 
> Renisha Chainani, "FACTORS INFLUENCING GOLD PRICES". (2016)

<br/>

Generally, in this project, I want to test 2 hypotheses related to SHAP Explainer:

> H1: 
>> Kumar explained that SHAP value’s explanation of feature importance is inconsistent due to the correlation between features. We can roughly understand the mathematical reasoning behind this inconsistency from the Eq.10, 11, 12, 13 excerpted from Kumar’s paper.
>> 
>> I.e. The correlation level between features used for training may result in different feature importance explanation if we use SHAP to explain black-box model. 
>> 
>> Hence, the first thing I want to test is, for synthetic datasets with varying correlation coefficient between features, will the SHAP explanation of feature importance changes?


<div align=center>
  <img width="500" 
       height="350" 
       src="https://github.com/Yanyu-Chen1010/AI-Visual-Final-Project/blob/6a2b8a9ed4258f145a1d01b6a10e9b35feb9237a/equation.jpeg"/>
</div>

> H2: 
>> Mokhtari et.al concluded in their paper, using the SHAP values to train models can improve the prediction accuracy in his research scenario. Hence, they believe SHAP values can be used as a data transformation technique to improve modeling process. 
>> 
>> So the second things I want to test is, in the example of Gold price forecast using XGBoost Classifier. Will the accuracy improved when we used the SHAP values of features matrix to train model?

<br/>



# Methodology
## 2. Data
### 2.1 Raw Original Data

Jabeur et, al. chose features: [ Silver,  inflation, Iron_Ore, USD_CNY, USD_EUR, Oil, SP_500] to train regressor models and predict the Gold prices. Then by the Shap.Explainer, they obtained below summary plot, in which the bar chart indicates the influence each kind of feature contribute to the final prediction. 

<div align=center>
  <img width="1200" 
       height="300" 
       src="https://github.com/Yanyu-Chen1010/AI-Visual-Final-Project/blob/27ad29df1396242e0a52f1f8d4e98443b0363530/Jabeur_summaryplt.png"/>
</div>

In my project, instead of training XGBoost.Regressor, I decide to train XGBoost.Classifier. Because the scale of original data I collect is small (149 rows), and classifier’s prediction is more general. In specific, while the regressor aims to predict precise Gold price next month, the classier aims to predict the Gold price will go up or go down next month. Practically, classifier is easier for normal people to briefly understand the Gold’s important potential as a risk-hedging investment. 

<br/>

Meantime, since the price of platinum group metal have considerable influence on the price of gold price (James, et.al. “Investment of Platinum Groups Metals” ), as well as the Economics and Geopolitical uncertainty (Renisha, “Factors Influencing Gold Prices, 2016). I decide to use:

> features X = [ Gold, Dollar_index, Crude_oil, Silver, Platinum, Palladium, Geo-political risk indicator, Economic Policy uncertainty] 
>
> label y = [Gold_trend_label]

<br/>

All commodity features are prices in unit: US-Dollar, collected as monthly records. The data frame obtained (df = X + y) after cleaning is described below:

<div align=left>
  <img width="550" 
       height="300" 
       src="https://github.com/Yanyu-Chen1010/AI-Visual-Final-Project/blob/27ad29df1396242e0a52f1f8d4e98443b0363530/Cleaned_Data_info.png"/>
</div>

<br/>

Raw Data Sources:
> [Gold Price](https://www.gold.org/)
> 
> [Metal Commodities' Price and Dollar Index](https://www.investing.com/)
> 
> [Geopolotical and Economic Policy Uncertainty indicators](https://www.policyuncertainty.com/gpr.html)





### 2.2 Create Synthetic Datasets

Ref:
1. [Correlation Matrix Heatmap Plot](https://seaborn.pydata.org/examples/many_pairwise_correlations.html)
2. [CapitalOne-Github: "Create Synthetic Data by correlation matrix"](https://github.com/capitalone/synthetic-data)

<div align=left>
  <img width="500" 
       height="400" 
       src="https://github.com/Yanyu-Chen1010/AI-Visual-Final-Project/blob/70c6f5b50ee297db426f197e071b3db11c337d4b/correlation_matrix_X.png"/>
</div>

<br/>

To test hypothesis 1, I plan to use the heatmap to find the original correlation coefficient between different features, then select the most closely correlated two out. Using the package written by CapitalOne to create new correlation matrix and construct synthetic dataset with varied structure. Then, with different synthetic dataset, we train the XGBoost.Classier and SHAP explained their feature importance. Compare their summary plot to whether structure change explanation eventually. 

<br/>

(For this part, since at first I misunderstood the package code, so I'm now re-writing this part. So currently I don't have many reuslts for H1. Yet, you can keep track of my progress in "My Colab Code" above.)

<br/>

## 3. Train Models and Explainers

### 3.1 XGBClassifier Train with original data

Please see "My Colab Code"

<br/>

### 3.2 XGBClassifier Train with shapley values

Please see "My Colab Code"

<br/>

### 3.3 Shap.TreeExplainers of Synthetic Datasets

Please see "My Colab Code"

<br/>

# Results

## 4. Evaluation and Results Visualization

### 4.1 Hypothesis 1: SHAP explanation of features' importance is unstable.

<div align=left>
  <img width="600" 
       height="700" 
       src="https://github.com/Yanyu-Chen1010/AI-Visual-Final-Project/blob/27ad29df1396242e0a52f1f8d4e98443b0363530/Original_XGB_Feature_Importance.png"/>
</div>

<br/>

The summary plot of other synthetic dataset's SHAP explainer is still in progress. 

<br/>


### 4.2 Hypothesis 2: use shap value to train classifier will increase accuracy

<div align=left>
  <img width="600" 
       height="300" 
       src="https://github.com/Yanyu-Chen1010/AI-Visual-Final-Project/blob/27ad29df1396242e0a52f1f8d4e98443b0363530/ROC_Compare_SHAP_Original_Train.png"/>
</div>

<br/>

I plan to compare the ROC of different classifer to visually illustrate how the SHAP value data transforamtion influence the performance of XGBoost.Classifiers. 

<br/>

### 4.3 Interactive Explanation Visual Tool

Ref: [Shoumik Goswami, Medium Blog](https://towardsdatascience.com/top-4-python-libraries-to-build-interactive-timeseries-plots-f2214cc9b1ea)

<br/>

Inspried by the post of Shoumik Goswami, I plan to design an interactive Visual tool to help users understand H1, H2. The design of tool is still in progress. Future results will be updated here in Git-hub.

<br/>

## 5. Case Study with Census-Income(KDD) dataset

Applying the interactive tool made to solve a classification problem in case of "Census-Income(KDD) dataset"

