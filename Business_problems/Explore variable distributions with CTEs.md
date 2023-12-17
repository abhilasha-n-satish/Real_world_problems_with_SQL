## Exploring variable distributions with CTEs

![B1](images/2.png)

### The Solution: 

``` SQL
-- SQL request(s)​​​​​​‌​‌​​‌‌​​​‌‌‌‌​​​​​​‌​‌‌‌ below
with click_links as (
select 
userid, count(EVENTID) as num_link_clicks
from 
frontendeventlog
where eventid = 5
group by userid)

select 
num_link_clicks, count(userid) as num_users
from click_links
group by num_link_clicks
```

### Solution Screenshot:

![B1](images/S_2.png)
