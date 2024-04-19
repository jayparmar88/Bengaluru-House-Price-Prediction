# Bengaluru House Price Prediction:

This project aims to predict the prices of houses in Bengaluru, India, based on various features such as location, area, number of bedrooms, and more. The project is implemented in Python and utilizes machine learning techniques to build a regression model for predicting house prices.

## Table of Contents

  - [Dataset](#dataset)
  - [Data Preprocessing](#data-preprocessing)
  - [Feature Engineering](#feature-engineering)
  - [Model Selection](#model-selection)
  - [Model Evaluation](#model-evaluation)
  - [Usage](#usage)
  - [License](#license)

## Dataset

The project uses the "Bengaluru House Data" dataset, which contains information about houses in Bengaluru, including their location, area, number of bedrooms, bathrooms, and the corresponding sale prices. The dataset is available in the `Bengaluru_House_Data.csv` file.

## Data Preprocessing

The dataset undergoes several preprocessing steps to handle missing values, outliers, and data formatting issues. These steps include:

1. **Handling Missing Values**: The missing values in the `balcony` and `bath` columns are filled with their respective medians.
2. **Removing Outliers**: Outliers are removed based on the total square feet area per bedroom (bhk) and the price per square foot.
3. **Feature Engineering**: New features such as `bhk` (number of bedrooms) and `new_total_sqft` (total square feet area) are created from the existing features.
4. **Categorical Data Encoding**: Categorical features like `location`, `availability`, and `area_type` are encoded using one-hot encoding.

## Feature Engineering

The following feature engineering steps are performed:

1. **BHK (Bedrooms)**: A new column `bhk` is created to represent the number of bedrooms, extracted from the `size` column.
2. **Total Square Feet Area**: The `total_sqft` column is cleaned and converted to a numerical format, and a new column `new_total_sqft` is created to store the cleaned values.
3. **Price per Square Feet**: A new column `price_per_sqft` is added, which represents the price per square feet of the property.
4. **Location Clustering**: Locations with fewer than 10 occurrences are grouped into the 'other' category.
5. **Availability Clustering**: Availability options with fewer than 10,000 occurrences are grouped into the 'Not Ready' category.

## Model Selection

The project explores three different regression models: Linear Regression, Lasso Regression, and Decision Tree Regression. A grid search cross-validation approach is used to find the best model and its corresponding hyperparameters. Based on the evaluation, Linear Regression is selected as the best model for this problem.

## Model Evaluation

The selected Linear Regression model is trained on the preprocessed dataset, and its performance is evaluated using the test set. The model achieves a score of approximately 0.83 on the test set, indicating a good fit for predicting house prices in Bengaluru.

## Usage

The project includes a `prediction` function that can be used to predict the price of a house based on its features. The function takes the following parameters:

- `location`: The location of the property.
- `bhk`: The number of bedrooms.
- `bath`: The number of bathrooms.
- `balcony`: The number of balconies.
- `sqft`: The total square feet area of the property.
- `area_type`: The type of area (e.g., Built-up Area, Plot Area).
- `availability`: The availability status of the property (e.g., Ready to Move, Not Ready).

Example usage:

```python
price = prediction('1st Block Jayanagar', 2, 2, 2, 1000, 'Built-up  Area', 'Ready To Move')
print(f"Predicted price: {price} lakhs")
Predicted price: 173.3706060772339 lakhs
```

## License

This project is licensed under the [MIT License](LICENSE).
