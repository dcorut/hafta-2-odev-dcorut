# Soru 1:

Damla Cörüt

```
select * from(
with gold_medals as
(
  select
    sport, 
    country,
    count(*) as medal_count
  from `dsmbootcamp.sample.summer_medals`
  where year >= 1980 and country is not null
  group by country, sport

)
select
    sport,
    medal_count,
    country,
    row_number() over(partition by sport order by medal_count desc) as rank
from gold_medals)
where rank=1 OR rank= 3 OR rank= 5

```
