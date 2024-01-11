WITH user_ride_status
AS (SELECT user_id,
Max(CASE
WHEN dropoff_ts IS NOT NULL THEN 1
ELSE 0
END) AS ride_completed
FROM ride_requests
GROUP BY user_id)
SELECT Count(*) AS total_users_ride_requested
FROM user_ride_status;
