# Predicting Housing Market Sales Price
### Ames Iowa: Alternative to the Boston Housing Data Set

## Problem Statement
Develop a multilinear regression that helps home owners and contractors determine what features add value to homes in Ames, Iowa. The goal is to have a general model that can be easily interpreted and then generate a more sophisticated model to improve performance.

## Data Dictionary
|Feature|Type|Dataset|
|---|---|---|
|**saleprice**|*float*| The price of the house when sold | 
|**neighborhood**|*object*| The neighborhood name |
|**paved_drive**|*object*| Paved, partially paved, or not paved driveway|
|**gr_liv_area**|*float*| Above ground living area sq. ft.|
|**overall_qual**|*int*| Quality of building materials used|
|**garage_area**|*float*| Size of the garage in sq. ft.|
|**total_bsmt_sf**|*float*| Size of the basement in sq. ft.| 
|**year_built**|*int*| The year the home was built| 
|**year_remod_add**|*int*| Year remodeled or added onto the home|
|**mas_vnr_area**|*float*| Masonry veneer type |
|**fireplaces**|*int*| If the home has a fireplace or not |
|**bsmtfin_sf_1**|*float*| Finished basement sq. ft.|
|**central_air**|*int*| Does the home have central air, Yes or no|

## Inferences
- Having a fireplace increases home sale price by $7,000, while holding other features constant and not taking in consideration the type of fireplace. Home owners and contractors may use this information to determine if its worth it to add a fire place based on the cost of installing one. 

- For every increase in one Overall Quality rating, Sale Price increases by 13,000 dollars. with 10 ordinal rating, the difference between a 0 and 10 is $130,000. 

- Garage Area impact is almost double that of basement area. An increase in 1 square foot returns a 21 dollar increase in sale price for basement total areas, whereas garage area return $37.

- Basement Finished Area doesn't have that much more of an impact as basement area with an increase of 24 dollars per square foot instead of $21. Finishing basements may not be worth the costs according to this model. 

- Suprisingly, the coefficients for Central AC did not contribute to predicting a higher price. Having central air resulted in a decreased value of 3,900 dollar. Taking a closer look at the distribution, a large number of lower valued homes have central air. Since more sale prices are concentrated in the middle, having an central air lowers to predictions to more average to lower prices. 

## Conclusions on Model Performance
Ridge has a slightly better test score and has less variability over cross validation. Ridge may work better because of the large number of variables. The log scale in the loss function for ridge may be better for such a high quantity of features. Log transformation tend to work well with features that increase at a higher rate as things get larger. We see this relationship with price. Because of the high number of features in this MLR model, the expodential like characteristics of the higher valued homes, and the increasinly high variance in the residuals for expensive houses explain why the Ridge regularization performs better.

The lasso regularization model only reduced one feature to zero. I purposely left out features that seemed likely to be correlated with one another. It was beneficial to run both models to determine if more feature reduction was neccesary.

The ElasticNet model did not seem to help performace.

Overall, the model performed well accounting for 88% variability. I do not see an issue with overfitting. This model would not generalize well to other location because of the use of neighborhood features and due to the specific sample from which the dataset was taken from. The impact that above ground living area has on price in Iowa is drastically different from larger cities like Chicago.

This model would only work well for Ames, Iowa. 