# uci-secom
Classification model for a semiconductor manufacturing dataset


Given features associated with sensors etc., classify whether the manufacturing process is pass(-1) or fail(+1).

Sub-task list: 
- Data wrangling to optimize for missing values, NaNs and constant values.
- Classification using full feature list with ridge classifier and ten-fold cross validation.
- Using feature selection techniques to determine top K features for the classification task.

### Data wrangling

- Total features: 590
- Total entries/samples: 1567
- Processing: To remove feature columns with more than 250 missing 	values.
	Use interpolation to fill missing values for the rest of the columns.
	Dropping columns with constant feature values (0 standard deviation)
- Features considered for training: 422
  Total number of fails: 104
  Total number of pass: 1463

### Basic Classification Pipeline
- StandardScaler to squeeze the data within (-1, 1) range.
- Undersampling pass cases to achieve a balancing effect.
- Use RidgeClassfier to train on the scaled data with 10-fold cross validation.
- Results on a subset used for testing: 
	BER: 35.8%
	Fail class: 13/28
	Pass class: 401/490

### Feature Selection and Classification Pipeline
- Applying univariate feature selection to identify top 100 best features for classification.
- Use the same classification scheme as above to report results.
- Results on a subset used for testing: 
	BER: 33.87%
	Fail class: 16/28
	Pass class: 368/490


