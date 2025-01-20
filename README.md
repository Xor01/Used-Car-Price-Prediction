# Project Summary

This Jupyter Notebook is focused on analyzing and modeling a dataset of used cars. The notebook includes data preprocessing, exploratory data analysis (EDA), feature engineering, and model training and evaluation. Below is a detailed description of each section and the corresponding code cells.

## Data Preprocessing and Exploration

1. **Importing Libraries and Loading Data**

   - Libraries such as `pandas`, `matplotlib.pyplot`, and `seaborn` are imported.
   - The dataset `used_cars.csv` is loaded into a DataFrame `df`.
   - Initial exploration of the dataset is performed using `head()`, `info()`, `describe()`, and `isnull().sum()` methods.

2. **Data Visualization**

   - Various plots are created to visualize the distribution of car prices, mileage, count of cars by brand and fuel type, and the relationship between car price and model year.
   - Histograms, count plots, scatter plots, and box plots are used for visualization.

3. **Handling Missing Values**

   - Missing values in the `fuel_type`, `accident`, and `clean_title` columns are filled with appropriate values.
   - The updated count of missing values is printed.

4. **Feature Engineering**
   - Encoding categorical variables such as `brand`, `model`, `fuel_type`, `transmission`, `ext_col`, and `int_col` using techniques like label encoding and one-hot encoding.
   - Creating new features such as `encoded_brand`, `engine_displacement`, and `color_changed`.
   - Standardizing numerical features using `StandardScaler`.

## Model Training and Evaluation

1. **Splitting Data**

   - The dataset is split into training and testing sets using `train_test_split`.

2. **Training Models**

   - Various regression models are trained, including `Ridge`, `ridgeCV`, `LinearRegression`, `RandomForestRegressor`, `LassoCV`, and `XGBRegressor`.
   - Recursive Feature Elimination (RFE) is used to select the best features for each model.

3. **Evaluating Models**

   - Models are evaluated using metrics such as Mean Squared Error (MSE) and R-squared (R²).
   - Residual plots, actual vs predicted plots, feature importance plots, error distribution plots, and learning curves are generated for each model.

4. **Handling Outliers**
   - Outliers in the `price` column are removed using Z-scores.

## Final Model Training and Evaluation

- The cleaned dataset is used to train and evaluate the models again, following the same process as before.

This notebook provides a comprehensive workflow for analyzing and modeling a used car dataset, including data preprocessing, visualization, feature engineering, and model evaluation.

## Handling Data

1. **Data Cleaning**

   - The `milage` column is cleaned by removing unwanted characters and converting it to a numerical format.
   - The `engine` column is processed to extract numerical values for engine displacement and the number of cylinders.

2. **Encoding and Standardization**
   - Categorical variables are encoded using one-hot encoding and mean encoding.
   - Numerical features are standardized using `StandardScaler` to ensure they have a mean of 0 and a standard deviation of 1.

## Impact of Removing Outliers

Removing outliers from the `price` column significantly improved the accuracy of the models. By filtering out data points with Z-scores beyond a threshold of 3, the dataset became more representative of the general trend, reducing the noise caused by extreme values. This led to better model performance, as indicated by improved evaluation metrics.

## Model Performance

The performance of different models before and after removing outliers is summarized below:

- **Ridge Regression**

  - Before: MSE = 878504764.4467131, R² = 0.52
  - After: MSE = 511764521.959076, R² = 0.62

- **RidgeCV**

  - Before: MSE = 878639941.3446958, R² = 0.52
  - After: MSE = 511598290.46433365, R² = 0.62

- **Linear Regression**

  - Before: MSE = 878654974.1379756, R² = 0.52
  - After: MSE = 511784636.2424409, R² = 0.62

- **Random Forest Regressor**

  - Before: MSE = 335863729.1024245, R² = 0.81
  - After: MSE = 203842098, R² = 0.85

- **LassoCV**

  - Before: MSE = 852003416.7752014, R² = 0.53
  - After: MSE = 511792234.8866373, R² = 0.62

- **XGBRegressor**
  - Before: MSE = 1036914082.5827103, R² = 0.43
  - After: MSE = 167383529.085204, R² = 0.88

The removal of outliers resulted in lower Mean Squared Error (MSE) and higher R-squared (R²) values across all models, indicating better fit and predictive accuracy.
