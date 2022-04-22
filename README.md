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

> H1: Kumar explained that SHAP explanation is 
> 
> H2:

<br/>



# Methodology
## 2. Data
### 2.1 Raw Original Data

Jabeur and his team collect the price data of Gold, 

In reference to Jabeur's work, I collect the monthly price records  of features from Nov,2009 to Mar,2022 through website:

Raw Data Sources:
> [Gold Price](https://www.gold.org/)
> 
> [Metal Commodities' Price and Dollar Index](https://www.investing.com/)
> 
> [Geopolotical and Economic Policy Uncertainty indicators](https://www.policyuncertainty.com/gpr.html)

<br/>

Jabeur obtained a feature importance static diagram by the SHAP values explanation:
<div align=center>
  <img width="1200" 
       height="300" 
       src="https://github.com/Yanyu-Chen1010/AI-Visual-Final-Project/blob/27ad29df1396242e0a52f1f8d4e98443b0363530/Jabeur_summaryplt.png"/>
</div>

From this graph, we see the inflation feature contributes most positively to the final result. This correlation observation should be intuitive, because as inflation increases, the face value of products will increase in general. However, I'm more interested in probing the contribution of features besides inflation to the final prediction of XGBoost classifier, and the 




<div align=left>
  <img width="550" 
       height="300" 
       src="https://github.com/Yanyu-Chen1010/AI-Visual-Final-Project/blob/27ad29df1396242e0a52f1f8d4e98443b0363530/Cleaned_Data_info.png"/>
</div>





### 2.2 Create Synthetic Datasets

Ref:
1. [Correlation Matrix Heatmap Plot](https://seaborn.pydata.org/examples/many_pairwise_correlations.html)
2. [CapitalOne-Github: "Create Synthetic Data by correlation matrix"](https://github.com/capitalone/synthetic-data)

<div align=left>
  <img width="500" 
       height="400" 
       src="https://github.com/Yanyu-Chen1010/AI-Visual-Final-Project/blob/70c6f5b50ee297db426f197e071b3db11c337d4b/correlation_matrix_X.png"/>
</div>



## 3. Train Models and Explainers

### 3.1 XGBClassifier Train with original data

### 3.2 XGBClassifier Train with shapley values

### 3.3 Shap.TreeExplainers of Synthetic Datasets



# Results

## 4. Evaluation and Results Visualization

### 4.1 Hypothesis 1: use shap value to train classifier will increase accuracy

<div align=left>
  <img width="600" 
       height="300" 
       src="https://github.com/Yanyu-Chen1010/AI-Visual-Final-Project/blob/27ad29df1396242e0a52f1f8d4e98443b0363530/ROC_Compare_SHAP_Original_Train.png"/>
</div>






### 4.2 Hypothesis 2

<div align=left>
  <img width="600" 
       height="700" 
       src="https://github.com/Yanyu-Chen1010/AI-Visual-Final-Project/blob/27ad29df1396242e0a52f1f8d4e98443b0363530/Original_XGB_Feature_Importance.png"/>
</div>




### 4.3 Interactive Explanation Visual Tool

Ref: [Shoumik Goswami, Medium Blog](https://towardsdatascience.com/top-4-python-libraries-to-build-interactive-timeseries-plots-f2214cc9b1ea)



## 5. Case Study with Census-Income(KDD) dataset










