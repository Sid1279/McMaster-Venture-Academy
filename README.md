# Lane Detector
This project demonstrates lane detection in videos using OpenCV and basic computer vision techniques. The goal is to detect and overlay lane boundaries in a video stream.

## Libraries
- `cv2` (OpenCV): Used for image and video processing, including edge detection, image manipulation, and line detection.
- `numpy` (NumPy): Used for numerical operations and array manipulation.
- `PIL` (Pillow): Used for reading and manipulating images.
- `matplotlib.pyplot` (Matplotlib): Used for image visualization and plotting.

## How it works
The code performs the following steps to detect and overlay lane boundaries in a video:
1. Canny Edge Detection
   - The canny() function converts the input image to grayscale and applies a Gaussian blur to reduce noise. Canny edge detection is then performed to detect edges in the image.
2. Region of Interest Selection
   - The region_of_interest() function creates a mask to define the region of interest in the image where the lane boundaries are expected.
   - The mask is created as a triangle shape at the bottom center of the image.
   - The masked image is obtained by applying the mask to the Canny edge-detected image.

3. Hough Line Detection
   - The houghLines() function applies the Hough transform to the cropped Canny image to detect lines. Detected lines are returned as a set of endpoints.

4. Line Averaging and Drawing
   - The average_slope_intercept() function calculates the average slope and intercept for left and right lane boundaries.
   - Lane lines are then created by extrapolating the averaged slope and intercept values.
   - The display_lines() function overlays the detected lane lines on a black image.
   - The addWeighted() function combines the lane lines with the original frame to create a final output image.

5. Video Processing Loop
   - The main program reads frames from a video using cv2.VideoCapture().
   - For each frame, the lane detection pipeline is applied to detect and overlay lane boundaries.
   - The processed frame is displayed, and the resulting frames are stored in an array.
   - The program terminates when the 'q' key is pressed or when the video ends.


## Usage
1. Ensure that the required libraries (cv2, numpy, PIL, matplotlib.pyplot) are installed.
   ``` shell
   pip install opencv-python numpy PIL matplotlib
   ```
   
2. Prepare/capture a video file for lane detection. Update the cap = cv2.VideoCapture("test2.mp4") line with the path to your video file.
3. Run the code, and the lane detection process will begin.
4. The program will display the processed frames in a new window, showing the lane boundaries overlaid on the original video frames.
5. Press the 'q' key to stop the program or wait until the video finishes.



# Power Prediction: ARIMA Time Series Forecasting Project

This project focuses on time series forecasting using the ARIMA (AutoRegressive Integrated Moving Average) model. The goal is to predict future values based on historical data.

## Libraries

The project utilizes the following libraries:

- `math.sqrt`: Provides the square root function for mathematical calculations.
- `numpy.split`: Splits arrays into multiple sub-arrays based on specified indices.
- `numpy.array`: Creates and manipulates arrays for numerical computations.
- `pandas.read_csv`: Reads and processes data from CSV files using DataFrames.
- `matplotlib.pyplot`: Generates visualizations, such as line plots, to analyze data.
- `statsmodels.tsa.arima_model.ARIMA`: Implements the ARIMA model for time series analysis.

## How Does It Work

The code performs the following steps to achieve time series forecasting using the ARIMA model:

1. **Data Splitting:**
   - The `split_dataset()` function splits the input dataset into training and testing sets. The training set consists of all data points except the last 328 entries, while the testing set consists of the last 328 to 6 entries.
   - The training and testing sets are converted into arrays and split further into sub-arrays based on a weekly basis.

2. **Data Transformation:**
   - The `to_series()` function converts the data into a series format that can be used by the ARIMA model. It extracts the first column from each week of data and flattens them into a single array.

3. **Model Evaluation and Prediction:**
   - The `evaluate_model()` function trains and evaluates the ARIMA model. It initializes a list called `history` with the values from the training set.
   - For each week in the testing set, the function calls the `arima_forecast()` function to generate predictions based on the historical data in `history`.
   - The predictions are appended to the `predictions` list, and the corresponding week from the testing set is added to the `history` list.
   - Finally, the function returns the array of predictions.

4. **ARIMA Forecasting:**
   - The `arima_forecast()` function takes the historical data as input. It converts the data into a series format using the `to_series()` function.
   - An ARIMA model with an order of (7, 0, 0) is created using the `ARIMA` class from the `statsmodels.tsa.arima_model` module.
   - The ARIMA model is fitted to the series data using the `fit` method, and predictions are made for the next 7 days using the `predict` method.
   - The function returns the predicted values for the next 7 days.

5. **Visualization and Result Display:**
   - The code reads a dataset from a CSV file called 'household_power_consumption_days.csv' using `read_csv()` function from pandas.
   - The dataset is split into training and testing sets using the `split_dataset()` function.
   - The `evaluate_model()` function is called to obtain the predictions for the testing set.
   - The actual values of the 11th week from the testing set and the predicted values of the 10th week are plotted on a line graph using `pyplot.plot()`.
   - The resulting graph, showing the actual and predicted values, is displayed using `pyplot.show()`.

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

This project focuses on building a movie recommendation system using collaborative filtering and the Pearson correlation coefficient. The goal is to recommend movies to users based on their ratings and the ratings of other users.

## Libraries

The project utilizes the following libraries:

- `pandas`: Used for data manipulation and analysis, particularly for reading and processing CSV files.
- `math.sqrt`: Provides the square root function for mathematical calculations.

## How It Works

The code performs the following steps to generate movie recommendations:

1. **Data Organization and Preprocessing:**
   - The code reads two CSV files, 'ratings.csv' and 'movies.csv', into pandas DataFrame objects using the `read_csv()` function.
   - The 'movies' DataFrame is split by the '|' delimiter in the 'genres' column to create a list of genres for each movie.

2. **Getter Functions:**
   - The code defines several getter functions:
     - `getRating(user, movieid)`: Retrieves the rating a user gave to a specific movie.
     - `getMovieids(user)`: Returns a list of all movie IDs that a user has rated.
     - `getMovieTitle(movieid)`: Retrieves the movie title based on a given movie ID.
     - `moviesWatched(user)`: Returns a dictionary of all movie titles that a user has rated.

3. **Pearson Correlation Calculation:**
   - The `pearsonCorrelation(user1, user2)` function calculates the similarity score (Pearson correlation coefficient) between two users.
   - It first identifies the movies that both users have watched and computes the necessary summations for the correlation calculation.
   - The Pearson correlation coefficient is returned as the similarity score between -1 and 1.

4. **Movie Recommendations:**
   - The `getRecs(user)` function generates movie recommendations for a given user.
   - It iterates over other user IDs and calculates the similarity score using the Pearson correlation.
   - If the similarity score is positive, it calculates the weighted similarity scores for movies that the other user has rated but the given user has not.
   - The ratings are then normalized, and a ranking is generated based on the weighted scores.
   - The top 10 movie recommendations (based on the ranking) are returned.

5. **Testing and Result Display:**
   - The code includes test cases for the getter functions and the recommendation system.
   - The movie recommendations for a specific user are displayed on the console.

## Usage

To use this movie recommendation system, follow these steps:

1. Ensure that the required libraries (`pandas`, `math`) are installed.
   ``` shell
   pip install pandas math
   ```
3. Prepare two CSV files: 'ratings.csv' and 'movies.csv', containing user ratings and movie information, respectively. You can find the dataset here: https://grouplens.org/datasets/movielens/
4. Update the code to specify the correct file paths in the `read_csv()` function for both ratings and movies.
5. Run the code, and it will load the ratings and movies data, define the necessary functions, and generate movie recommendations.
6. Examine the movie recommendations for a specific user, which will be displayed on the console.

This movie recommendation system can be customized and expanded upon to include additional features, such as collaborative filtering with matrix factorization or content-based filtering using movie genres or tags.
