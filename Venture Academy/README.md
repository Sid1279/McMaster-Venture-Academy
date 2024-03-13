# Power Prediction: ARIMA Time Series Forecasting Project

This project focuses on time series forecasting using the ARIMA (AutoRegressive Integrated Moving Average) model. The goal is to predict future values based on historical data.

## Usage
1. Ensure that the required libraries (`numpy`, `pandas`, `matplotlib`, `statsmodels`) are installed.
   ``` shell
   pip install numpy pandas matplotlib statsmodels
   ```
2. Prepare a time series dataset in CSV format and update the code to specify the correct file path in the `read_csv()` function.
3. Run the code, and it will load the dataset, split it into train and test sets, apply the ARIMA model for forecasting, and display a line graph comparing the actual and predicted values.
4. Analyze the graph to assess the accuracy of the ARIMA model in forecasting future values.

This project can be used for various time series forecasting tasks, such as predicting stock prices, energy consumption, or any other data that exhibits a temporal pattern.


## Movie Recommendation System

### Dataset: https://grouplens.org/datasets/movielens/

This project focuses on building a movie recommendation system using collaborative filtering and the Pearson correlation coefficient. The goal is to recommend movies to users based on their ratings and the ratings of other users.

## Usage

To use this movie recommendation system, follow these steps:

1. Ensure that the required libraries (`pandas`, `math`) are installed.
   ``` shell
   pip install pandas math
   ```
3. Prepare two CSV files: 'ratings.csv' and 'movies.csv', containing user ratings and movie information, respectively.
4. Update the code to specify the correct file paths in the `read_csv()` function for both ratings and movies.
5. Run the code, and it will load the ratings and movies data, define the necessary functions, and generate movie recommendations.
6. Examine the movie recommendations for a specific user, which will be displayed on the console.

This movie recommendation system can be customized and expanded upon to include additional features, such as collaborative filtering with matrix factorization or content-based filtering using movie genres or tags.
