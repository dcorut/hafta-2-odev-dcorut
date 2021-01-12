# Soru 2:

Damla Cörüt

Kısmen yapabildim :(

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
  lead(athlete,1) over(partition by year order by year) as second_champ,
  lead(athlete,2) over(partition by year order by year) as third_champ,

FROM athlete_medal)

```
