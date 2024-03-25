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

https://private-user-images.githubusercontent.com/83869822/257723169-e544d398-d339-43f5-8e35-628f0c4fe5f5.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MTEzNjcyOTYsIm5iZiI6MTcxMTM2Njk5NiwicGF0aCI6Ii84Mzg2OTgyMi8yNTc3MjMxNjktZTU0NGQzOTgtZDMzOS00M2Y1LThlMzUtNjI4ZjBjNGZlNWY1LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNDAzMjUlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjQwMzI1VDExNDMxNlomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWY1YWQ0MDRlODQ3ZDA3ZTJkZGNjMGUwYWNlZThhNzhkMzQyNjZmMTlmMTZmODllOTg5NzRlNWVjOGQxMjIyMGImWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JmFjdG9yX2lkPTAma2V5X2lkPTAmcmVwb19pZD0wIn0.kKlcar6vxOblRM3Un65--V0jpj4LJpHiysHtwP_19mM



