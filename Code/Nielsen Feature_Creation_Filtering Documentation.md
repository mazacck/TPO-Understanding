### Nielsen Feature Creation Filtering Functions:
- Output location: ‘Output/Feature_Creation_Filtering’
- Standalone feature creation functionsdf['month'] = pd.DatetimeIndex(df['birth_date']).month
1.	Trend
2.	Median baseprice
3.	EDLP
4.	TPR discount and Lag1 and Lag2
5.	Seasonality index
6.	Category sales: Sum of variable values based on user input granularity.
7.	ACV selling
8.	Category trend:
9.	Time trend ratio: Ratio of current period variable value and previous period variable value.

### Master function ‘feature_creation’
-	Function to combine all the above standalone functions and return a dataframe with every feature added in the original data.

### SKU-PPG mapping function ‘sku_to_ppg’
-	Function to group the SKUs on certain conditions to form PPGs.
-	Level1 is created based on input granularity and the packsize within the granularity.
-	The items with similar packsize within the granularity are grouped together. The similarity range is by default 0.05 for 5% 
-	Level2 is created on top of Level1 based on the average selling price of SKUs in the calendar year.
-	The items within Level1 with similar average selling price are grouped together. The similarity range is by default 0.05 for 5%
-	The range for both packsize and average selling price can be changed by the user as per requirement.
-	The SKUs within Level1 that are promoted together are grouped together as Level2.

### Filtering function ‘retailer_modelling_data_creation’
-	Modelling dataset creation based on certain threshold values.
-	PPG item/SKU summary for inclusion/exclusion in the modelling dataset also given as output. 
