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
