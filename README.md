# Fresh-Retail
Building ML models to forecasting sale of Fresh Retail business with latend demand due to stock out

## Overview
The Project notebook is structured into several key sections:
1.  **Setup and Data Download**: Installs necessary libraries and downloads the `FreshRetailNet-50K` dataset from Hugging Face. **Dataset**: [Dingdong-Inc/FreshRetailNet-50K](https://huggingface.co/datasets/Dingdong-Inc/FreshRetailNet-50K)
2.  **Data Preparation**: Cleans and transforms the raw data, creating unique series IDs and day indices.
3.  **Shared Functions**: Defines and applies common data processing functions, including `flag_censoring` (to identify stockouts), `make_features` (for lags and rolling means), and `time_split` (to separate training and validation data).
4.  **Data at a Glance**: Provides a high-level summary and initial visualizations of the dataset characteristics.
5. **Operation track**
6.  **Benchmark with baseline models**: Implemented a Weighted Absolute Percentage Error (WAPE) evaluation function.
Established naive forecasting baselines (Global mean, Seasonal naive, Rolling 28-day) on raw sales and evaluated their performance (D1). Explored a recovery-first approach by imputing censored hourly sales using random pool sampling to estimate corrected daily sales (D2).
7.  **ML models and recovering strategies**: 

***Direct Forecasting ( D1)***
Develop ML models to beat the base line. Suggested models from lectures: exponential smoothing or a simple LightGBM with lag features; SSA; TFT; DLinear
→  Compare the performance of models 
Analyze errors ( part 6d slide): Analyze errors by day-of-week to detect weekly patterns; Compare WAPE across cities to find geographic patterns;...

***Forecasting with Recovered demand (D2)***
Use different methods to recover demand. Suggested strategies from lectures: (a) per-series hourly mean; (b) weighted sampling by recency; (c ) learned models (TimesNet, ImputeFormer, SAITS, iTransformer, GPVAE, CSDI, DLinear)
→  Compare performance of different recovering strategies  
→  Compare forecast performance of a model trained on recovered demand and latent demand  
Analyze errors:  focusing on high-stockout series where recovery matters most,....
