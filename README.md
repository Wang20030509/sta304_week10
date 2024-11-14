# sta304_week10

CREATE TABLE wanted_data AS
SELECT
           p.id AS product_id,
		   p.vendor AS product_vendor,
		   CAST (r.current_price AS NUMERIC) AS current_price,
		   CAST (r.old_price AS NUMERIC) AS old_price
FROM
           product p
JOIN
           raw r
ON
           p.id = r.product_id;
		   
-- Create analysis dataset
CREATE TABLE analysis_data AS
SELECT
           vendor,
		   current_price,
		   old_price
FROM
           wanted_data
WHERE
           vendor IS NOT NULL
		   AND current_price IS NOT NULL
		   AND old_price IS NOT NULL