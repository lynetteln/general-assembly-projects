# Project 2: PREDICTING SALE PRICES OF HOMES IN AMES, IOWA

### Problem Statement
The prediction of housing prices in any city is extremely important to all parties involved in the transaction. If buyers from another city want to move into Ames, they will need to predict what prices will be to best facilitate their move into their new home. On the other hand, houseowners and real estate agents wanting to sell a unit will need to know what the best price is that they can list the home at.

### Overview of the Data
The training set used in this project involves about 2,000 samples (82 columns total - 23 nominal, 23 ordinal, 14 discrete, and 20 continuous variables) Data is initially cleaned by dropping features with large amounts of nulls and points with obvious outliers.

Categorical features are either one-hot-encoded or label-encoded. This is later further split into training and testing sets, and fitted to Linear, Ridge, and Lasso regressions. The metric used to assess these models is the Root Mean Squared Error (RMSE), and the best performing model would have the lowest RMSE.

||dataType|Category|Description|
|---|---|---|---|
|**pid**|*int*|Nominal|Parcel Identification number | 
|**ms_subclass**|*object*|Nominal|Identifies the type of dwelling involved in the sale. Values are bin_01 to bin_10 defined in chart below| 
|**lot_frontage**|*float*|Continuous|Linear feet of street connected to property| 
|**lot_area**|*int*|Continuous|Lot size in square feet| 
|**lot_shape**|*int*|Ordinal|General shape of property| 
|**utilities**|*int*|Ordinal|Type of utilities available| 
|**lot_config**|*object*|Nominal|Lot configuration| 
|**land_slope**|*int*|Ordinal|Slope of property| 
|**neighborhood**|*object*|Nominal|Physical locations within Ames city limits (map available)| 
|**house_style**|*object*|Nominal|Style of dwelling| 
|**overall_qual**|*int*|Ordinal|Rates the overall material and finish of the house| 
|**overall_cond**|*int*|Ordinal|Lot size in square feet| 
|**year_built**|*int*|Discrete|Original construction date| 
|**year_remod/add**|*int*|Discrete|Remodel date (same as construction date if no remodeling or additions)| 
|**mas_vnr_type**|*object*|Nominal|Masonry veneer type| 
|**mas_vnr_area**|*float*|Continuous|Masonry veneer area in square feet| 
|**exter_qual**|*object*|Ordinal|Evaluates the quality of the material on the exterior| 
|**exter_cond**|*int*|Ordinal|Evaluates the present condition of the material on the exterior| 
|**foundation**|*object*|Nominal|Type of foundation| 
|**bsmt_qual**|*int*|Ordinal|Evaluates the height of the basement| 
|**bsmt_cond**|*int*|Ordinal|Evaluates the general condition of the basement| 
|**bsmt_exposure**|*int*|Ordinal|Refers to walkout or garden level walls| 
|**bsmtfin_type_1**|*int*|Ordinal|Rating of basement finished area| 
|**bsmtfin_sf_1**|*float*|Continuous|Type 1 finished square feet| 
|**bsmtfin_type_2**|*int*|Ordinal| Rating of basement finished area (if multiple types)| 
|**bsmtfin_sf_2**|*float*|Continuous|Type 2 finished square feet| 
|**heating_qc**|*int*|Nominal|Type of heating| 
|**electrical**|*int*|Ordinal|Electrical system| 
|**1st_flr_sf**|*int*|Continuous|First Floor square feet| 
|**gr_liv_area**|*int*|Continuous| Above grade (ground) living area square feet| 
|**bsmt_full_bath**|*float*|Discrete| Basement full bathrooms| 
|**full_bath**|*float*|Discrete|Full bathrooms above grade| 
|**half_bath**|*float*|Discrete| Half baths above grade| 
|**bedroom_abvgr**|*float*|Discrete|Bedrooms above grade (does NOT include basement bedrooms)| 
|**kitchen_abvgr**|*float*|Discrete|Kitchens above grade| 
|**kitchen_qual**|*int*|Ordinal|Kitchen quality| 
|**totrms_abvgrd**|*int*|Discrete|Total rooms above grade (does not include bathrooms)| 
|**functional**|*int*|Ordinal|Home functionality (Assume typical unless deductions are warranted)| 
|**fireplaces**|*int*|Discrete| Number of fireplaces| 
|**fireplace_qu**|*int*|Ordinal|Fireplace quality| 
|**garage_type**|*object*|Nominal|Garage location| 
|**garage_yr_blt**|*int*|Discrete|Year garage was built| 
|**garage_finish**|*int*|Ordinal| Interior finish of the garage| 
|**garage_area**|*float64*|Continuous|Size of garage in square feet| 
|**garage_qual**|*int*|Discrete| Garage quality| 
|**garage_cond**|*int*|Ordinal|Garage condition| 
|**paved_drive**|*int*|Ordinal|Paved driveway| 
|**wood_deck_sf**|*float*|Continuous| Wood deck area in square feet| 
|**open_porch_sf**|*float*|Continuous|Open porch area in square feet| 
|**enclosed_porch**|*float*|Continuous|Enclosed porch area in square feet| 
|**screen_porch**|*float*|Continuous| Screen porch area in square feet| 
|**mo_sold**|*int*|Discrete|Month Sold (MM)| 
|**sale_type**|*object*|Nominal|Type of sale| 
|**saleprice**|*float*|Continuous|Price of sale| 

## ms_subclass
| BIN No. | Subclasses |
| --- | --- |
|bin1|20 & 75|
|bin2|30|
|bin3|60|
|bin4|70|
|bin5|80 & 85|
|bin6|50 & 90|
|bin7|120|
|bin8|190 & 40|
|bin9|160 & 180|
|bin10|All other subclasses (45 & 150)|

## ONE-HOT Encoding

Columns that were one-hot encoded include: 'ms_subclass','lot_config','neighborhood','house_style',
'mas_vnr_type','foundation','garage_type','sale_type'

# Modelling
After modelling, the primary model used for prediction was the Lasso Model. Though the Root Mean-Squared-Errors (RMSEs) for both the Lasso and Ridge were close in magnitude, the Lasso model helped better with noise reduction by removing features that had coefficients of 0.

The Kaggle scoring on this model was almost 28,000. The metric used here was RMSE as well, meaning that this model can be improved significantly by further feature engineering/model optimization.





