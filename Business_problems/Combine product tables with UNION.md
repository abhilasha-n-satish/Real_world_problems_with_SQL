## Combining Multiple Tables Using UNION

![B1](images/6.png)

### The Solution: 

``` SQL
-- SQL request(s)​​​​​​‌​‌​​‌‌​​​‌‌‌‌​​​​​​‌​‌‌‌ below
With all_subscriptions as(

--UNION subscriptions tables here
select * from subscriptionsproduct1
UNION
select * from subscriptionsproduct2

)
select
	date_trunc('year', expirationdate) as exp_year, 
	count(*) as subscriptions
from 
	all_subscriptions
where active=1
group by 
	date_trunc('year', expirationdate)
```

### Solution Screenshot:

![B1](images/S_6.png)
