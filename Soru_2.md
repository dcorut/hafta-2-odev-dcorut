# Soru 2) 1980’den itibaren herhangi bir spor grubunda üst üste 3 veya daha fazla madalya almış atletleri bulalım.

```
select * from(
with athlete_medal as
(
  select
    ANY_VALUE(year) as year,
    ANY_VALUE(country) as country,
    sport,
    ANY_VALUE(athlete) as athlete
  from `dsmbootcamp.sample.summer_medals`
  where year >= 1980 and athlete is not null
  group by sport
  order by year, country
)
SELECT
  year,
  athlete,
  country,
  sport,
 lead(athlete,1) over(partition by year order by year) a,
 lead(athlete,2) over(partition by year order by year) b
FROM athlete_medal)

```
