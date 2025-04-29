 1. This script uses recursion to calculate factorials.
def factorial(n):if n == 0 or n == 1:return 1 else:return n * factorial(n - 1)
print(factorial(5))

2.This script uses recursion to calculate Fibonacci numbers.
def fibonacci(n):if n == 0:return 0 elif n == 1:return 1 else:return fibonacci(n - 1) + fibonacci(n - 2)

print(fibonacci(6))
3.This script uses recursion to split a string into rows of substrings for each character in the string. (Example)
def split_string(s, index=0):if index == len(s):return print(s[index]) split_string(s, index + 1)
split_string("hello")

4.Create a CTE to rank employees based on their total sales. (Employees, Sales)
with TotalSales AS (select e.employee_id, e.name, SUM(s.amount) AS total_sales from Employees e join 
Sales s on e.employee_id = s.employee_id group by e.employee_id, e.name),
RankedEmployees as (select *, rank() over (order by total_sales desc) as sales_rank from TotalSales)
select * from RankedEmployees;

5.Write a query using a derived table to find the top 5 employees by the number of orders made.(Employees, Sales)
select e.employee_id, e.name, s.order_count from Employees e join (select employee_id, COUNT(*) as order_count
from Sales group by employee_id) s on e.employee_id = s.employee_id
order by s.order_count desc limit 5;

6.Use a CTE to calculate the sales difference between the current month and the previous month.(Sales)
with MonthlySales as (select date_trunc('month', sale_date) as sale_month,
SUM(amount) as total_sales from Sales group by date_trunc('month', sale_date)),
SalesDiff as (select sale_month, total_sales, lag(total_sales) over (order by sale_month) as previous_month_sales,
total_sales - lag(total_sales) over (order by sale_month) as sales_difference
from MonthlySales)
select * from SalesDiff;

7.Write a query using a derived table to find the sales per product category.(Sales, Products)
select p.category, SUM(s.amount) as total_sales
from Products p join (select product_id, amount from Sales) s on p.product_id = s.product_id
group by p.category
order by total_sales desc;

8.Use a CTE to rank products based on total sales in the last year.(Sales, Products)
with SalesLastYear as (select s.product_id, SUM(s.amount) as total_sales from Sales s
where s.sale_date >= current_date - interwal '1 year'  -- Filtering sales from the last year
group by s.product_id), RankedProducts as (select p.product_id, p.name, sl.total_sales, rank() over (order by sl.total_sales desc) as sales_rank
from Products p join SalesLastYear sl on p.product_id = sl.product_id)
select * from RankedProducts;

9.Create a derived table to find employees with sales over $5000 in each quarter.(Sales, Employees)
select e.employee_id, e.name, s.sale_quarter, s.total_sales from Employees e
join (select employee_id, extract(year from sale_date) as sale_year,
extract(quarter from sale_date) as sale_quarter,
SUM(amount) as total_sales from Sales group by employee_id, extract(year from sale_date),
extract(quarter from sale_date) having 
SUM(amount) > 5000) s on e.employee_id = s.employee_id
order by e.employee_id, s.sale_year, s.sale_quarter;

10.Use a derived table to find the top 3 employees by total sales amount in the last month.(Sales, Employees)
select e.employee_id, e.name, s.total_sales from Employees e join ) select employee_id, SUM(amount) as total_sales
from Sales where sale_date >= date_trunc('month', CURRENT_DATE) - INTERVAL '1 month'  -- Last month and sale_date < date_trunc('month', current_date)  -- End of last month
order by s.total_sales desc;
