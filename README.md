# Consultation for Ames, IA Realtor Focused on Incoming University Professors

## Data Used

test.csv - Pre-supplied testing data for testing and modeling for Kaggle competition
clean_test.csv - Cleaned testing data to the specifications of the Kaggle submission
train.csv - Pre-supplied training data for creating and modeling data to answer data science problem
clean_train.csv - Training data cleaned based on needs of answering data science problem
engineered_train.csv - Training data including feature engineering and outlier mitigation
submission.csv - Two-column file including house sale ID and sale price prediction for purpose of Kaggle submission

## Problem Statement

A realtor in Ames, IA has reached out to a data scientist for a consult. Their preferred clientele are professors moving from far-away places (i.e. not familiar with Iowa). As a realtor in Iowa, they are hyperfixated on tornado safety, and want to provide homes to their clients that have reasonably good quality basements in case they spend an abundance of time there due to tornadoes. That being said, they also seek to find their clients homes in neighborhoods close to Iowa State University. For their consult, they want help creating a model that helps them predict good sale prices for homes with good quality basements near Iowa State in order to make sure they can satisfy their fixation on a good basement while minimizing the commutes of their clients and making sure they get a good deal on a home. 

## Data Dictionary

|Feature|Type|Description|
|---|---|---|
|lot_area|int|The square footage of the lot that a home is on|
|1st_flr_sf|int|The square footage of the first floor of a home|
|2nd_flr_sf|int|The square footage of the second floor of a home|
|bsmtfin_sf_1|int|The square footage of the primary finished basement of a home|
|bsmtfin_sf_2|int|The square footage of the secondary finished basement of a home|
|bsmt_unf_sf|int|The square footage of the unfinished basement of a home|
|1stflr_bsmtfin1_sf|int|Interaction term of 1st_flr_sf and bsmtfin_sf_1|
|bsmt_full_bath|int|Number of full baths in the basement of a home|
|bsmt_half_bath|int|Number of half baths in the basement of a home|
|neighborhood_CollgCr|int|Determines if home is located in College Creek neighborhood|
|neighborhood_Crawfor|int|Determines if home is located in Crawford neighborhood|
|neighborhood_Edwards|int|Determines if home is located in Edwards neighborhood|
|neighborhood_MeadowV|int|Determines if home is located in Meadow Valley neighborhood|
|neighborhood_NoRidge|int|Determines if home is located in Northridge neighborhood|
|neighborhood_SWISU|int|Determines if home is located in neighborhood south and west of ISU|
|neighborhood_Sawyer|int|Determines if home is located in Sawyer neighborhood|
|neighborhood_SawyerW|int|Determines if home is located in Sawyer West neighborhood|
|bsmt_qual_Ex|int|Determines if basement is 90-100 inches tall|
|bsmt_qual_Gd|int|Determines if basement is 80-90 inches tall|
|bsmt_qual_TA|int|Determines if basement is 70-80 inches tall|
|bsmt_cond_Gd|int|Determines if basement is in good or better condition i.e. no moisture allowed in|
|bsmt_exposure_Av|int|Determines if exposure of basement is of average quality|
|bsmt_exposure_Gd|int|Determines if exposure of basement is of good quality|
|bsmtfin_type_1_GLQ|int|Determines if primary finished basement area contains good quality living quarters|
|bsmtfin_type_1_ALQ|int|Determines if primary finished basement area contains average quality living quarters|
|bsmtfin_type_2_GLQ|int|Determines if secondary finished basement area contains good quality living quarters|
|bsmtfin_type_2_ALQ|int|Determines if secondary finished basement area contains average quality living quarters|
|bsmtfin_type_2_Rec|int|Determines if secondary finished basement area is used as a rec room|
|neighborhood|object|The neighborhood that the home is in|
|bsmt_qual|object|Determines basement height|
|bsmt_cond|object|Determines overall basement condition i.e. dampness, insulation, etc.|
|bsmt_exposure|object|Refers whether basement has walkout or garden level walls|
|bsmt_type_1|object|Rating of type of primary space in basement|
|bsmt_type_2|object|Rating of type of secondary space in basement if multiple types|


## Modeling Summary

The initial step required determining the features that would be vital to creating a model that fit the client's needs. In this case, since the client sought a model that would help predict prices based on a home's proximity to ISU, creating one-hot variables for neighborhoods to identify the impact that neighborhood has on price is crucial. The remaining features were all of those regarding basements, some of which also required one-hot encoding in order to be modeled. After fitting and testing a linear regression, LASSO, and Ridge model, it was found that the Ridge model provided the R-squared score closest to 1 after cross-validation. 

## Conclusions

Overall, the model indicates that area-related features, i.e. lot size and various square footages, were the most significant predictors of sale price. However, all of the basement-related features that made it to the final model had positive impacts, especially finished basement size and the excellent and good quality basement features, all of which had coefficients into the tens of thousands. Neighborhood data was less impactful, with the majority of neighborhoods having negative coefficients, implying that neighborhoods around ISU tended to be less desirable with the exception of College Creek, Crawford, and Northridge, which had positive coefficients.

Based on the fit of the model, this could be a fairly helpful model for helping the client predict sales prices of homes based on their location and basement data, accounting for about 80% of the variation in the data.