# Question 1
docker --help
docker build --help
--iidfile string

# Question 2
winpty docker run -it --entrypoint=bash python:3.9
pip list
3

# Question 3
SELECT COUNT(1)
FROM green_taxi_data
WHERE DATE_TRUNC('DAY',lpep_pickup_datetime) = '2019-01-15'  
AND DATE_TRUNC('DAY',lpep_dropoff_datetime) = '2019-01-15' 
20530

# Qustion 4
SELECT lpep_pickup_datetime, (lpep_dropoff_datetime-lpep_pickup_datetime) AS duration
FROM green_taxi_data
WHERE DATE_TRUNC('DAY',lpep_pickup_datetime) = '2019-01-18'  
OR DATE_TRUNC('DAY',lpep_pickup_datetime) = '2019-01-28'  
OR DATE_TRUNC('DAY',lpep_pickup_datetime) = '2019-01-15'  
OR DATE_TRUNC('DAY',lpep_pickup_datetime) = '2019-01-10'  
ORDER BY duration DESC;
2019-01-15

# Question 5
SELECT count(1)
FROM green_taxi_data
WHERE DATE_TRUNC('DAY',lpep_pickup_datetime) = '2019-01-01'  
AND passenger_count = 2

SELECT count(1)
FROM green_taxi_data
WHERE DATE_TRUNC('DAY',lpep_pickup_datetime) = '2019-01-01'  
AND passenger_count = 3

2: 1282 ; 3: 254

# Question 6
SELECT "Zone" FROM zone_taxi_data
WHERE "LocationID" = (
	SELECT "DOLocationID"
		FROM green_taxi_data gd
		JOIN
			zone_taxi_data zd
		ON
			gd."PULocationID" = zd."LocationID"
		WHERE zd."Zone" = 'Astoria'
		ORDER BY gd.tip_amount DESC LIMIT 1)
	ORDER BY gd.trip_distance DESC LIMIT 1)

Long Island City/Queens Plaza