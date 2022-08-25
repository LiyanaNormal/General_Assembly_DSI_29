# Project 2 - Ames Housing Data and Kaggle Challenge

### Problem Statement ###

As purchase of housing plays a pivotal point to the human lifecycle into adulthood, we the bank find it integral to develop a model to predict the sale price of houses.
With use of the Ames housing data collected are used in the regression model to create the most accurate model. The model will be fine-tuned through analysis of features utilised, type of modelling and parameters, and will be evaluated through array of scoring such as MSE, R2 in the creation of the most accurate model.
This model will aid in housing sale price analysis giving the bank a more accurate benchmark for housing evaluation. 
A more accurate model would assist not only property agents but homeowners potentially selling and potential customers purchasing housing at that area in identifying the potential value of the property. 

### Executive Summary ###

In the following report, the following dataset of Ames Iowa Housing dataset was fitted to a regression model using the following with the consideration of the models (Linear regression, Lasso, Ridge and Elastic Net). From the In conclusion a regression model is used on the dataset provided. A lasso regression model is selected and with a cross validation mean score of 0.819, a mean square validation score of 0.876 and a mean cross validation of 30171 respectively. The top 5 highest coeficients to the features are Gr Liv Area, Overall Qual, Neighborhood_NdridgHt, Exter Qual and Garage Area in decreasing order respectively. The bottom 5 lowest coefficents to the features are Garage Type_Basement, Heating_Grav, Exterior 1st_HdBoard, Roof Dtyle_Mansard and Bsmt Unf SF respectively.

### Imported Data Dictonary ###

The data dictonary is for the imported dataframe can be imported from the Kaggle competition for DSI-US-11 Project 2 Regression Challenge ([source](https://www.kaggle.com/competitions/dsi-us-11-project-2-regression-challenge/data)).


### Decision of droping numerical feature columns ###

From the numerical columns, the features are evaluated on the variance, pearson correlation to Sale Price (output), p-values to determine if the feature is significant to be kept for the modelling stage.

The columns are noted for the following attributes are favourable:
1. Variance below 1 
2. Pearson correlation smaller than 0.3 (Only a statistically significant columns are kept to reduce multicolinearity of the model)
3. Analysis of the null-hypothesis, p-values more than 0.05 (Only a statistically significant columns, backward regression)

The feature columns are dropped in at 3 points in the analysis. They are for the numerical columns, the ordinal categorical columns and the nominal categorical columns.

### EDA of Numerical Columns ###

Based on the inspection of the histogram of the numerical columns, several features appear to be zero-inflated (left or right-skewed curve) and not following normal distribution. An outlier is identified in the Garage Yr Blt column has a general positive linear correlation to the sale price output. From the scatter plot there, is an outlier of garage year built in **2200** to be dropped prior to modelling.

### Removal of numerical Features ###

From the above statistical model, the probability (F-statistic) is 0, adjusted R-square (0.835). P>|t| values below 0.05, is likely to have correlation to the output feature y(Sale Price). 
The following feature value (P>|t|) above 0.05 are:
1. Id
2. PID
3. Lot Frontage
4. BsmtFin SF 2
5. Bsmt Unf SF
6. Low Qual Fin SF
7. Bsmt Half Bath
8. Full Bath
9. Garage Area
10. Open Porch SF
11. Enclosed Porch
12. 3Ssn Porch
13. Mo Sold
14. Yr Sold.

### EDA of Categorical Columns ###

From the categorical columns in the train dataframe, boxen plot was generated for all columns to determine the distribution of the 
data and to make outliers more visible in the columns. From the above plots and filters, there are some features does have outliers present such as in features, (ie.Sale Type, Misc Feature). However, these outliers are not removed from the dataframe because the information may be significant to the model and has no contrasting information to check against the column.

In addition, the following feature columns are itdentified to be ordinals, Alley, Lot Shape, Land Contour, Exter Qual, Exter Cond, Bsmt Qual, Bsmt Cond, Bsmt Exposure, BsmtFin Type 1, BsmtFin Type 2, Heating QC, Central Air, Electrical, Kitchen Qual, Fireplace Qu, Garage Finish, Garage Qual, Garage Cond, Pool QC and Fence. The remaining columns are taken to be nominal categorical columns. 

From the boxen plot above, there is no significant categorical columns with data highly favouring a particular option within the categorical column. Thus variance threshold is not used for the above dataset.

### Removal of categorical features (Nominal) ###
The following features are to be dropped prior to the modeling stage as both the pearson correlation is below 0.3 to Sale Price and has a P>|t| above 0.05. The features are the following:

1. Central Air
2. Garage Cond
3. Electrical
4. Exter Cond
5. Pool QC
6. BsmtFin Type 2
7. Fence

### Dropping of categorical Columns (Nominal) ###

From the above statistical model, the probability (F-statistic) is 0, adjusted R-square (0.921). P>|t| values below 0.05, is likely to have correlation to the output feature y(Sale Price). The following feature value (P>|t|) above 0.05 are:

1. MS SubClass 
2. Alley
3. Lot Shape
4. Land Contour
5. Year Remod/Add
6. Bsmt Qual
7. BsmtFin Type 1
8. Heating QC
9. 1st Flr SF
10. 2nd Flr SF
11. Bsmt Full Bath
12. Half Bath
13. Kitchen AbvGr
14. Fireplaces
15. Fireplace Qu
16. Garage Yr Blt
17. Garage Finish
18. Garage Cars
19. Wood Deck SF
20. Open Porch SF
21. Pool Area
22. Misc Val
23. MS Zoning_C (all)
24. MS Zoning_I (all)
25. MS Zoning_RM
26. Street_Pave
27. Utilities_NoSewr
28. Lot Config_FR2
29. Lot Config_FR3
30. Lot Config_Inside
31. Land Slope_Mod
32. Land Slope_Sev
33. Neighborhood_Blueste
24. Neighborhood_BrDale
25. Neighborhood_BrkSide
26. Neighborhood_ClearCr
27. Neighborhood_CollgCr
28. Neighborhood_Crawfor
29. Neighborhood_Edwards
30. Neighborhood_Gilbert
31. Neighborhood_Greens
32. Neighborhood_IDOTRR
33. Neighborhood_Landmrk
34. Neighborhood_MeadowV
35. Neighborhood_Mitchel
36. Neighborhood_NAmes
37. Neighborhood_NPkVill
38. Neighborhood_NoRidge
39. Neighborhood_OldTown
40. Neighborhood_SWISU
41. Neighborhood_Sawyer
42. Neighborhood_SawyerW
43. Neighborhood_Somerst
44. Neighborhood_Timber
45. Neighborhood_Veenker
46. Condition 1_Feedr
47. Condition 1_RRAe
48. Condition 1_RRAn
49. Condition 1_RRNe
50. Condition 1_RRNn
51. Condition 2_Feedr
52. Condition 2_Norm
53. Condition 2_PosN
54. Condition 2_RRAn
55. Condition 2_RRNn
56. Bldg Type_2fmCon
57. Bldg Type_Duplex
58. Bldg Type_Twnhs
59. Bldg Type_TwnhsE
60. House Style_1.5Unf
61. House Style_1Story
62. House Style_2.5Fin
63. House Style_1.5Unf
64. House Style_2Story
65. House Style_SFoyer
66. House Style_SLvl
67. Roof Style_Gable
68. Roof Style_Gambrel
69. Roof Style_Hip
70. Roof Style_Shed
71. Exterior 1st_AsphShn
72. Exterior 1st_BrkComm
73. Exterior 1st_BrkFace
74. Exterior 1st_CBlock
75. Exterior 1st_CemntBd
76. Exterior 1st_ImStucc
77. Exterior 1st_MetalSd
78. Exterior 1st_Plywood
79. Exterior 1st_MetalSd
80. Exterior 1st_Plywood
81. Exterior 1st_Stucco
82. Exterior 1st_WdShing
83. Exterior 2nd_AsphShn
84. Exterior 2nd_Brk Cmn
85. Exterior 2nd_BrkFace
86. Exterior 2nd_CBlock
87. Exterior 2nd_CmentBd
88. Exterior 2nd_HdBoard
89. Exterior 2nd_ImStucc
90. Exterior 2nd_MetalSd
91. Exterior 2nd_Plywood
92. Exterior 2nd_Stone
93. Exterior 2nd_Stucco
94. Exterior 2nd_VinylSd
95. Exterior 2nd_Wd Sdng
96. Mas Vnr Type_BrkFace
97. Mas Vnr Type_None
98. Foundation_CBlock
99. Foundation_PConc
100. Foundation_Slab
101. Foundation_Stone
102. Foundation_Wood
103. Heating_GasW
104. Heating_Wall
105. Functional_Maj2
106. Functional_Mod
107. Functional_Sal
108. Functional_Sev
109. Garage Type_CarPort
110. Garage Type_CarPort
111. Paved Drive_P
112. Paved Drive_Y
113. Sale Type_ConLI
114. Sale Type_ConLw
115. Sale Type_WD

The above columns are drop from the final feature columns in the train and test.

### Hyperparameter tuning ###

By changing the alpha from the hyperparameter testing from 100 to 500, a decrease is observed from the lasso_score. The n_alpha value of 200 is selected as it has the highest score of 0.799.

### Model Selection ###

From the above 3 linear regresssion model on the selected dataframe. Both Lasso and the ridge has a similar cross validation score with a ridge showing a slightly higher score.
However in the final modeling, Lasso is prefered over the ridge as it would be able further features that would not impact the output to 0.

### Summary of the Models ###

|Model Type|Cross Validation Score|Mean Square Score|Root Mean Square Error|
|---|---|---|---|
|Linear Regression|0.819|0.876|21948| 
|Elastic Net|0.148|0.150|73115| 
|Lasso|0.819|0.876|30171| 
|Ridge|0.819|0.876|29954| 

From the above table the Elastic Net model is values as the scores and RMSE is not performing as expected as it should be similar to the Lasso and Ridge model as it is an amalgamation of both aforementioned model. A possibility of such result could be due to the hyperparameter of the model which should be explored prior to use of this model for results on the current dataset.

### Model Selection of the Lasso ###

The lasso scores for the train and the test set is 0.856 and 0.876 respectively. Since the train and test results are not significantly different, the model is not significantly overfit or underfit. From the above cell, the R2 score for the lasso model is 0.876. 

From the above coefficient bar chart the following features are scaled to zero through the lasso regression, Exter Qual, MS_Zoning_RH, Exterior 2nd_Wd Shng, Functional_Min2, Garage Type_Detchd and Sale Type_ConLD.

The top 5 highest coeficients to the features are Gr Liv Area, Overall Qual, Neighborhood_NdridgHt, Exter Qual and Garage Area in decreasing order respectively.
The bottom 5 lowest coefficents to the features are Garage Type_Basement, Heating_Grav, Exterior 1st_HdBoard, Roof Dtyle_Mansard and Bsmt Unf SF respectively.


### Limitations to the model ###

The following are the limitations of the model:
1. Limited to features and scaling used in model such as neighbourhood, type of housing
2. Model is feasible on assumptions that future environment remain constant/same, i.e. national real estate regulations, economic status at time of sales. 
3. Sales price can change drastically should there be changes in macroeconomy (i.e no occurances such as pandemic)
4. Accuracy is limited to type of modelling and parameters used. 
5. There may be better machine learning models or hypertuning methods available currently and in future that can provide better prediction

The regression model used also has the following assumptions:
1. An assumption of linearity between dependent and independent variables.
2. An assumption that the linear regression is sensitive to outliers.

### Conclusions and Recommendations ###

In conclusion a regression model is used on the dataset provided. A lasso regression model is used and with a cross validation mean score of 0.819, a mean square validation score of 0.876 and a mean cross validation of 30171 respectively. The model was shortlised based on above criteria ensures chosen model provide best predict property value, allowing bank give a safe valuation for closest mortgage loan or real estate acquisition consideration.   

The following recommendations for the futher analysis to strengthen the model are to further explore the following features in more in-depth. The features are Gnr Liv Area (Above grade (ground) living area square feet), Overall Quality and the Neighbourhood of the housing.
