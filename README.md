# Transport-demand-prediction
# Project Summary
# Objective
In summary, the project aims to create a model that predicts the number of seats sold for each ride on specific routes, dates, and times for Mobiticket. The routes originate from 14 towns towards Lake Victoria, ending in Nairobi. The journey takes around 8 to 9 hours to reach the outskirts of Nairobi and an additional 2 to 3 hours to reach the main bus terminal. Passengers are influenced by traffic conditions during their travel into the city and onward to their final destinations in Nairobi. Understanding these patterns can help improve service planning and optimize operations for Mobiticket.

# Variables in data
ride_id: unique ID of a vehicle on a specific route on a specific day and time.
seat_number: seat assigned to ticket
payment_method: method used by customer to purchase ticket from Mobiticket (cash or Mpesa)
payment_receipt: unique id number for ticket purchased from Mobiticket
travel_date: date of ride departure. (MM/DD/YYYY)
travel_time: scheduled departure time of ride. Rides generally depart on time. (hh:mm)
travel_from: town from which ride originated
travel_to: destination of ride. All rides are to Nairobi.
car_type: vehicle type (shuttle or bus)
max_capacity: number of seats on the vehicle

# Data Wrangling
Created target variable 'number_of_ticket'
Dropped constant and non essential columns
Used travel_date and travel_time columns to extract and create datetime related features
Created period feature from travel time for data visualization

# Feature Engineering and Data Preprocessing
To enhance the performance of the model, additional features have been generated. These new features aim to provide more relevant information and contribute to improved predictions. These include:

Some columns travel_month, travel_day_of_year, travel_day_of_month and time_period_of_day have skewed data, to handle this, new weight wise columns have been created by taking log transformation.
How frequently the bus arrives at every source destination can be a major factor effecting the number of tickets sold on that route. Hence, the following columns are created based on the frequency of bus/shuttle arriving :
Time_gap_btw_0_1_next_bus
Time_gap_btw_0_1_previous_bus
Time_gap_btw_0_2_next_bus
Time_gap_btw_0_2_previous_bus
Time_gap_btw_0_3_next_bus
Time_gap_btw_0_3_previous_bus
Time_gap_btw_next_previous_bus
The distance of source to destination (Nairobi) can also be a major factor effecting the number of tickets, hence, a new column called distance_to_destination is created containing distances of all the 14 sources to Nairobi.
To deal with multicollinearity, few of the columns are dropped.
Categorical encoding is done on few columns and finally data is split into training and test.


# ML Model Implementation

Five models are implemented to predict the transport demand to Nairobi. These include:
Linear Models:
Linear Regression
Lasso Regression (L1)
Ridge Regression (L2)
Ensemble Models:
Random Forest
XGBoost
To improve model performance, k-fold cross validation and hyperparamter tuning is done using GridSearchCV.
Evaluation metrics such as MSE, RMSE, MAE, MAPE, R2 score and Adjusted R2 score is used to compare model performance
Final model comparision on test data accuracy:

Linear regression :- 0.35
Lasso:- 0.248
Ridge:- 0.356
Random Forest Regression:- 0.941
XG Boost:- 0.894

# Impact Quantification
This project resulted in hyperparameter tuned Random Forest based predictive model, achieving an R2 score of 94.2% for training data and 94.3% for test data.


