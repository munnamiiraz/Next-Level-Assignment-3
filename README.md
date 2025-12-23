# Vehicle Rental System

## About the Project

This is a database assignment for managing vehicle rentals. I created three tables - Users, Vehicles, and Bookings - to handle the rental system.

## Database Tables

**Users**
- Stores user information like name, email, phone
- Has role field for Admin or Customer
- Email is unique for each user

**Vehicles**
- Contains vehicle details (name, type, model)
- Registration number is unique
- Tracks if vehicle is available, rented, or in maintenance

**Bookings**
- Links users with vehicles they booked
- Has start date, end date, and total cost
- Status shows if booking is pending, confirmed, completed or cancelled

## Relationships

Users and Bookings have 1:N relationship (one user can book multiple times)
Vehicles and Bookings have 1:N relationship (one vehicle can be booked multiple times)

## Queries

**Query 1 - JOIN**
Gets booking details with customer name and vehicle name. I used INNER JOIN to connect Bookings table with Users and Vehicles tables.

```sql
SELECT 
    b.booking_id,
    u.name AS customer_name,
    v.name AS vehicle_name,
    b.start_date,
    b.end_date,
    b.status
FROM Bookings b
INNER JOIN Users u ON b.user_id = u.user_id
INNER JOIN Vehicles v ON b.vehicle_id = v.vehicle_id;
```
Result: Shows all bookings with customer and vehicle names instead of just IDs

**Query 2 - EXISTS**
Finds vehicles that were never booked. Used NOT EXISTS to check if vehicle has no bookings.

```sql
SELECT 
    vehicle_id,
    name,
    type,
    model,
    registration_number,
    rental_price,
    status
FROM Vehicles v
WHERE NOT EXISTS (
    SELECT 1 
    FROM Bookings b 
    WHERE b.vehicle_id = v.vehicle_id
);
```
Result: Returns vehicles that have no booking records

**Query 3 - WHERE**
Gets available cars only. Used WHERE with two conditions - type must be car and status must be available.

```sql
SELECT 
    vehicle_id,
    name,
    type,
    model,
    registration_number,
    rental_price,
    status
FROM Vehicles
WHERE type = 'car' AND status = 'available';
```
Result: Shows cars that are currently available for rent

**Query 4 - GROUP BY and HAVING**
Finds vehicles with more than 2 bookings. Used GROUP BY to group by vehicle, COUNT to count bookings, and HAVING to filter results.

```sql
SELECT 
    v.name AS vehicle_name,
    COUNT(b.booking_id) AS total_bookings
FROM Vehicles v
INNER JOIN Bookings b ON v.vehicle_id = b.vehicle_id
GROUP BY v.vehicle_id, v.name
HAVING COUNT(b.booking_id) > 2;
```
Result: Shows vehicles that have been booked more than 2 times

## How to Run

Just run the queries.sql file in any SQL editor. It will create database, tables. Then insert data and run all queries.
