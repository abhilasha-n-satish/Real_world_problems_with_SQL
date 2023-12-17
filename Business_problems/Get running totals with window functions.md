## Tracking Running Totals with Window Functions

![B1](images/10.png)

### The Solution: 

``` SQL
-- SQL request(s)​​​​​​‌​‌​​‌‌​​​‌‌‌‌​​​​​​‌​‌‌‌ below
select 
salesemployeeid,
saledate,
saleamount,
sum(SALEAMOUNT) over (partition by salesemployeeid order by saledate) as Running_total,
 cast(sum(SALEAMOUNT) over (partition by salesemployeeid order by saledate) as float) / quota as percent_quota
from
Sales as s
join
Employees as e
on 
s.SALESEMPLOYEEID = e.EMPLOYEEID
order by salesemployeeid, saledate
```

### Solution Screenshot:

![B1](images/S_10.png)
