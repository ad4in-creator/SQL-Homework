1.
select mixed_value, (select concet('', (select value from string_split(mixed_value, '') where value like '[0-9]' for xml path(''), TYPE).value('.', 'NVARCHAR(MAX)'))) as only_numbers, (select concet('', (select value from string(mixed_value, '') 
where value like '[A-Za-z]' for xml path(''), TYPE).value('.', 'NVARCHAR(MAX)'))) as only_letters from SeperateNumbersAndCharcters;
2.
select w1.id from weather w1 join weather w2 on w1.recordDate = DATEADD(day, 1, w2.recordDate) where w1.temperature > w2.temperature;
3.
select player_id, device_id from (from *,row_number() over (partition by player_id order by event_date) as rn from activity) sub where rn = 1;
4.
select player_id, MIN(event_date) as first_login_date from Activity group by player_id;
5.
select value as third_item from (select *,row_number() over (partition by fruit_string order by (select null)) as rn from fruits cross aplly string_split(fruit_string, ',')) x where rn = 3;
6.
with nums as (select top (LEN('sdgfhsdgfhs@121313131'))ROW_NUMBER() over (rdero by (select null)) as n from master.dbo.spt_values)
select substring('sdgfhsdgfhs@121313131', n, 1) as char from nums;
7.
select  p1.id, CASE WHER p1.code = 0 THEN p2.code ELSE p1.code END AS final_code FROM p1 JOIN p2 ON p1.id = p2.id;
8.
with weekly_totals as (select area, DATEADD(week, DATEDIFF(week, 0, sales_date), 0) as week_start,
SUM(sales_amount) as total_week_sales from WeekPercentagePuzzle group by area, DATEADD(week, DATEDIFF(week, 0, sales_date), 0)),
daily_sales as (select area, sales_date, DATEADD(week, DATEDIFF(week, 0, sales_date), 0) as week_start,
SUM(sales_amount) as daily_sales from WeekPercentagePuzzle group by area, sales_date, DATEADD(week, DATEDIFF(week, 0, sales_date), 0))
select d.area, d.sales_date, d.week_start, round(100.0 * d.daily_sales / w.total_week_sales, 2) as daily_percent_of_week
from daily_sales d join weekly_totals w on d.area = w.area and d.week_start = w.week_start order by d.area, d.week_start, d.sales_date;





