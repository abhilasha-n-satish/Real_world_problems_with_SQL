## Creating Binary Columns with CASE

![B1](images/4.png)

### The Solution: 

``` SQL
-- SQL request(s)​​​​​​‌​‌​​‌‌​​​‌‌‌‌​​​​​​‌​‌‌‌ below
select 
customerid,
count(productid) as num_products,
sum(numberofusers) as total_users,
case when sum(numberofusers) > 5000 OR count(productid) = 1 then 1
else 0
end as upsell_opportunity
from subscriptions
group by customerid
```

### Solution Screenshot:

![B1](images/S_4.png)
