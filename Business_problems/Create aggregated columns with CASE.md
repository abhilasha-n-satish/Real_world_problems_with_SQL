## Pivoting rows into aggregated columns with CASE



### The Solution: 

``` SQL
-- SQL request(s)​​​​​​‌​‌​​‌‌​​​‌‌‌‌​​​​​​‌​‌‌‌ below
select 
userid,
sum(case when fl.EVENTID = 1 then 1 else 0 end) AS ViewedHelpCenterPage,
sum(case when fl.EVENTID = 2 then 1 else 0 end) AS ClickedFAQs,
sum(case when fl.EVENTID = 3 then 1 else 0 end) AS ClickedContactSupport,
sum(case when fl.EVENTID = 4 then 1 else 0 end) AS SubmittedTicket
from frontendeventlog as fl
join frontendeventdefinitions as fd
on fl.EVENTID = fd.EVENTID
where eventtype = 'Customer Support'
group by userid
```

### Solution Screenshot:
