1. Select ProductName Name from Products;
2. select * from Customers Client;
3. select ProductName from Products
  union
  select ProductName from Products_Discounted;
4. select * from Products
  intersect
  select * from Products_Discounted;
5. select distinct FirstName, Country from Customers;
6. select *,
  Case when Price > 1000 then 'High'
  else 'Low' 
  end as PriceType
  from Products;
7. select *, IIF (StockQuantity > 100,'Yes','No') as Stock_Availability  from Products_Discounted
8. select ProductName from Products 
Union 
select ProductName from OutOfStock
9. select * from Products
EXCEPT
select * from Products_Discounted 
10. select *, IIF (Price>1000,'Expensive','Affordable') as 'PriceType' from Products
11. select * from employees
where age < 25 or Salary > 60000
12. update employees
set Salary = Salary*1.1
where departmentname = 'HR' or EmployeeID = 5
13. select * from Products
INTERSECT
select * from Products_Discounted 
14. select *,
case when SaleAmount > 500 then 'Top Tier' 
	when SaleAmount > 200 and SaleAmount <= 500 then 'Mid Tier' 
	else 'Low Tier'
	end
from sales
15. select CustomerID from Orders
EXCEPT
select CustomerID from Invoices
16. select customerid, quantity, case when Quantity =1 then '3%' when Quantity >1 and Quantity <=3 then '5%' else '7%' end as Discount from Orders
