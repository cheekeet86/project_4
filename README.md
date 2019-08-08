# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 4 - Kaggle Competition on West Nile Virus Prediction 

## Problem Statement





Predict West Nile virus in mosquitos across the city of Chicago

## Background

For project 4, we are participating in a kaggle competition on predicting West Nile Virus in Chicago. Public health workers in Chicago setup mosquito traps scattered across the city from late-May to early-October every year. These traps collect mosquitos every week from Monday through Wednesday and the mosquitos are tested for the presence of West Nile virus before the end of the week. The test results include the number of mosquitos, the mosquitos species, and whether or not West Nile virus is present in the cohort. 

For this competition, we will be analyzing weather data and geospatial train/test dataset and will be predicting whether or not West Nile virus is present, for a given time, location, and species. 

## Datasets

We are given the following datasets: 
- train.csv, test.csv: The training and test set of the main dataset. The training set consists of data from 2007, 2009, 2011, and 2013, while we are required predict the test results for 2008, 2010, 2012, and 2014.
- spray.csv: Geospatial data of spraying efforts in 2011 and 2013. Contains 584 null values in time column.
- weather.csv: Weather data from 2007 to 2014. Contains missing values in several columns. 

## Project Planning

We started by examining the different datasets and coming up with an overall framework on how we should approach the data cleaning process before splitting up the data cleaning work. We then combined the test, train and spray datasets and performed data visualisation and feature engineering on the combined dataset. The imbalanced dataset is a key challenge and we have attempted to address this with two different oversampling methods namely, Synthetic Minority Over-sampling Technique (SMOTE) and random oversampling. SMOTE method appears to be more effective compared to random oversampling as it gives a higher ROC score during the subsequent modeling phase. We then tried different regression techniques (including decision tree, random forest, K-Nearest-Neighbour and AdaBoost). We selected RandomForest as our choice model as it gives the highest ROC score and did hyperparameter tuning to see if we could get an even higher score. 

Click [here] (https://docs.google.com/spreadsheets/d/1D7kW-O84Uw8OBh_lDO1cWSdUZuZpYE5IqDCNe0ANCq0/edit?usp=sharing) for further details on the work allocation and project planning phase. 



## Folder Structure

    .
    ├── code            # source code
    ├── data            # datasets
    |   ├── 1_raw       # data downloaded from kaggle
    |   ├── 2_input     # extracted files from 1_raw      
    |   ├── 3_clean     # cleaned dataframes
    |   └── 4_output    # for kaggle submissions
    ├── documents       # requirements, presentations             
    ├── images          # pictures and media   
    └── README.md

## Model Evaluation 

We tried a variety of models including Logistic Regression, Random Forest, Decision Trees. Both Random Forest and Decision Trees models give pretty high scores but we eventually chose Random Forest Classification as Decision Tree is prone to overfitting. We have also decided against using the spray dataset as it only contains data from 2011 and 2013, whereas the test/train and weather datasets are from 2007 to 2014. 

The differences between the kaggle scores and the training scores for our initial models indicated that our models were overfitted. Therefore, we proceeded to explore more work to better prepare the data for modelling. For the exploration of SMOTE that was used as our final model - SMOTE is closely related to the real-life scenario where presence of virus is expected to cluster in vicinity of an infected area.

## Recommendation

There is no human vaccine for West Nile Virus. In some severe cases, patients need to be hospitalized to receive treatment- such as intravenous fluids, pain medication, and nursing care. In addition to threatening lives, outbreaks of WNV in the United States are very costly in terms of both medical treatment and event control. As an example, a 2005 outbreak in Sacramento, CA generated costs of approximately $3 million, of which about $700 thousand was associated with vector control (emergency spraying) and $2.3 million was related to medical treatment and lost productivity of patients (Barber et al. 2010).

**Prevention is thus better than cure.** We recommend using our model with the following features to predict when and where to spray airborne pesticides one month before: (i) Number of mosquitos, (ii) Average temperature, (iii) Precipitation, (iv) Location, and (v) Month. We further propose to launch education campaigns at hotspot neighbourhood to nip larvae growth in the bud. This includes broadcasting information to self-protect during days/ months where mosquito count is expected to peak.

## Further Exploration 

Our best model currently gives a false negative rate of 18%. We recommend to explore further reducing this rate by increasing accuracy of prediction of number of mosquitos. We also recommend exploring more feature engineering to improve our model score. We also suggest to gather more data on the spraying efforts and examine its effectiveness. 

