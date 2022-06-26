
# Stress Detection using Physiological Signals 

We have extracted the following features from AffectiveROAD Dataset, a publicly available dataset of drivers in different stress situations. 

[Feature Extraction Code](AffectiveROAD_FeatureExtractionCode.ipynb)

A Frequency of 64 HZ was used, thus undersampling and oversampling were performed for the features. 

## BVP Features


**Total 32 BVP Feautres have been extracted.** 

There are 4 types of features we have extracted for BVP: 

NNI stands for NN Intervals here, we have haven't normalised our RR peaks. So, for all calculations, NNI and RRI are equivalent. And we use NNI to refer to them. 

- **Time domain features** : Mean_NNI, SDNN, SDSD, NN50, pNN50, NN20, pNN20, RMSSD, Median_NN, Range_NN, CVSD, CV_NNI, Mean_HR, Max_HR, Min_HR, STD_HR

- **Geometrical domain features** : Triangular_index, TINN

- **Frequency domain features** : LF, HF, VLF, LH/HF ratio, LFnu, HFnu, Total_Power

- **Non Linear domain features** : CSI, CVI, Modified_CSI, SD1, SD2, SD1/SD2 ratio, SampEn

**Note:- TINN, Triangular Index & VLF values had "inf" and "nan" values and thus these features were discarded and were not used for analysis**

We have used  [HRV-Analysis by Aura-healthcare](https://github.com/Aura-healthcare/hrv-analysis) in our code to easily extract features, for further information, please check their github repository.

## GSR/EDA Features

For GSR Data, features were extracted for a window size of 5 seconds with 2.5 seconds overlapping. 

**Total 18 GSR Feautres have been extracted.** 

There are 3 types of features we have extracted for GSR: 

We have used GSR to refer to GSR/EDA data here.

- **Statistical GSR/EDA Features** : 'mean_gsr','var_gsr','skew_gsr','kurtosis_gsr','std_gsr',

- **Tonic GSR Features** : 'mean_scl','var_scl','skew_scl','kurtosis_scl','std_scl','slope_scl',

- **Phasic GSR Features** : 'mean_scr','var_scr','skew_scr','kurtosis_scr','std_scr','max_scr','scr_peaks'

## Skin Temperature Features

For Skin Temperature, 7 features were extracted. 

- Min Temp
- Max Temp
- Minimum of Moving Average
- Maximum of Moving Average
- Mean of Moving Average
- STD of Moving Average



## XGBoost Model Results 
A 80-20 train test split was used to split the data. 
| **Physiological Signal** | **Accuracy on Test Data 10 CV** |
|--------------------------|---------------------------------|
| BVP                      | 77.48                           |
| EDA or GSR               | 75.389                          |
| Skin Temperature         | 55.96                           |
| BVP + EDA                | 78.98                           |
| BVP+ST                   | 78.37                           |
| GSR+ST                   | 78.26                           |
| BVP+GSR+ST               | 80.80                           |