DROP TABLE IF EXISTS ola;
CREATE TABLE ola(
     booking_date DATE,
	 booking_time TIME,	
	 booking_id	VARCHAR(15) PRIMARY KEY,
	 booking_status VARCHAR(20),
	 customer_id VARCHAR(15),	
	 vehicle_type VARCHAR(20),
	 pickup_location VARCHAR(30),
	 drop_location VARCHAR(30),
	 VTAT INT,	
	 CTAT INT, 
	 cancelled_rides_by_Customer VARCHAR(50),	
	 cancelled_rides_by_driver VARCHAR(50),
	 incomplete_rides VARCHAR(5),
	 incomplete_rides_reason VARCHAR(50) ,
	 booking_value FLOAT,
	 payment_method VARCHAR(15),
	 ride_distance FLOAT,
	 driver_ratings FLOAT,
	 customer_rating FLOAT);

SELECT  * FROM ola;

/*
1. Retrieve all successful bookings: 
2. Find the average ride distance for each vehicle type:
3. Get the total number of cancelled rides by customers: 
4. List the top 5 customers who booked the highest number of rides:
5. Get the number of rides cancelled by drivers due to personal and car-related issues: 
6. Find the maximum and minimum driver ratings for Prime Sedan bookings: 
7. Retrieve all rides where payment was made using UPI:
8. Find the average customer rating per vehicle type:
9. Calculate the total booking value of rides completed successfully:
10. List all incomplete rides along with the reason
*/

--1.
CREATE VIEW successful_booking AS
SELECT * FROM ola
WHERE booking_status='Success';

--2.
CREATE VIEW avg_ride_distance_by_each_vehicle AS
SELECT vehicle_type,AVG(ride_distance) AS average_distance 
FROM ola 
GROUP BY vehicle_type; 

--3.
CREATE VIEW canceled_rides_by_customer AS
SELECT COUNT(*) 
FROM ola 
WHERE booking_status='Canceled by Customer';

--4.
CREATE VIEW Top_5_customers AS
SELECT customer_id , COUNT(booking_id) AS total_rides 
FROM ola 
GROUP BY customer_id
ORDER BY 2 DESC LIMIT 5 ;

--5.
CREATE VIEW rides_cancelled_by_driver_p_c_issue AS
SELECT COUNT(*) 
FROM ola 
WHERE cancelled_rides_by_driver='Personal & Car related issue';

--6.
CREATE VIEW  min_max_rating AS 
SELECT MAX(driver_ratings) AS maximum_rating, MIN(driver_ratings) AS minimum_rating 
FROM ola 
WHERE vehicle_Type='Prime Sedan';

--7.
CREATE VIEW UPI_payment AS 
SELECT * FROM ola WHERE payment_method='UPI';

--8.
CREATE VIEW avg_customer_rating_per_vehicle AS 
SELECT vehicle_type,AVG(customer_rating) AS avg_customer_rating 
FROM ola 
GROUP BY vehicle_type;

--9.
CREATE VIEW total_successful_ride_value AS 
SELECT SUM(booking_value) AS total_booking_value 
FROM ola 
WHERE booking_status='Success';

--10.
CREATE VIEW incomplete_rides_reason AS
SELECT booking_id, incomplete_rides_reason 
FROM ola 
WHERE incomplete_rides='Yes';
