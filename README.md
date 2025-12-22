# Vehicle Rental System - Database Assignment

## Project Overview

This project implements a database system for managing vehicle rentals. The system handles users, vehicles, and booking information with proper relationships between tables.

## Database Structure

The database consists of three main tables:

**Users Table**
- Stores customer and admin information
- Each user has a unique email address
- Contains user role (Admin or Customer)

**Vehicles Table**
- Stores information about available vehicles
- Includes cars, bikes, and trucks
- Tracks vehicle availability status
- Each vehicle has a unique registration number

**Bookings Table**
- Records rental bookings
- Links users with vehicles
- Tracks booking dates and status
- Stores total cost for each booking

## Relationships

- One user can make multiple bookings (1:N relationship)
- One vehicle can have multiple bookings (1:N relationship)
- Each booking belongs to one user and one vehicle

## SQL Queries Explanation

**Query 1: JOIN**
This query retrieves all booking information along with the customer name and vehicle name. It uses INNER JOIN to combine data from three tables (Bookings, Users, and Vehicles) to show complete booking details.

**Query 2: EXISTS**
This query finds all vehicles that have never been booked. It uses NOT EXISTS to check if there are no matching records in the Bookings table for each vehicle.

**Query 3: WHERE**
This query retrieves all available vehicles of a specific type. It uses WHERE clause with multiple conditions to filter vehicles by type (car) and availability status (available).

**Query 4: GROUP BY and HAVING**
This query finds vehicles that have more than 2 bookings. It uses GROUP BY to group bookings by vehicle, COUNT to calculate total bookings, and HAVING to filter only vehicles with more than 2 bookings.

## How to Run

1. Open any SQL database management tool
2. Run the queries.sql file
3. The file will create the database, tables, insert sample data, and execute all queries

## Sample Data

3 users, 4 vehicles, and 4 bookings are included for testing.

## Query Results

- Query 1: Shows 4 bookings with customer and vehicle details
- Query 2: Shows 2 vehicles that have no bookings
- Query 3: Shows 1 available car
- Query 4: Shows vehicles with more than 2 bookings
