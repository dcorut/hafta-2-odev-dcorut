# Soru 3

Damla Cörüt

Yapamadım :(

```
SELECT 
  TIMESTAMP_SECONDS(5*60 * DIV(UNIX_SECONDS(view_ts), 5*60)) view_period,
  count(distinct deviceid) active_user_count
FROM sample.pageview
GROUP BY view_period
order by view_period limit 10
```
