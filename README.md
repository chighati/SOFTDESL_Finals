# House Prices Analysis and Prediction

## Dataset Description
The dataset used in this project is sourced from [House Prices in the US](https://raw.githubusercontent.com/datasets/house-prices-us/refs/heads/main/data/cities-month-NSA.csv). It contains monthly housing price index data for various cities in the United States, spanning multiple years.

## Summary of Findings
Through exploratory data analysis and visualization, key insights about the trends in housing prices across different cities were uncovered. Notably, the average house prices have shown significant variation over time, with certain cities experiencing peak prices at specific intervals.

## Data Preprocessing
1. **Null Value Handling**:
   - The dataset was examined for null values, and the `MN-Minneapolis` and `NV-Las Vegas` columns were dropped due to missing data.
   - I checked the data under the column `MN-Minneapolis` and half of it was null so I decided to drop the whole column, on the other hand `NV-Las Vegas` had many 0 values from the start so I decided to remove it since that would count as if it was free and it would ruin the predictive model I am trying t o build.
2. **Duplicate Records**:
   - Duplicate records based on the `Date` column were identified and managed, and it turns out there were none, which is a good thing.

## Exploratory Data Analysis
The exploratory data analysis involved:
- Checking the dataset's structure and summary statistics.
- Analyzing the price trends of selected cities over time.

## Visualization
1. **House Prices Over Time**:
   - Two subsets of cities were analyzed, and the maximum prices for each city were highlighted on the plots.
   - The reason I split them into 2 groups is for them to be more visible and the colors don't merge that much for visualization

   **Interpretation**:
   - This visualization shows how housing prices fluctuate in different metropolitan areas, with peaks indicating the most expensive periods.

2. **Average House Prices**:
   - A separate visualization highlighted the date with the highest average house price across all selected cities.
   - I used "df.drop(columns=['Date']).mean(axis=1)" to go and get first the average price for each date across all the cities, date was dropped since it not relevant here.
   - I used "average_prices_df = pd.DataFrame({'Date': df['Date'], 'Average_Price': average_prices})" to create a DataFrame for dates and their corresponding average prices
   - highest_avg_price_index = average_prices_df['Average_Price'].idxmax()  # Finds the index of the highest average price
   - highest_avg_price_date = average_prices_df.loc[highest_avg_price_index, 'Date']  # Gets the date corresponding to that index
   - highest_avg_price_value = average_prices_df['Average_Price'].max()  # Retrieves the highest average price value


   **Interpretation**:
   - The plot indicates overall trends in house prices, revealing periods of growth or decline in the housing market.
   - It also highlights which date has the average house price in the US.

## Model Development
Several regression algorithms were implemented to predict house prices based on the date:

1. **Decision Tree Regressor**
2. **Random Forest Regressor**
3. **XGBoost Regressor**
4. **Gradient Boosting Regressor**
5. **AdaBoost Regressor**
6. **Support Vector Regressor**
7. **K-Neighbors Regressor**

- this were the remaining models since I excluded everything that was below the 85% passing mark for accuracy.

The feature used was a numerical representation of the date, and the target variable was the average house price.

## Model Evaluation
Each model was evaluated based on:
- **Mean Squared Error (MSE)**
- **Mean Absolute Error (MAE)**
- **R² Score**

Decision Tree:
 - Mean Squared Error: 0.93
 - Mean Absolute Error: 0.68
 - R² Score: 99.94%

Random Forest:
 - Mean Squared Error: 0.33
 - Mean Absolute Error: 0.38
 - R² Score: 99.98%

XGBoost:
 - Mean Squared Error: 1.18
 - Mean Absolute Error: 0.71
 - R² Score: 99.92%

Gradient Boosting:
 - Mean Squared Error: 0.88
 - Mean Absolute Error: 0.65
 - R² Score: 99.94%

AdaBoost:
 - Mean Squared Error: 14.23
 - Mean Absolute Error: 2.87
 - R² Score: 99.09%

Support Vector Regressor:
 - Mean Squared Error: 163.17
 - Mean Absolute Error: 7.45
 - R² Score: 89.59%

K-Neighbors Regressor:
 - Mean Squared Error: 0.68
 - Mean Absolute Error: 0.65
 - R² Score: 99.96%

### Results Summary:
- Models were fitted, and performance metrics were calculated.

**Conclusion:**
In this project, I looked at housing prices in the U.S. over time and used different machine learning models to try to predict future prices based on the trends we found. After cleaning up the data and analyzing it, I saw that housing prices in different cities vary a lot, with certain areas hitting peak prices at different times. The visualizations made it clear how housing prices move in each city, which helps us understand how the market has shifted over the years.

When it came to building predictive models, the Random Forest Regressor and K-Neighbors Regressor stood out as the best performers. Both had really high accuracy (R² scores above 99%) and low error rates, making them reliable for predicting future prices. On the other hand, the Support Vector Regressor didn’t do as well, possibly because it struggled with the non-linear trends in the data.

### Contributors:
CPE-401, Rafael Luis Canlas

