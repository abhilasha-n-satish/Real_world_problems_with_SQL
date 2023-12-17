## Using Self joins to compare rows within the same table



### The Solution: 

``` SQL
-- SQL request(s)​​​​​​‌​‌​​‌‌​​​‌‌‌‌​​​​​​‌​‌‌‌ below
with monthly_revs as (
select 
    date_trunc('month', orderdate) as order_month, 
    sum(revenue) as monthly_revenue
from 
    subscriptions
group by 
    date_trunc('month', orderdate)
)

select
current.order_month as Current_month,
previous.order_month as Previous_month,
current.monthly_revenue as Current_Revenue,
previous.monthly_revenue as Previous_Revenue
from
monthly_revs as current
join
monthly_revs as previous
where
datediff('month', previous.order_month, current.order_month) = 1
and 
current.monthly_revenue > previous.monthly_revenue
```

### Solution Screenshot:
