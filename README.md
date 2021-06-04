
# King County Housing Project
By: Lera Tsayukova

![Seattle](https://user-images.githubusercontent.com/75099138/120870328-a295e280-c566-11eb-8f6c-179ca160d4c6.jpg)

Phase 2 Project

# Summary
This project examines housing sales data from Kings County Washington, between 2014 and 2015, in order gain insight about what factors determine house prices. 
This repo is broken into two parts. The EDA notebook outlines the data exploration process; it examines the raw data set, engineers new features, and goes through the cyle of creating a model and testing the data against itself. . The Prediction Notebook utilizes the findings and features from the EDA notebook in order to create predictions for a holdout data set of housing data to see how accurately the created model can predict housing prices.

### Data Preparation and EDA Steps
A) Prep the data by: 
  -Checking for null/missing values
  -Imputing values if neccessary
  -Examining the types of data within the Pandas DataFrame
  -Finding outliers by running statistical tests- using the mean and standard deviations
  -Checking for inconsistencies in the data
  
B) Exploratory Data Analysis (EDA: 
  The goal here was to gain an understanding of the data's main characterstics by:
  -Creating a correlation map
  -Producing graphs of features and the target(housing prices)
  -Looking for linear relationship among the data
  -Running statiscal tests in order to validate relationships
  -Determine which features are continous or noncontinuous
  -Engineer new features in order to better caputure relationships
  -Capping certain values 
 

## I. Data Prep and EDA Useful findings 

-Based on the heat map below, it was easier to see how the features correlated with themselves:
![corr_heatmap](https://user-images.githubusercontent.com/75099138/120867196-7034b700-c55f-11eb-969b-8e223a6a1d4b.png)


##### Bathrooms
-Some insightful findings includes the number of bathrooms which were oddly distributed:
![bathrooms scatterjoin](https://user-images.githubusercontent.com/75099138/120869903-8180c200-c565-11eb-9d40-b08a1538e0b6.png)


#### View & Sqft Living
-Additionally it seemed that square foot living had a large impact on price, especially when paired with other features:
![view_scatter](https://user-images.githubusercontent.com/75099138/120867296-9f4b2880-c55f-11eb-9464-8a0cf8872368.png)

#### Location (Latitude & Zipcode)
-Perhaps the most obvious feature but hidden amongst the others was Latitude:
-This feature was engineered to split Kings County homes between North and South, showing a substantial difference in home prices
-The GeoMap from Seaborn shows the approximate split at about 47.5 degrees latitude, with a concentration of high priced homes in the center
![geomap_prices](https://user-images.githubusercontent.com/75099138/120867543-226c7e80-c560-11eb-9371-6d5a49e6ad96.png)


## II. Inference And Prediction Modeling 
- The next step in the process involved two parts
 A) modeling for inference
  -In order to better understand our data we need to determine what variables affect the target(housing price)
-B) modeling for prediction
  -Once we have enough insight for our data we can narrow down to the most important factors and use those to predict unknown housing prices
 
 ##### Inference: 
  By running an OLS model on our numerical categories, we are able to better understand how the variables impact price based on the paired coeffecient:
  -For example: SqftLiving, waterfont, and bathrooms were some features which strongly impacted price.
  <img width="532" alt="Screen Shot 2021-06-04 at 6 17 32 PM" src="https://user-images.githubusercontent.com/75099138/120868183-7035b680-c561-11eb-982a-a55734ec4b77.png">
<img width="643" alt="Screen Shot 2021-06-04 at 6 17 22 PM" src="https://user-images.githubusercontent.com/75099138/120868186-7330a700-c561-11eb-8c45-483d5d19f525.png">

 ##### Prediction:
  
  In order to model for prediction, first a simple model was evaluated using the Train-Test split method; a Root Mean Squared Error score was computed from the errors for both Testing and Training Data and used to evaluate how well the model predicted price.

 Next, the original features in the data were combined with new engineered features, and dummy variables. The next step was to narrow these variables down to the most useful predictors using Feature Selection Methods.
 
 ###### Feature Selection:
 
All of the original features combined with new engineered features and dummy categories were filtered down through the Wrapper Method- Recursive Feature Selection. The final model was then whittled down to 106 features which gave the the lowest RMSE score predicting within 150000 dollars of the target. The residuals were graphed below:![Residuals](https://user-images.githubusercontent.com/75099138/120869475-90b34000-c564-11eb-8d34-b84209e86ba0.png)


# III: Ideas for Future Modeling
-More work can be done to narrow down and eliminate down and eliminate the best features, such as going back and looking at the residuals more in depth, and finding out which errors are not normally distributed. Another best practice could be to take the log transformation of some of the numerical columns.
 
 
### Repository 
-READ.me
-data
-visuals
-EDA notebook
-KC_Final_Housing_Model.ipynb
-KC_Final_Housing_Predictions.ipynb
-KC_Housing_presentation.pdf



  
