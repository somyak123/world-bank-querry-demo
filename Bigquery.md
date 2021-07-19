# world bank
## Number of countries
```sql
SELECT count(distinct (country_code)) FROM `patents-public-data.worldbank_wdi.wdi_2016` LIMIT 1000
```
## Min and max year
```sql
SELECT max(year) as max_year,min(year) as min_year FROM `patents-public-data.worldbank_wdi.wdi_2016` LIMIT 1000
```
## Min Surface area for all countries.
```sql
SELECT min(indicator_value) as minimum_surface_area
, max(indicator_value) as maximum_surface_area
, avg(indicator_value) as average_surface_area 
FROM `patents-public-data.worldbank_wdi.wdi_2016` 
where 1=1 
--and lower(indicator_name) like '%surface%'
and indicator_name = 'Surface area (sq. km)'
```
## For every country
```sql
SELECT
  country_name,
  MIN(indicator_value) AS minimum_surface_area,
  MAX(indicator_value) AS maximum_surface_area,
  AVG(indicator_value) AS average_surface_area
FROM
  `patents-public-data.worldbank_wdi.wdi_2016`
WHERE
  1=1
  --and lower(indicator_name) like '%surface%'
  AND indicator_name = 'Surface area (sq. km)'
GROUP BY
  country_name
ORDER BY
  average_surface_area DESC,
  country_name  -- double sort - first by avg_sa descending and then by country name
  ```
