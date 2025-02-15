# Time Series Analysis of Deaths in the UK  

## Overview  

Understanding long-term mortality trends is crucial for **public health planning, policy formulation, and resource allocation**.  
This project analyzes and forecasts the **annual number of deaths in the United Kingdom** using **time series modeling**,  
providing insights into historical patterns and future mortality trends.  

By applying **Holt-Winters Exponential Smoothing and ARIMA models**, this study offers a data-driven foundation  
for predicting mortality rates, aiding **healthcare resource management** and **policy interventions**.  

## Objectives  

- Analyze **historical mortality trends** in the UK.  
- Identify **patterns, trends, and key events** influencing death rates.  
- Develop **forecasting models** to predict future mortality rates.  
- Compare **Holt-Winters Exponential Smoothing** and **ARIMA** for predictive accuracy.  

## Dataset  

The dataset, sourced from the **Office for National Statistics (ONS)**, contains **annual death records in the UK from 1887 to 2021**.  
It includes:  

- **Yearly Death Counts** (aggregated at the national level).  
- **Key Historical Events** (e.g., **World Wars, pandemics, demographic shifts**).  

### Ethical Considerations  

- **Publicly Available Data**: The dataset is open-source and complies with **ethical research standards**.  
- **Data Accuracy**: Official records ensure **reliability and credibility** for forecasting.  

## Exploratory Data Analysis (EDA)  

Key insights from the **data exploration phase**:  

- **Long-Term Trends:**  
  - **Declining mortality rates** from 1887–1920s.  
  - **Sharp spikes** during **World War I (1914-1918), the 1918 Influenza Pandemic, and World War II (1939-1945)**.  
  - **Steady increase** from the **1960s to the 1980s**, linked to population aging.  
  - **Mortality decline (1980s-2000s)** due to **advancements in healthcare**.  
  - **Recent increase (2010s-2020s)**, likely influenced by **COVID-19** and demographic shifts.  

- **Decomposition Analysis:**  
  - The series was found to be **non-seasonal**, with a **clear trend and irregular fluctuations**.  
  - A **10-year Simple Moving Average (SMA)** was applied to smoothen short-term fluctuations.  

## Time Series Modeling  

Two forecasting models were developed:  

### **1. Holt-Winters Exponential Smoothing**  

- **Chosen for its ability to model long-term trends.**  
- **Key Model Parameters:**  
  - **Alpha (0.48):** Recent observations carry 48% weight.  
  - **Beta (0.15):** Past trends contribute 85% to slope estimation.  
- **10-Year Forecast:**  
  - Predicted **steady rise in deaths (673,000 to 761,000 per year)**.  
  - Confidence intervals provided for **uncertainty assessment**.  
- **Model Performance:**  
  - **RMSE:** 30,940  
  - **MAPE:** 3.54%  
  - **Evaluation:** Effective but **higher error compared to ARIMA models**.  

### **2. ARIMA Models (Auto-Regressive Integrated Moving Average)**  

- **Step 1: Stationarity Check (Dickey-Fuller Test)**  
  - The series was **not stationary** (p-value > 0.05).  
  - **First-order differencing** applied to achieve stationarity.  

#### **ARIMA (0,1,1) - Moving Average Model**  

- **Simplest model with minimal parameters**.  
- **Key Features:**  
  - No autoregressive terms.  
  - **Dependence on past errors** (MA(1) term).  
- **Performance:**  
  - **RMSE:** 28,391  
  - **MAPE:** 3.28%  
  - **Evaluation:** Best balance of **accuracy and simplicity**.  

#### **ARIMA (3,1,0) - Autoregressive Model**  

- **Includes three autoregressive terms** for better trend modeling.  
- **Performance:**  
  - **RMSE:** 28,078  
  - **MAPE:** 3.26%  
  - **Evaluation:** Most accurate but **slightly more complex**.  

## Model Comparison  

| Model | RMSE | MAPE | Strengths | Weaknesses |
|--------|------|------|-----------|------------|
| **Holt-Winters** | 30,940 | 3.54% | Simple, effective for long-term trends | Higher error rate |
| **ARIMA (0,1,1)** | **28,391** | 3.28% | Minimal parameters, best AIC score | Slightly less accurate than ARIMA(3,1,0) |
| **ARIMA (3,1,0)** | **28,078** | **3.26%** | Best accuracy, no autocorrelation in residuals | More complex |

- **Final Choice:** **ARIMA (0,1,1)**  
  - Nearly identical accuracy to ARIMA(3,1,0).  
  - **Fewer parameters**, making it **more interpretable and efficient**.  

## Key Findings & Business Implications  

- **Steady Increase in Mortality Rates**: Forecasts suggest rising deaths, requiring **healthcare resource planning**.  
- **Impact of Historical Events**: Mortality trends align with **wars, pandemics, and healthcare advancements**.  
- **Data-Driven Decision Making**: Governments can use forecasts to **allocate resources efficiently**.  
- **Public Policy Impact**: Mortality trends can **inform public health interventions and social policies**.  

## Actionable Recommendations  

- **Healthcare Resource Planning:**  
  - Use forecasts to allocate resources for **hospitals, elderly care, and emergency response units**.  
- **Public Health Policies:**  
  - Develop **preventive healthcare programs** to **reduce future mortality rates**.  
- **Demographic Strategy:**  
  - Prepare for **aging population impacts** on social services and pensions.  


## How to Run  

### Clone the Repository  

```sh
git clone https://github.com/kenny-balogun/time_series_analysis_UK_mortality.git
```
### Install Dependencies

```sh
Rscript -e "install.packages(c('tidyverse', 'forecast', 'TTR', 'tseries', 'readxl'))"
```
### Run the Analysis

Open RStudio and load the statistical_analysis_wine.rmd file.
To knit the markdown file into a PDF, run:

```sh
rmarkdown::render("time_series_analysis_UK_death.rmd")
```
