# HOTEL-DATA-SQL-POWERBI-PROJECT
/* lETS FIND OUT REVENUE IS INCREASING OR NOT */     /*    */

select (stays_in_weekend_nights + stays_in_weekend_nights)* adr AS REVENUE
FROM `HOTEL.YEARS_DATA`;

/* ADD YEAR COLUMN TO COMPARE */
select arrival_date_year,(stays_in_weekend_nights + stays_in_weekend_nights)* adr AS REVENUE
FROM `HOTEL.YEARS_DATA`;

/* GROUPING BY YEAR, HOTEL */
select arrival_date_year,HOTEL,SUM((stays_in_weekend_nights + stays_in_weekend_nights)* adr) AS REVENUE
FROM `HOTEL.YEARS_DATA`
GROUP BY arrival_date_year,hotel
ORDER BY REVENUE;
/* REVENUE FOR 2020 IS LESS THAN 2019, CHECKING IF DATA IS COMPLETE FOR 2020 */
SELECT DISTINCT arrival_date_month
FROM `HOTEL.YEARS_DATA`
WHERE arrival_date_year=2020;
/* DATA TILL ONLY AUGUST 2020 IS AVL, AS PER DATA REVENUE IS INCREASING FROM YEAR 2018 TO 2019 */

/* MARKET SEGMENT DICOUNTS WILL BE APPLIED BY JOINING THE TABLE */
SELECT *
FROM `HOTEL.YEARS_DATA`AS YD
LEFT JOIN `HOTEL.MARKET_SEGMENT`AS MS ON MS.market_segment =YD.market_segment
